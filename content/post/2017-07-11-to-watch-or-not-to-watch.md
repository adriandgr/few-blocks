---
title: "To watch or not to watch"
description: "A question about build tools"
date: 2017-07-11T18:13:27-04:00
tags: [
  "discussion",
  "performance",
  "dev tools"
]
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

Let webpack do its thing and then simply import your sass files as needed. When I'm setting up a React project by hand there's really no question about this process and it feels like the right choice. I never thought about other ways of doing processing `.scss` files until I started using scaffolding tools such as`create-react-app` cli.

## [Create React App](https://github.com/facebookincubator/create-react-app) is magic.

Anyone that has gone a few times through the slightly involved process of setting up a React project *by hand* would agree there's a fair bit of smoke and mirrors happening with `create-react-app`.

First of all it takes you all in all about 30 seconds (install of node_modules included) to set up everything. It takes care of all your webpack settings and fine tunes babel for a React project. Moreover, there are no traces whatsoever of any of this *magic*.

![Topher](/uploads/topher.gif)



```
node-sass-chokidar src/ -o src/ --watch --recursive
```

Do you have an opinion on the subject? Give me a twitter shout-out [@ONZOart](https://twitter.com/intent/tweet?text=Thinking%20about%20watching%20or%20not%20watching&url=http%3A%2F%2Fbit.ly%2FnodeWatch&via=ONZOart)