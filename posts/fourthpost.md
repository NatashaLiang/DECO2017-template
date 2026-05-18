
---
title: Second Post!!
date: 2026-04-25
author: Natasha
summary: Figuring out MVPs and wireframing
tags:
  - tag1
  - tag2
  - tag3
---

 Pushing my map feature and extending existing code. Integrating, pushing our features together. 
# 4th Reflection: 

This week we were starting to come together, merging our individual work features to a working website/prototype. Whilst I was building court maps independently, we found that our final features still needed working on despite the functionality meeting the MVP. We found that the overall website still needed UI changes to be made such as finalising our font and restyling the template pages to fit the community branding. With our merges made, we had a few functionality errors that we had to re-cover and ticket.


We started uncovering how to integrate the other features (forum) and (event) to the main homepage, for users to have a clear understanding of the community hub and its features for users to interact with. Whilst these were not features that I had to code, it was important for us as a group to discuss and re-align to ensure the home website would reflect the same features that were already built.


I also (rookie mistake) didn’t double check the website URL for each booking site, where some websites for courts were linked correctly. Since the LLM created the CSV, the website URLs created were invalid. Due to the nature of CSV seeding the database I needed to correct these stored values. I thought of a few solutions, at first I thought I could re-import the CSV with the updated links without needing to create an update script, allowing me to mass edit them quickly. But the database was already live within the prototype, so to edit the csv, I added a **db.exec('DELETE')** command to temporarily wipe and edit the CSV data directly. This was a clean way to reseed faster offering efficiency over **SQL updating** each row. Whilst updating each court would ensure no data loss, this fix was efficient as we were still in the prototyping stage rather than a proper production that favoured clean data changes.


<img width="806" height="519" alt="Screenshot 2026-05-18 at 10 36 46 pm" src="https://github.com/user-attachments/assets/4c216fa3-fb2b-4166-87e5-15c093b02c0c" />


### Profile page - navigating teammates code
After covering the map interactions, I pushed towards creating a profile page for users to edit their account profile for others to view such as **bio, skill_level, postcode, favourite gear and social media links**  created with a users table, for users to input their data. I did this using an alter table, to create a column for the system but with a catch wrap to continue running if the command accidently runs twice. I was really happy with the turnout of the basic functionality of the profile. 

I decided to add random profile colours for each user that signs up within the profile function. But to make this more consistent, I had to trace how the forum was pulling user data, how templates were being rendered, and where user information was being passed through before I could confidently add anything without breaking anything. The forum was originally hardcoded with a single colour (created by another teammate), where I identified and replaced all the hash function, to match the profile feature I pushed out.  It may be a minor feature but makes the prototype feel more considered and designed with intention. The process of identifying and changing in the team’s code to implement smoothly was a really fun part of the project being able to extend existing code and collaborating in a team environment. 


### Last MVP decisions, (Security & ethical considerations):
We also made a final call on a feature we had debated from our initial development, whether to show other users' profiles to non-logged-in visitors. We were happy to confirm that we should restrict profile visibility to logged-in users only. Where users should be required to log-in before they have access to viewing other users. This aligns with our responsibility to handle user information appropriately. Though skill level and attendance count does seem like low-risk data, users should reasonably expect that information is only shared within the community for safety. 

We looked back at our MoSCow framework from early stages in our project which helped a lot in understanding the scope of our project in aligning with our community members when we first identified their needs. 

Must Have:
- One tap RSVP system to reduce organisational friction
- Skill level filtering and display to minimise mismatched games
- Forum for Q&A and discussion to support organic community building
- Location aware court map to reduce search friction
- User profiles showing activity history to provide credibility and context

Should Have
- Photo uploads for event recaps
- Notifications for RSVP updates or cancellations
- Search functionality within the forum
- Court review system

Won't Have
- Dedicated member browsing tab
- Leaderboards or rankings

We had all our must-haves stay the same, suggesting our early research on our user group (reducing intimiadation for people joining the community) was fairly accurate and designed with intention. But the products that were shaped the most were our 'court review system' in our "should haves", where we realised during the project scope this no longer aligned with our project. Whilst we first valued how important it intially could've been, mapping the data made us realise the complexity wasn't worth it especially if we already had an existing forum page with a similar function. Whilst the remaining should haves are unbuilt - the MVP of our prototype works well in the core user flow. 

This helped us realise our assumptions weren't wrong, but rather the process revealed the importance of being specific and analyse trade-offs to get the best prototype possible when working with so many data layers. 

