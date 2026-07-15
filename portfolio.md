---
title: Portfolio
permalink: /portfolio/
layout: page
excerpt:
comments: false
---

## Selected Work

Most of my production engineering work was completed in private repositories. These case studies describe the systems I helped build, the problems I worked on, and the technical decisions involved.

*Code is proprietary and the descriptions have been generalized.*

### Expanding Cyber-Risk Scan Coverage

Corvus’s cyber-insurance platform evaluated organizations’ publicly accessible infrastructure to identify vulnerabilities and inform underwriting and policyholder recommendations. One gap in the scanning process involved infrastructure discovered through MX DNS records, which identify the mail servers associated with a domain.

I worked across the platform’s Elixir services, PostgreSQL database, GraphQL APIs, and legacy Python integrations to incorporate MX-discovered assets into the scanning workflow.

#### My contributions

- Added scanning support for IP addresses discovered through MX records.
- Verified MX coverage across a legacy Python vendor integration.
- Updated application queries and asset views to recognize and display the new asset origin.
- Extended automated underwriting checks to account for vulnerabilities found on email infrastructure.
- Built normalization and filtering logic for common hosted-email providers, accounting for inconsistent capitalization, formatting, and trailing characters.
- Added tests based on representative production scenarios to reduce the risk of false-positive underwriting decisions.

##### Outcome

The project expanded visibility into email-related infrastructure and gave underwriting and policyholder-facing systems a more complete picture of an organization’s external risk exposure.

**Technologies:** Elixir, PostgreSQL, GraphQL, Oban, Python, AWS

### Building a Policyholder Security Survey

External infrastructure scans provide valuable information, but they cannot reveal internal security practices such as multifactor authentication, employee training, or incident-response preparation. Corvus wanted to collect this information while also giving policyholders another meaningful reason to engage with its application.

I helped design and build a configurable survey system within the policyholder platform using Elixir, Elm, GraphQL, and PostgreSQL.

#### My contributions

- Designed the relational data model for survey types, sections, subsections, questions, answer options, and responses.
- Created and migrated the new database tables and populated them with the initial survey content.
- Built the GraphQL components needed to move survey data between the backend and Elm frontend.
- Developed an interactive progress tracker in which each question was represented by a navigable status indicator.
- Created clear answered and unanswered states so policyholders could understand their progress and return directly to incomplete questions.

##### Outcome

The survey gave Corvus a structured way to incorporate internal security practices into its risk picture while creating a more engaging policyholder experience. It shipped as part of a broader set of product improvements after which active policyholder engagement increased by 50%.

**Technologies:** Elixir, Elm, GraphQL, PostgreSQL

## Earlier Work

* [MSET](#mset)
* [Sweather Weather](#sweater-weather)
* [Viewing Party](#viewing-party)

#### MSET<a name="mset"></a>
[Repo](https://github.com/gabichuelas/mset_app) | [Application](http://mset-app.herokuapp.com/)

![MSET](./assets/img/mset.png)

##### Overview

Medical treatments intended to address any variety of conditions all have something in common: there are always side effects to consider.

As a patient taking medication or exploring treatment options, it’s important to monitor the way a treatment is impacting you. However, with so many other things on our minds on a day to day basis, it can be challenging to be mindful of how medication is actually impacting you, resulting in missed patterns that are important for you and your medical provider to be aware of.

MSET (Medication Side Effects Tracker) allows you, as a medication user, to track side effects for a variety of medications and supplements in order to cultivate a mindful practice of tracking how a medical treatment is impacting you, in turn allowing you to provide your doctor with holistic feedback to guide your treatment plan.

The current iteration of MSET supplies an interface to track symptoms and side effects over time and allows you to take control of your medical treatment.

The idea for this app was pitched and exectued with a team of 4 over the course of 10 days.

Our team was invited to present MSET at Turing Demo Comp on October 6, 2020 (video of presentation [here](https://www.youtube.com/watch?v=JzkCOFQSIFQ).)

##### My Areas of Focus


- I created the CRUD functionality for medications and create the user's medication list, as well as the show page for each medication.
- I enhanced the user experience for logging a symptom via a more intuitive symptom search function, which utilizes a fuzzy string match Ruby library that uses the Jaro–Winkler distance to measure the edit distance between the search keyword and every symptom in the database.
- I designed the medication search function and how medication information should be retrieved from the API called. In particular, I parsed HTML using the Nokogiri gem to retrieve and organize potential medication side effects, which were otherwise not accessible without a thorough and complex parsing.

---

#### Sweater Weather<a name="sweater-weather"></a>
[Repo](https://github.com/ejdelsztejn/sweater_weather)

![Sweater Weather](./assets/img/sweater_weather.png)


##### Overview

Sweater Weather is a Ruby on Rails back-end REST API for a fictional road trip planning application. The app allows users to see the current weather at their destination, future forecasted weather at their destination, and additional information such as total navigation time, mileage, and an image of their destination.

##### My Areas of Focus


- I exposed an API that aggregates data from multiple external APIs and requires an authentication token.
- I ensured that the structure of all responses are JSON API 1.0 Compliant.
- I tested API calls using WebMock and VCR.
- I adhered to MVC design principals by organizing logic into intentional facade, PORO, model, serializer, and service files.

---

#### Viewing Party<a name="viewing-party"></a>
[Repo](https://github.com/ejdelsztejn/viewing_party) | [Application](http://viewing-party-paired-project.herokuapp.com/)

![Viewing Party](./assets/img/viewing_party.jpeg)

##### Overview

Viewing Party is an application to explore movies and create a viewing party event for you and your friends to watch a movie together. Users log into the application using Google OAuth and can explore the movie database thanks to the consumption of the MovieDB API.  Users can view information about movies, add friends to their account, and plan viewing parties with their friends that will be added as events to their Google Calendars.

##### My Areas of Focus

- I implemented basic user authentication using Google OAuth and utilized the Google Calendar AP to integrate the app with Google Calendar and enable users to add viewing parties to their calendars.
- I applied RuboCop’s style guide for code quality.
- I utilized Continuous Integration using Travis CI.
