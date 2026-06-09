
---
title: A3 Final reflection
date: 2026-06-09
author: Natasha
summary: A final reflection about RallyCLUB
tags:
  - tag1
  - tag2
  - tag3
---

# Reflecting upon our community, RallyClub 
When starting the project; RallyClub, we had a vision in creating a community that was not only welcoming and allowed others to connect. But a new way to find social games for badminton members in Sydney, making it easier to find others and rally no matter the skill level without the anxiety of contacting strangers or event organisers. Now the product MVP has been developed, looking back on what we delivered is a small part of how we can further improve moving forward in developing RallyClub further by considering what worked, what didn’t and what I’d do differently next time.

---

##  Performance

Lighthouse testing was performed on all main pages before delivering our product but due to time constraints fixing accessibility issues didn’t get adjusted. 


> **Evidence: Lighthouse audit scores across key pages**

> | Page | Score | Key Issues |
> |---|---|---|
> | Home | <img width="400" alt="Screenshot 2026-06-09 at 6 49 30 pm" src="https://github.com/user-attachments/assets/d24ca8a3-4ea3-462e-a1f5-d75563624da3" /> | -> Contrast Ratio for orange subheading, <img width="200" alt="Screenshot 2026-06-09 at 7 01 20 pm" src="https://github.com/user-attachments/assets/80f9e1f5-4291-4ab4-b178-cc9acf36499f" /> **Fix required to pass WCAG AA**: Either darker orange hue or larger text font |
> | Forum | <img width="400" alt="Screenshot 2026-06-09 at 6 50 29 pm" src="https://github.com/user-attachments/assets/1a25f065-93c4-4583-8960-f6b4b21b7ccf" /> | Contrast ratio fails at topic tags. Fix required: Either change to a darker hue or change font colour to black|
> | Events | <img width="400" alt="Screenshot 2026-06-09 at 6 50 29 pm" src="https://github.com/user-attachments/assets/1a25f065-93c4-4583-8960-f6b4b21b7ccf" />  | Performance affected due to the weight of the pages scripts, images and fonts. Css could be optimised for scripts that aren't being applied on the page. Skill level badges, again, need better contrast ratio|
> | Profile | <img width="400" alt="Screenshot 2026-06-09 at 6 51 38 pm" src="https://github.com/user-attachments/assets/487e0f74-8433-4772-9002-4b4867a87a78" /> | Score of best practices could be improved by reducing unused JS and CSS Improved semantics for skill level dropdown could also be adjusted for better accessibility|

The home page receiving the strongest score was a direct reflection in our last minute pivot, where we were flagged by expert feedback, mentioned by our tutor that the design felt generic. The design system was weak and had no strong connotation to the badminton community. With this, we redesigned it in Figma before submission. 


We added:
- more colour
- bolder fonts
- stronger hierarchy with grid layouts + imagery
- styling animation of hover lifts on clickable elements

We re-designed features to be user friendly on the home page,  instead of recycling elements already coded within the project. With user feedback **p2** mentioned the homepage being **"professional, simple, and approachable"** during a think-aloud session, which confirmed the revamp had landed the way we intended. 

> | Page | Screenshot |
> |---|---|
> | Old Home page|  <img width="400"  alt="Screenshot 2026-06-09 at 6 53 44 pm" src="https://github.com/user-attachments/assets/81f707ff-af3e-4f8d-b9b8-06f8e6f4e08e" /> |
> | New home page | <img width="400" alt="Screenshot 2026-06-09 at 6 54 58 pm" src="https://github.com/user-attachments/assets/d4da5973-8587-4508-919f-e04ec8c032ed" />  |

However, this redesign came at a cost in lighthouse findings. Since the changes were drastic and made last minute - affecting home page, colour tags and hover animations to apply site side. It leaned towards using LLM-generated code to ship these changes quickly. This trade-off created bloat, with 29KiB from unused CSS & 74KiB in JS, the total payoff came to 2,816. Whilst some could've also been affected by the google maps API, leaning on LLM genderated code can lead to redudant code that doesn't get eliminated properly. The result is code bloat that earlier iteration would have avoided, and that a production build pipeline with minification would address.

Other accessibility culprits were found in contrast issues with tags (skills & forum topics) with proper WCAG contrasting tools, this could’ve been prevented before shipping and found as an issue with last minute lighthousing. 

The map I worked on had an interaction gap that I was submissively aware of during submission but due to prioritisation did not get handled on time. With the HTMX filtering, the courts updated on the side panels but the map pins don't reload to the changes. Every marker still remains visible despite the filter function. Not correcting the map breaks the spatial logic of this feature, where the fix would've required a filter state back to the API and re-rendering the markers. In hindsight was the wrong prioritisation and filtering required to be functional for every aspect, to meet the real world users expectations.

# User Experience and Accessibility

> _“This would be cool if expanded to other sports as well to help find social events”_

