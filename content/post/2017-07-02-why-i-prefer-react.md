---
title: Why I prefer React
description: Compared to other frameworks, I find development in React more enjoyable for the time being.
date: 2017-07-02T18:47:00-04:00
tags: [
  "react",
  "angular",
  "frameworks",
  ]
---


> However **isolated scope** creates a new problem: if a **transcluded** DOM is a child of the widget isolated scope then it will not be able to **bind** to anything. Fot this reason the transcluded scope is a **child** of the **original scope**, before the widget created an isolated scope for its local variables. This makes the transcluded and widget isolated scope **siblings**
>
> Slide from [Rethinking Best Practices](https://www.slideshare.net/floydophone/react-preso-v2)


## Up and Running

During my web dev bootcamp, I heard lots of people tell me that learning web frameworks is much harder than learning a programming language. Once you know the basics of a particular language, you can pick up a new one in about a week, give or take... Your main emphasis is learning language specific syntax and implementations, allowing you to leverage most of the knowledge you've already accrued from previous languages. This notion was reinforced with resources such as [Learn X in Y](https://learnxinyminutes.com/), a site where you can easily digest the most common features of a variety of languages.

The same thing may not be said about frameworks. If picking up a new language usually takes a week, then getting comfortable with the basics of a framework may take up to a month or more (so I heard).

<strong>I couldn't really believe these statements...</strong>

![giphy-downsized.gif](/uploads/giphy-downsized.gif)

After all, a language should *in theory* be a much more complex beast than the framework itself. Right? As a growing developer, I've tried not to get too comfortable with the same tools I've already learned and set out to explore various frameworks and tools. By doing this, I've discovered how true these previous statements have been in my experience.

## Angular, An Actual Framework

One of the frameworks that I kept going back to and then getting turned off by was Angular. I spent a lot of time on their docs, reading through 'Up and Running' sections, only getting frustrated by the snail speeds of the experience. At the time I just wrote it off as lack of experience, which is to be expected, however, I also felt like there was more to it. I just didn't know what it was. My only reaction was to move on to something else and come back to it when I felt I had gained that elusive experience.

It was only when I stumbled upon the set of slides referenced above that I started to understand why I liked libraries like React or Vue.js much more. I enjoyed the composability of React components way more than the highly decoupled Angular directives with their separate templates and services. Sure, Angular is a much larger tool, after all, it prides itself on being a real framework covering all stages of the MVC model. However, I can't stop to think how this emphasis on decoupling concerns can hurt the development process.

I'm not closing myself off to Angular forever, I'm just happy I have a better understanding of the reasons why for now I much rather invest my time with React.

## Kindred Spirits

<blockquote class="twitter-tweet" data-conversation="none" data-lang="en"><p lang="en" dir="ltr">after <a href="https://twitter.com/reactjs">@reactjs</a> can&#39;t even look at template based frameworks. It solves everything. Fast, composable and easy to use.</p>&mdash; Tim Voronov (@ziflex) <a href="https://twitter.com/ziflex/status/820806834449711105">January 16, 2017</a></blockquote>
<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">This list of <a href="https://twitter.com/hashtag/reactjs?src=hash">#reactjs</a> patterns is helpful for structuring components in a clean and composable way from the start.<a href="https://t.co/6trWW1aFSt">https://t.co/6trWW1aFSt</a></p>&mdash; Marc Löhe (@bfncs) <a href="https://twitter.com/bfncs/status/770873280651730944">August 31, 2016</a></blockquote>
<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">&quot;The philosophy of small, composable, single-purpose tools never goes out of style.&quot; <a href="https://t.co/33JOo3SVlO">https://t.co/33JOo3SVlO</a> <a href="https://twitter.com/hashtag/reactjs?src=hash">#reactjs</a> <a href="https://twitter.com/hashtag/javascript?src=hash">#javascript</a></p>&mdash; Eric Nograles (@grales) <a href="https://twitter.com/grales/status/684743816839036928">January 6, 2016</a></blockquote>
<blockquote class="twitter-tweet" data-lang="en"><p lang="und" dir="ltr">❤️ composable UI components <a href="https://twitter.com/hashtag/reactjs?src=hash">#reactjs</a></p>&mdash; Dimitris Karagiannis (@MitchKarajohn) <a href="https://twitter.com/MitchKarajohn/status/868092720170115073">May 26, 2017</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>