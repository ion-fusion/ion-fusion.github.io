---
title: The Ion Fusion programming language
layout: home
---

**Ion Fusion** is a programmable programming language for working with JSON and [Amazon Ion][ion]
data. Its goal is to simplify data processing by eliminating impedance mismatch and enabling
domain-specific custom syntax. Among its interesting characteristics:

* Fusion source code is Ion data, and the Fusion type system is a superset of the
  [Ion data model][data]. This reduces glue code such as object binding, and eliminates lossy type
  conversions.
* While Fusion facilitates general-purpose use, you can use syntactic abstractions to create custom
  syntax forms and Domain-Specific Languages, even those that are not as general as the core.

Linguistically, Fusion is a dialect of [Racket][], adapted to the Ion notation. Here's a quick
sample:

```
// Read each Ion value from stdin into local var `value`
(for [(value (in_port))]                 
  // ...and write its marketplace_id field to stdout
  (writeln (. value "marketplace_id")))  
```

[The `fusion` CLI][cli] has an interactive command console for experimentation, and a "batch" mode
for running scripts and pipelining data. The runtime can also be embedded into Java applications and
services, with some support for sandboxing untrusted code.

Ion Fusion started inside Amazon in 2012, and has been used in production for over a decade, driving
numerous data processing, workflow management, and analytics systems. It is now an independent 
[Apache-licensed][apache] project led by current and former Amazonians.

⚠️ This project is under active development, preparing for a 1.0 open source release. The language
itself is largely stable, but expect significant changes to Java APIs and packaging as we renovate 
everything for public development and use.
{: .notice--warning}

To try out the language, we recommend the [`fusion` CLI][cli], but at the moment you'll need to
[build it from source][build] (sorry).


# Support

This product is not owned or supported by Amazon or AWS, but by a small group of volunteers.
At this time we cannot promise any particular SLA for responding to issues.

Please submit bug reports and feature requests via [GitHub issues][issues].
If you have questions, feel free to reach out on our [Slack workspace][slack].


[apache]: {{ site.baseurl}}{% link license.md %}
[build]:  https://docs.ion-fusion.dev/latest/howto_build.html
[cli]:    https://docs.ion-fusion.dev/latest/about_cli.html
[data]:   https://amazon-ion.github.io/ion-docs/docs/spec.html
[ion]:    https://amazon-ion.github.io/ion-docs/index.html
[issues]: https://github.com/ion-fusion/fusion-java/issues
[Racket]: https://racket-lang.org/
[slack]:  https://join.slack.com/t/ion-fusion/shared_invite/zt-2y0jr8vh2-bZLa66hdyZ3ykHcgOcYkcA
