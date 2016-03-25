---
title: Promise defer
date: 2016-01-25 10:18:00
description: Lost treasure chest
---

With ES2015 getting more and more mainstream, people are starting to use the native Promise API.
Your typical ES2015 Promise looks like this:

```js
const hackBank = () => {
    return new Promise(resolver);

    function resolver (resolve, reject) {
        // do some async stuff

        if (/* everything went according to plan */) {
            resolve('got the money');
        } else {
            reject(Error('alarm went off'));
        }
    }
}
```

It's arguable very cool to have this tool inside EcmaScript, but I recently stumbled upon an issue where I needed to have a defer. You know, like `jQuery.Deferred` or `$q.defer`. Turns out this does not exist in native Promise land.

After chit chatting with colleagues and searching the interwebs this is what came out:

{% gist 9c67215d7f1f5e92f14d %}

Hopla! Enjoy doing stuff like:

```js
const myDefer = defer();

myDefer.resolve();
// or
myDefer.reject();

myDefer.promise
    .then(/* great success */)
    .catch(/* mega fail */);

```
