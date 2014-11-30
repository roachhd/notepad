---
layout: post
title: "Get Your Badge On"
share: true
comments: true
category: Tips n Tricks
tags: [geek, open-source, badges]
---
I love adding badges to my projects. It's an easy way to quickly check dependencies are up to date, and build are passing. Others are just to show what services you use on the project, and others just for fun. So what can you use badges for? Check out the list below for some examples.

##### What kind of meta data can you convey using badges?

- test build status: `build | failing`
- code coverage percentage: `coverage | 80%`
- stable release version: `version | 1.2.3`
- package manager release: `gem | 1.2.3`
- status of third-party dependencies: `dependencies | out-of-date`
- static code analysis GPA: `code climate | 3.8`
- [semver](http://semver.org/) version observance: `semver | 2.0.0`
- amount of [gittip](http://gittip.com) donations per week: `tips | $2/week`


###### Services that give you badges! (using the Shields standard)
- [Travis CI](https://github.com/travis-ci/travis-ci/issues/630#issuecomment-38054967)
- [Code Climate](https://codeclimate.com/changelog/510d4fde56b102523a0004bf)
- [Coveralls](https://coveralls.io/r/kaize/nastachku)
- [Gemfury/RubyGems](http://badge.fury.io/)
- [Gemnasium](http://support.gemnasium.com/forums/236528-general/suggestions/5518400-use-svg-for-badges-so-they-still-look-sharp-on-r)
- [Scrutinizer CI](https://scrutinizer-ci.com/)
- [Semaphore](https://semaphoreapp.com)
- [VersionEye][]
- [Read the Docs](https://readthedocs.org/)
- [BadgerBadgerBadger][gem]
- [badges2svg][]
- [reposs][]
- [ruby-gem-downloads-badge][]

##### Do you Grunt?

Do you use Grunt in a project? If so you should proudly display that in your project README or on your project website? Now you can with the "Built with Grunt" badge!

Built with Grunt
[![Built with Grunt](https://cdn.gruntjs.com/builtwith.png)](http://gruntjs.com/)

###### Using the Badge

Just copy the following Markdown code snippet and paste it right underneath the headline in your project README. You can also put it on your project website homepage or footer.

```markdown
[![Built with Grunt](https://cdn.gruntjs.com/builtwith.png)](http://gruntjs.com/)
```

If you need an HTML version, we've got you covered.

```html
<a href="http://gruntjs.com/"><img src="https://cdn.gruntjs.com/builtwith.png" alt="Built with Grunt"></a>
```

[gem]: https://github.com/badges/badgerbadgerbadger
[badges2svg]: https://github.com/bfontaine/badges2svg
[reposs]: https://github.com/rexfinn/reposs
[VersionEye]: https://www.versioneye.com/
[ruby-gem-downloads-badge]: https://github.com/bogdanRada/ruby-gem-downloads-badge/
