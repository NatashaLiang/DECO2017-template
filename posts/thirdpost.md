---
title: Third Post
date: 2026-05-7
author: Natasham
summary: Developing map feature
tags:
  - tag1
  - tag2
  - tag3
---



After finalising our teams wireframes, we created tickets in distributing our project's features within our team meeting. I am leading charge for the ‘map’ feature in the community blog, where members can search up the best courts provided with amenities such as parking, public transport availability and gear hire. This will significantly help users to choose courts depending on their preference with price and a booking link for each court. I was able to research further into what requirements I needed and created the tickets in our team kanban board. Using a kanban board will help members progress on our tasks for others to understand what we are up to, and create the check in process easier. 



# Creating data:
This week I was able to work and complete the data sheet for court information,(with some help of an LLM) to fill out information required. Whilst initially I thought of researching courts to fill out the data sheet, I found that using an LLM would be efficient in grabbing the court's information (especially 10+). This would allow me to develop the structure of the SQL schema code more effectively in the timeline. Having a diverse amount of courts is beneficial to bringing data diversity for functionality e.g searching post codes, suburbs and filtering tables for specific amenities to show functionality of how queries would be handled. 


Our group has been able to annotate our wireframes to understand our data and how the users interact with the website, whilst it was difficult at first to understand which interactions extract data, it helped define the scope of how each table can connect together to display information in the front end.  We transferred these annotations to a schema database in DBdatabase.io to help our team visualise the data. I find that this visualisation is easier to scan than an EDD, whilst useful to search to ensure our team is synced on using the same attributes. Interacting and discussing our tables made us realise we had a lot of overlapping information that provided a lot of fluff within our screens e.g reviews for map courts cluttered our prototype. We realised it wasn’t an essential functionality as our core MVP, especially with our current technical capacity. We found the trade-off to be worth it, where we wouldn’t lose existing community interactions as they would be handled within the forum feature for court discussion. This helped the scope of our project between “nice-to-have” and “must haves” from our initial project ideation. 


# Google maps api & feature development:
The most significant technical hurdle this week was integrating Google Maps API with our HTMX-driven interactions. The core requirement was a "no-refresh" experience when browsing court details. I encountered specific hurdles with API key security and template rendering. I had to pivot to using <%== when integrating my API key into the script URL, which would have broken the map entirely when restructuring the key to .env to keep secret from git. I found passing the key in the courtmap.ts script through a function first when initialising also fixed my hurdle problems. With all API keys managed via server-side environment variables (.env) to prevent unauthorised usage or data leaks. I utilised HTMX interactions for users to go through the list of courts on the map, where filters (user interaction) will respond and update the users needs instantly. This also is an important feature for accessibility needs, where the information of courts can still be displayed if the users’ device isn’t able to load the map properly. However I am yet to trial and error if the map should be updated dynamically too as I am worried adding the HTMX swap will make the map jumpy for each court update making the users experience a bit jarring or buggy. 


# Next ticket:
My next goal is to figure out filtering. I need to decide if the map should show every court at once, or if it should hide markers that don't match the user's search. Both have pros and cons, and I plan to test both versions to see which feels more natural for a badminton player looking for a quick game.