The think aloud sessions were conducted with two participants that gave us a clear idea if our product worked as intended. The results helped highlight our strengths, and re-evaluate interactions that need more attention towards. Both users completed four tasks, where they were asked to ‘think-aloud’ to understand our users' intentions and thoughts. Both participants found strengths in identifying skill-level badges when selecting the correct event, confirming that the skill badges were organised and working correctly as intended. P2 commented the forum being similar to Reddit or Facebook but better, for sport related questions which felt like an excellent validation community aspect for our concept. 

Both users struggled in finding attendee profiles, as the task was structured to view the profiles after they were tasked to RSVP to an event. There was a buffer or confusion if they had to re-find the event or if there was another way to view community members. There was an expectation by P2, “I should be able to see events that I already RSVPed to in my profile”. 

P1 also expected the full event card to be clickable, not just the title, creating visible hesitation before completing the task. P2 flagged the logo not being interactive, breaking a fairly standard navigation expectation, and noted that the logout in the navigation bar was unusual. _**“Logout should be a dropdown from profile so people don’t accidentally click it”.**_

Accessibility is the biggest issue in the backend that I would like to be most critical in, especially that profiles scored the lowest, which was rooted to the dropdown contrast and the skill labels not meeting AA WCAG ratios. These colours chosen were created to match the style guide without being out of place, but should've been checked through the contrast checker in Figma before developing. We relied on Lighthouse audits as our primary accessibility check, which flagged the problems after the styles were already embedded across the code. But, this should be checked during the design phase, where running these when developing the style guide stage would’ve prevented the gaps we already had delivered. 


# Critical reflection and improvements

The map filter and profile accessibility features share the same underlying causes: underscoring the prioritisation of decisions. Where tasks seemed manageable in the scope but weren’t tested properly or evaluated close enough until the last minute, undermining user’s experiences. 

The map pin filtering came under time pressure where HTMX updates felt like a polished item that wasn’t necessary at the time. But in fact this was something I should have communicated to my team members, discussing what was necessary under the time crunch. This feature is a core part of the page’s logic, filters that don’t match the map creates a spatial mismatch. With clearer task understanding, earlier in the sprints could’ve had a better distinction for “must have” and “nice to have” when evaluating before it became too late to address. 

The RSVP events not being reflected on the profile page hit a technical wall where we failed to integrate this properly within the MVP. As this feature is one of the main core features for the community, the entire platform's premise is not working properly as users expect. A user who’d want to cancel a session should be able to see this on their profile, ultimately leading to another feature that an early sprint session could’ve prevented when developing RallyClub. 


The home page redesign reinforced a lesson about iteration timing. Leaning on LLM assistance to push through major styling changes under deadline pressure allowed us to ship something that tested well, but produced unused CSS and JavaScript that hurt performance scores. The issue isn't using LLM-generated code, but implementing chunks of code without leaning it out, and without time to audit the output. Running those iterations earlier would have left room to trim code, rather than shipping code bloat under deadline pressure.


# Retrospective on functional requirements 


Looking back on our initial plans for RallyClub, the outcomes were more constrained than we anticipated. We had initially ideated on more features but had to cut a lot to ensure the core features could be delivered functionally within the scope. 

Dropping court reviews in the court map, in favour of keeping the conversation in the forum worked well. Users found the map to have an overall clean and straightforward function and could’ve potentially been scope creep for the feature. But the location-based radius filtering that P2 reached for unprompted **"maybe a 5km or 20km thing"** was something we could’ve considered during development and filed as a nice-to-have. Watching the user instinctively prompt for it during testing changed my read on that decision. Finding a game near you is a natural need for users who are using this feature for selecting a court.

The forum worked and exceeded expectations. Where both participants engaged with the forum positively and found the structure to be intuitive and felt more connected in the community. This concept was validated well, in favour of the new homepage that we pivoted last minute which had an excellent value to our prototype. 

The RSVP system's core flow worked, where both users completed it with little to no hesitation. But the seeded attendee counts and the unresolved cancel-on-profile limitation leave a gap in the original promise. The premise was that transparency about who's attending would reduce the anxiety of showing up to a session of strangers. Simulated counts and a profile sync issue can arise trust issues more than we'd planned. This demonstrated to me that the concept has potential, but it isn't ready to rely on in the real world yet for hosting sessions. 

# Lessons learned


With reflecting upon the last 7 weeks, it was clear that assumptions about the scope need to be tested against actual usual behaviour earlier on within the project, not just hypothetical logic or assumptions. I went into the map assuming that it met MVP, but user testing shows me that it didn’t meet the users expectations. 

On the technical side: building these features pushed me to learn a lot about designing with SQL schema, API key security whilst balancing environment variables. Using tools such as lighthouse to provide qualitative metrics supporting our testing sessions, showed gaps in our technical side. The numbers reinforced our gaps, where code bloat from last minute AI- assisted iterations made clear that understanding your build output matters as much as writing the code itself. Using these numbers also helped me understand the importance of evaluating accessibility early in the design phase, where simple contrast checking can save us time rather than forcefully submitting failed accessibility issues. 
