---
title: Reviewing Merge App
date: 2017-03-07T02:17:00-08:00
---

<a href="/uploads/mockups.jpg"><img src="/uploads/mockups.jpg" width="600px"></a>
**Mock-up designs for Merge App:**

**Code review conducted by Vaz**

"Merge" decision-making app by Adrian Diaz, Donald Geddes, and Richard Hsieh


- app's visual design is very clean. Stylized but still professional
- impressed with the mobile-first design and responsiveness
- liked the graceful degradation (after "fifth choice", "choice 6", etc...)
- app's basic functionality was all present and working
- glad to see it working on your phone (including getting the emails) during the demo


On planning, division of work and collaboration:

- You basically followed Don's sermon during the planning phase. Spending most of the first day on this (and project setup) is pretty reasonable.
- We talked about how you divided up the work. It's common to divide things up into "backend", "frontend", "db", etc. As you saw, sometimes this kind of categorization can lead to uneven workload or uneven investment in critical/bottleneck areas of the app. Though, it's not always easy to see how things should be divided up at the beginning, and something like frontend/backend can be something to go on.
- git strategies (small and focused commits and topic branches, frequent merges - you can merge master into your branch as often as you want)
- using project tracking tools (I could recommend Github Issues and/or Trello for the final project)
- Clearly documenting (and possibly even versioning) your API's between frontend and backend (or any 2 components) and limiting the frequency at which they change (avoiding the case where they change often and without notice)
- Documenting sticky parts of the code where a non-obvious solution is being used or a lot of debugging time has been invested.
- pair programming on complicated issues, and making the time to do peer code reviews whenever work is being merged to master.

Code review notes:

- Server JS: - mostly looked great - SQL injection vulnerability! You pointed it out to me, you knew there was something wrong with it... knex has a string format for handling this in raw queries, look it up! - I liked that your db helpers returned promises instead of the callback style used in the skeleton code

- HTML/EJS: - email template looked good (proper email-friendly HTML) - main file was static HTML, client is a SPA - I want to say this is a bit "ambitious" with just jQuery

- Client JS: - Overall I think you did a great job with the frontend - Though, as you saw the frontend started to get more and more complex... it really is an "app" of its own and ends up needing to be structured like one - jQuery doesn't give you a lot in this regard (although it has plugins, or jquery-ui widgets, which can help) - really though, there's a reason I compared using just jQuery to build an SPA to using `http.createServer` instead of express to build a server. (Also, I know this was the stack we gave you!) - I think your experience doing the frontend "the hard way" will probably add to your appreciation of frontend frameworks like React :)


<a href="/uploads/mergeapp.png"><img src="/uploads/mergeapp.png" width="600px"></a>
**Screenshot of e-mail sent by Merge App**