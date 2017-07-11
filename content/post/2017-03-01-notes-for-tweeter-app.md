---
title: Notes for Tweeter App
date: 2017-03-01T02:39:00-08:00
---

[App deployed to Heroku](http://app.fewblocks.ca/)

**Code review by Karl**

- Adding the user support so that my tweets aren't attributed to a random user was great.
- Clean and consistent code style.

Here are a few of things that I noticed could be improved. Some of these are so minor and I only mentioned them to bring them to your attention.

- Tweet counter starts as `NaN`. Seemed to reproduce it if I logged out and refreshed my browser.
- When I logout with the tweet textarea visible it stays visible.
- Seeing weird behaviour with different length tweets. If I 'Tweet' something short like 'Test' the tweet box is quite small width wise. If I put something like 'aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa' then the box is quite long. I understand that without the text breaking then it will just go out of bounds, but I would at least handle the minimum width case. In this case we get weird results allowing the content to dictate the design.
- If you click login, then register it brings up the register box like expected. If you hit login again, it just brings the login box over top.
- I'm able to post tweets that are more than 140 characters. You should look in to adding some service side validation in addition to the existing client side validation.
- The tweet box and counter don't reset when you submit a tweet.
- Missing the white background for the list of tweets. I know you are strong in the UI area so I'm not concerned about your ability to write the css to achieve this. We also talked in the past about you wanting to make this tweeter app have a material look.
- Nice clean index.js Great work!
- In saveTweet you use the callback immediately after you insert. You could consider having the callback executed when the insert is complete. insertOne should allow for this.
- I've included some other opportunities for refactoring in the eval/jensen branch.
