---
title: Parsing with Nokogiri
date: 2020-10-19
tags: [blog, ruby, rails, nokogiri, html]

---

<hr>

#### Parsing with Nokogiri

I'm currently working on building an application that will enable a user to track any medications that they take along with any adverse symptoms that they experience, and quickly check if said symptom is a known side effect of the medication.

Our application consumes external API endpoints with relevant drug information.  While consuming APIs is not new to me, having to parse through HTML to retrieve necessary information isn't something that I have had to do before.  This project ended up offering a perfect opportunity to practive such a skill.

### The Problem

We've designed our application so that, when a user searches for a medication by either the brand name or the generic name, an HTTP request is made to an endpoint that sends a response containing the product's NDC ([National Drug Code](https://www.drugs.com/ndc.html)).  The FDA has a number of [free-to-use drug-related API endpoints](https://open.fda.gov/apis/drug/), including one that contains basic information about a given drug by generic or grand name, so this endpoint works for when a user searches for a drug by name in the app.  In order to retrieve the side effect information, my team and I went looking for an additional API that allows us to search for known side effects by a product NDC. We found one on [DrugBank](https://www.drugbank.ca/) that fit our needs perfectly, but it required a paid subscription.  If we have a budget to pay for our API then this would definitely be our go-to.  Thankfully, the FDA also has an adverse reactions endpoint.  Bingo!  The only problem is that the data is contained within a table and looks, to me at least, like an HTML minefield:

![Screen Shot 2020-09-12 at 11.40.04 AM](/Users/jejdelman/Library/Application Support/typora-user-images/Screen Shot 2020-09-12 at 11.40.04 AM.png)



This is where Nokogiri comes in.

### What is Nokogiri?

According to the [Nokogiri website](https://nokogiri.org/), *"Nokogiri (鋸) is an HTML, XML, SAX, and Reader parser. Among Nokogiri's many features is the ability to search documents via XPath or CSS3 selectors."*

The first step was to make the API call and then parse the response with JSON and assign the  `adverse_reactions_table` to a variable:

```ruby
require 'nokogiri'
require 'open-uri'
require 'json'
require 'faraday'

conn = Faraday.new('https://api.fda.gov')
response = conn.get('/drug/label.json?search=adverse_reactions:adderall&limit=1')
json = JSON.parse(response.body, symbolize_names: true)
tables = json[:results][:adverse_reactions_table]
```



Now the we have the tables, it's time to use Nokogiri.  We called the variable `tables` because the `adverse_reactions_table` contains a few tables of data, so we need to iterate through them all to save the symptoms.  We can parse the HTML with nokogiri using the `Nokogiri::HTML` method:

```ruby
tables.each do |table|
	page = Nokogiri::HTML(table)
end
```



Most of the required information could be retrieved using the following code:

```ruby
tables.each do |table|
  page = Nokogiri::HTML(table)
  rows = page.css('tr')
  rows.each do |row|
    if row.css('td:nth-child(2)').children.length > 0
      str = row.css('td:nth-child(2)').children[0].text.to_s.strip
      symptoms << str if str
    end
  end
end
```



Unfortunately, I ended up needing to use regex to sift through some of the text that we ended up with, but hey, we managed!  This was a fantastic learning experience and I'm proud of the project that we created.

If you're interested in using Nokogiri for parsing, here are some resources that I found helpful:

- [Parsing an HTML / XML Document](https://nokogiri.org/tutorials/parsing_an_html_xml_document.html)

- [ReadySteadyCode: How to extract data from HTML with Ruby](https://readysteadycode.com/howto-extract-data-from-html-with-ruby)
