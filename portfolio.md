---
title: Portfolio
permalink: /portfolio/
layout: page
excerpt:
comments: false
---
## Portfolio

### MSET

![MSET](./assets/img/mset.png)

#### Overview

Medical treatments intended to address any variety of conditions all have something in common: there are always side effects to consider.

As a patient taking medication or exploring treatment options, it’s important to monitor the way a treatment is impacting you. However, with so many other things on our minds on a day to day basis, it can be challenging to be mindful of how medication is actually impacting you, resulting in missed patterns that are important for you and your medical provider to be aware of.

MSET (Medication Side Effects Tracker) allows you, as a medication user, to track side effects for a variety of medications and supplements in order to cultivate a mindful practice of tracking how a medical treatment is impacting you, in turn allowing you to provide your doctor with holistic feedback to guide your treatment plan.

The current iteration of MSET supplies an interface to track symptoms and side effects over time and allows you to take control of your medical treatment.

The idea for this app was pitched and exectued with a team of 4 over the course of 10 days.

Our team was invited to present MSET at Turing Demo Comp on October 6, 2020 (video of presentation [here](https://www.youtube.com/watch?v=JzkCOFQSIFQ).)

#### My Areas of Focus


- I created the CRUD functionality for medications and create the user's medication list, as well as the show page for each medication.
- I enhanced the user experience for logging a symptom via a more intuitive symptom search function, which utilizes a fuzzy string match Ruby library that uses the Jaro–Winkler distance to measure the edit distance between the search keyword and every symptom in the database.
- I designed the medication search function and how medication information should be retrieved from the API called. In particular, I parsed HTML using the Nokogiri gem to retrieve and organize potential medication side effects, which were otherwise not accessible without a thorough and complex parsing.
