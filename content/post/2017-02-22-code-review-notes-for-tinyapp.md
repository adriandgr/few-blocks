---
title: TinyApp
description: Code review notes for my first bootcamp project.
date: 2017-02-22T16:22:00-08:00
tags: [
  "code review",
  "bootcamp"
  ]
---

<a href="/uploads/kortos.jpg"><img src="/uploads/kortos.jpg" width="600px"></a>

Code review for tinyApp assignment.

## Notes given by Dave during code review:
- use `temp/` directory to store local files instead of listing them individually in the `.gitignore` file
- ensure there is a new line character at the end of all code files
- `require('dotenv')` as early as possible
- move dev-dependencies to regular dependencies or guard them while in production mode
- [moment.js](https://momentjs.com/) as an alternative to dateformat
- look into app.listen and server.address api (for reporting the server address) domain configuration should be in `.env` file
- `app.set` is a server configuration (not a middleware) group them with other server configuration variables.
app.set is a configuration
- Good job on using `req.session.nowInMinutes`. Now go and research about why it's useful (session fixation attacks).
- emails **may not** be validated with regular expressions.

  - google: falsehoods programmers believe...
  - curated lists of falsehoods
  - email specification doc: RFC 822
- `if users()`
- why return false when you meant undefined
- you may give functions properties (they are objects)
- don't forget to `do { } while` when applicable. DRY code!
- `res.locals` in `app.use` read more about them. DRY code!
- Reduce you [cyclomatic complexities](https://en.wikipedia.org/wiki/Cyclomatic_complexity)... use `return` statements as guards.
- Religiously end line with every `{` and start line with `}`
- Watch out for using root level routes such as `GET /:username`. What if somebody's username is `urls`? route conflict with `GET /urls`. **Lesson:** users are intentionally or accidentally malicious. Guard for every edge case.
- look into **static code analysis** [bitHound](https://www.bithound.io/) or [sonarqube](https://www.sonarqube.org/) (code quality tools)
- Use `if` statements to check for truthy values and not the reverse, which increases logic complexity
- if it doesn't exist `404`. Do not treat unauthenticated users differently
- Not so important, but eventually look into ntp drift for dealing with time discrepancies in the vagrant vm
- **critical feature missing!** `delete /urls/:id` should only delete url if user is owner.
- `401` on `POST /urls`
- keep guards at the top
- avoid `for... in` loops
- check valid scheme such as ftp
- avoid business logic on the view side. Server should handle this.