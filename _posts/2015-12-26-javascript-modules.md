---
title: "JavaScript Modules"
description: How to deal with them
date: 2015-12-26 19:18:00
---

There are quite a few ways to split your JavaScript files into different chunks or modules.
CommonJS (popularized by [node](https://nodejs.org)), AMD and the new native syntax introduced in ES2015.

Now, this is great and all but how do we run this in the browser? The new ES2015 syntax is not working in any browser and browsers don't know about `require`.

## Multiple Options

CommonJS can be easily converted to ES5 with [Browserify](http://browserify.org/).

[Webpack](http://webpack.github.io/), which categorizes itself as a module bundler, handles both CommonJS and AMD.

"Ok, cool, so we covered CommonJS and AMD but what about ES2015 modules?"

Again, multiple options here!

Use [SystemJS](https://github.com/systemjs/systemjs). SystemJS loads ES6 modules, AMD, CommonJS and global scripts in the browser and NodeJS.
It also comes with its own package manager, [jspm](http://jspm.io/).

New kid on the block is, [Rich Harris'](https://github.com/Rich-Harris) [Rollup](http://rollupjs.org). Rollup is "the next-generation JavaScript module bundler" and does this efficiently. Rollup eliminates unused library code with *tree-shaking*.

"Tree what?"

Basically Rollup does *dead code elimination*.

<img class="x2 center" src="{{ site.baseurl }}assets/images/tree.png" />

"So what not call it that, then?"

Well, actually instead of excluding dead code, it only includes live code. Confused? Rich Harris himself made an [explanatory blog post](https://medium.com/@Rich_Harris/tree-shaking-versus-dead-code-elimination-d3765df85c80) about this.

Webpack 2 (which is now in beta) will also support the ES2015 syntax. Awesomeness!    
Bonus: Webpack 2 also supports tree shaking!

"Allright, so that is the module part tackled, but what about actual ES2015 support?"

The trick is to use a transpiler. 2 popular transpilers are [Babel](http://babeljs.io) and [Traceur](https://github.com/google/traceur-compiler).

Webpack 2, for example, will only transpile imports and exports to ES5. If you need to transpile the rest to ES5, you can use, what webpack calls, loaders. Loaders are basically plugins.
We'll use the Babel loader for transpilation.

There is one catch though. Since version 6, Babel was modularized and uses presets to transpile your code.
There's a preset called [es2015](http://babeljs.io/docs/plugins/preset-es2015/). You would think you could just use this one and you would be done, but here's the thing. The preset also includes the `transform-es2015-modules-commonjs` plugin. Which, you guessed it, transpiles your ES2015 modules to CommonJS.
That way Webpack would not be able to tree shake and your final bundle would not be optimal.

The solution is to include *all but* the `transform-es2015-modules-commonjs` plugin in your configuration file.
Hopefully Babel will launch a new preset without the CommonJS modules plugin. *Hint hint*

Rollup tackled this issue by creating it's own preset called [babel-preset-es2015-rollup](https://github.com/rollup/babel-preset-es2015-rollup).

Browserify uses the [Babelify](https://github.com/babel/babelify) transformer. As Browserify works with CommonJS you *can* use Babel's [es2015](http://babeljs.io/docs/plugins/preset-es2015/) preset.

In SystemJS you can also use bower to transpile to ES5.

## Conclusion
Lot's of options! Even if you are using the ES2015 syntax.

Personally I think Webpack 2 is the most promising one of the bunch. At [Showpad](http://www.showpad.com), the company where I currently work, we also decided to use Webpack 2 for new projects.

But in the end it's all about personal taste.

Got inspired by our brainstorm session at work, [2ality's post about tree shaking](http://www.2ality.com/2015/12/webpack-tree-shaking.html) and [Rich Hariss' post about tree shaking](https://medium.com/@Rich_Harris/tree-shaking-versus-dead-code-elimination-d3765df85c80) to write this blog post.
