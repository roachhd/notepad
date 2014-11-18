---
layout: post
title: Package Dependencies Done Right
category: Reference
tags: [tech, geek, dev, tips, dependencies]
share: true
comments: true
---
"Best practices" is a term that is often misused and thus can be ambiguous in this context. For such reasons, it is important to make clear the goals behind this particular versioning scheme:

1. Strive to be forwards compatible with node.js (within reason) 
2. Keep the dependencies of multiple installations of the same app cohesive 
3. Reduce the surface area of potential bugs due to breaking changes

Here is a sample package.json that uses the best practices we will discuss:

```json
{
  "name": "best-practices",
  "description": "A package using versioning best-practices",
  "author": "Charlie Robbins <charlie@nodejitsu.com>",
  "dependencies": {
    "colors": "0.x.x",
    "express": "2.3.x",
    "optimist": "0.2.x"
  },
  "devDependencies": {
    "vows": "0.5.x"
  },
  "engine": "node >= 0.4.1"
}
```

__When specifying modules dependencies: use `1.0.x` syntax__

Until recently, I was guilty of not following this guideline: I continued to use the `>= 0.2.0` syntax illustrated above in the naive.package.json example. At first glance there doesn't seem to be anything wrong with that style. You're saying "If there are changes in the future I want them." 

The problem arises because authors are conveying meaning in their versions. Not every version will be completely backwards compatible with the particular version you were using when you wrote your application. This is conveyed in the version string:

e.g.: 0.3.18
- Major Version (0) 
- Minor Version (3)
- Patch Version (18)

Changes to the major and minor parts of the version mean that changes have happened, although there is no convention to convey they are breaking. Changes to patch versions are used to express that a fix has been made and it is (usually) safe to upgrade.

Conversely, when using the `0.2.x` syntax you're saying: "If there are patch changes in the future I want them, but no minor or major versions." Given the description of the meaning conveyed by each of the version components above this means you won't __be tearing your hair out over breaking changes in a module you depend on.__

__When specifying node versions in apps: use `0.4.x` or `0.4.0` syntax
__

As with any sufficiently important problem, there are nuances to dependency management you should be aware of. One such nuance is the difference between specifying dependencies in an application vs. modules. 

Module authors encounter a much wider surface area of use cases, and as such should be more liberal in the versions of node.js they accept. On the other hand, application developers typically have no upstream dependencies and should be more explicit about what version of node.js they are expecting on the target system.

Take advantage of devDependencies

The package.json specification used by npm has an additional property for separately listing dependencies which are only required for development purposes. Why separate you might ask? Besides not having to download these dependencies from the registry when running in production, npm it is required if you wish to take advantage of a couple of neat npm features such as test:

``` json
$ pwd
  /Users/charlie/GitHub/nconf

  $ npm test
  npm info it worked if it ends with ok
  npm info using npm@1.0.6
  npm info using node@v0.4.8
  npm info pretest nconf@0.1.9
  npm info test nconf@0.1.9

  > nconf@0.1.9 test /Users/Charlie/GitHub/nconf
  > vows test/*-test.js --spec

  (...)
```

If I had not specified my test library, vows, in the devDependencies section of the package.json for nconf I would have received:

```json
  $ npm test
  npm info it worked if it ends with ok
  npm info using npm@1.0.6
  npm info using node@v0.4.8
  npm info pretest nconf@0.1.9
  npm info test nconf@0.1.9

  > nconf@0.1.9 test /Users/Charlie/GitHub/nconf
  > vows test/*-test.js --spec

  sh: vows: command not found
  npm info nconf@0.1.9 Failed to exec test script
  npm ERR! nconf@0.1.9 test: `vows test/*-test.js --spec`
  npm ERR! `sh "-c" "vows test/*-test.js --spec"` failed with 127
  npm ERR! 
  npm ERR! Failed at the nconf@0.1.9 test script.

  (...)
```

#####Conclusion

Node.js is evolving rapidly: it has been less than a month since npm 1.0 was released which dramatically changed the way in which dependencies are handled. More importantly: the modules on-top of node.js critical to building scalable web applications are evolving even faster, making the best practices outlined here that much more important if you want to cope.

Thanks [nodejitsu](http://blog.nodejitsu.com/) for ask your brilliant info.
