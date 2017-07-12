---
title: "To watch or not to watch"
description: "A few questions about build tools and the purposes they ought to be fulfilling."
date: 2017-07-11T18:13:27-04:00
tags:
  - discussion
  - react
  - dev tools
---

There's been a question on my mind in regards to best practices for compiling files from `.scss` to `.css`, specifically for use in React projects.


## The simple world of DIY webpack.config.js

The method which I was first familiar with, and which is probably the most common one is through the use of webpack module loaders:

```javascript
module: {
    rules: [
      { test: /\.(scss)$/, use: [
        'style-loader',
        'css-loader',
        'sass-loader'
      ]}
    ]
  }
```

Set up a simple test case for sass files, let webpack do its thing, and then simply import your files as needed. When I'm setting up a React project by hand there's really no question about this process and it feels like the right choice.

I never thought about other ways of processing `.scss` files until I started using scaffolding tools such as `create-react-app` cli.

## [Create React App](https://github.com/facebookincubator/create-react-app) is magic.

Anyone that has gone a few times through the slightly involved process of setting up a React project *by hand* would agree that there's a fair bit of smoke and mirrors happening with `create-react-app`.

First of all it takes you all in all about 30 seconds (install of `node_modules` included) to set up everything. It takes care of all your webpack settings and fine tunes Babel for a React project. Moreover, there are no traces whatsoever of *any of this magic*.

![Topher](/uploads/topher.gif)

Upon first inspection, there are no `webpack.config.js` or `.babelrc` files anywhere to be seen, just the familiar `/src` directory with the entry file to insert the root component by `ReactDOM` and an `App` component with some boilerplate content. Everything is styled beautifully with some `.css` imported directly into the `App` component.

When taking a look at the project's `package.json` file you would notice that **everything** is handled by `react-scripts`. These *scripts* also fall nothing short of magic, with a start script that lavishly launches `webpack-dev-server` with what I can only imagine is an `--open` flag as the app is automatically presented to you in Chrome. There are the expected build and test scripts with jest. You get the picture. This project, with all its bells and whistles comes with a single devDependency: `react-scripts`.


## Pay no attention to that man behind the curtain!

You might point out that `react-scripts` comes with an eject functionality, which basically allows you to lift the veil from everything responsible for this so called *magic*. The result is the permanent deletion of `react-scripts` and in its place all of the actual dependencies and configuration files of a regular React project.

It should also be noted that this eject functionality is presented to the developer as a "break glass in case of emergency" solution. The maintainers of `create-react-app` clearly don't want you using this feature and seemingly only provide it for edge cases. You're warned on numerous occasions that there is no going back from ejection and once the app is actually ejected they ask you to please submit feedback as to why you chose this irrevocable path.

## Okay, I won't eject

Create React App is a great tool for quickly starting off your project, but there were some things that I couldn't change right off the bat. An example would be configuring `.scss` files in your webpack module loaders.

With all the robust features provided by this tool it seemed unlikely that there wouldn't be a supported method of using sass in your projects. And there is. The method was slightly surprising for me as it completely ignores webpack and opts in for a separate process to watch and compile your sass files in place.

```
"scripts": {
    "build-css": "node-sass-chokidar src/ -o src/",
    "watch-css": "yarn run build-css && node-sass-chokidar src/ -o src/ --watch --recursive",
    "start-js": "react-scripts start",
    "start": "npm-run-all -p watch-css start-js",
    "build": "yarn run build-css && react-scripts build",
    "test": "react-scripts test --env=jsdom",
    "eject": "react-scripts eject"
  }
```

After installing the required dependencies and modifying the start scripts as shown above, you had a working solution where any `.scss` file found in the `/src` directory would be complied to `.css` and outputted to the same location. I wasn't particularly impressed with this solution as it required to have twice as many style files in my `/src` directory. Furthermore, it just felt like I was taking a step back in terms of tooling. After all, webpack is supposed to be your go to build tool and this solution placed it on the sideline.


## node-sass-what?

This finally brings me to the real questions that were prompted by this experience. Why choose another cli tool to watch and compile sass files? And while I'm at it, what is chokidar? According to the `create-react-app` docs, the normal `node-sass` module uses a watch process that is too wasteful on system resource. The `node-sass-chokidar` project README cites a similar reason and goes on to make claims that `node-sass` is up to 300% less efficient.

I understood the reason why the `create-react-app` developers chose the chokidar version of `node-sass`, after all, I had experience instabilities with `node-sass` in the past, which sometimes even led to runtime errors (most of which I solved by re-installing `node-sass`). What I still didn't get was why not opt in for a webpack solution.

## Black box tools

The title of this post might not be quite on point, as the most substantial questions that follow lean more towards questions about tooling and why people choose `create-react-app` itself.

Convenience is a big factor. I think these types of tools ought to be more critical about their end goals and the ways in which they achieve them. I believe the best tool is one which is powerful yet configurable. Because of this, I think that the maintainers of `create-react-app` have made a mistake by obscuring the majority of the configuration options inside of `react-scripts` (a black box).

## Discussion

Do you have an opinion on the subject? Would you eject your project to have access beyond the functionality provided by `react-scripts` or start a separate watch process as it is suggested in the Create React App docs? Give me a twitter shout-out [@ONZOart](https://twitter.com/intent/tweet?text=Thinking%20about%20watching%20or%20not%20watching&url=http%3A%2F%2Fbit.ly%2FnodeWatch&via=ONZOart) with your response.

## Related readings

I'm not the first one to ask this question (in a slightly different formulation).

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">To eject or not to eject? <a href="https://twitter.com/hashtag/CreateReactApp?src=hash">#CreateReactApp</a> <a href="https://twitter.com/hashtag/CRA?src=hash">#CRA</a></p>&mdash; Mihir K (@KarandikarMihir) <a href="https://twitter.com/KarandikarMihir/status/880031707600113664">June 28, 2017</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

This post is meant to be the beginning of a deeper dive into `create-react-app`. For the faults I mentioned above I think other people have things to say about them. It doesn't have to be a make or break situation. Here are a few readings I found interesting:

- [Porting enterprise React app to create-react-app](https://medium.com/@KarandikarMihir/porting-enterprise-react-app-to-create-react-app-bfb565a25460)
- [Configure create-react-app without ejecting ⏏](https://medium.com/@kitze/configure-create-react-app-without-ejecting-d8450e96196a)
