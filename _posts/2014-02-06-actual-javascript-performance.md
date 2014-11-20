---
layout: post
title: Actual JavaScript Engine Performance
---

JavaScript Performance
(Smaller is better)

| Browser |  Seconds |
| ------- | -------- |
| Chrome 10.0.648.205 |  2.801 |
| Chrome 13.0.754.0 canary |  0.543 |
| Firefox 4.0.1 |  0.956 |
| IE 9.0.8112.16421 64 |  1.159 |
| IE 10.0.1000.16394 |  0.562 |
| Opera 11.10 |  1.106 |
| Safari 5.0.5 (7533.21.10) |  0.984 |

[JSMeter: Measuring JavaScript Behavior in the Wild][1] showed that benchmarks are not representative of the behavior of real web applications. But lacking credible benchmarks, engine developers are tuning to what they have. The danger is that the performance of the engines will be tuned to non-representative benchmarks, and then programming styles will be skewed to get the best performance from the mistuned engines.

So I have come up with a benchmark that should be more representative of large, well-written JavaScript applications. It is in fact a popular, large, well-written JavaScript application: [JSLint][2].

The table shows the results on running JSLint on its main source file, [jslint.js][3], using the Good Parts options. I think these results are more indicative of actual JavaScript engine performance than those provided by the performance-oriented benchmarks.

[1]: http://research.microsoft.com/pubs/118663/paper_tr.pdf
[2]: http://www.JSLint.com/
[3]: https://github.com/douglascrockford/JSLint/blob/master/jslint.js

