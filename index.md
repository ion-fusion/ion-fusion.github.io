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

To try out the language, check out the `fusion` CLI [tutorial][cli]. The CLI 
enables running scripts and pipelining data, and has an interactive console for
experimentation. You can use the `fusion-java` [library][] to embed the runtime
into Java applications and services, with support for sandboxing untrusted code.

Ion Fusion has empowered production services inside Amazon for over a decade, driving
numerous data processing, workflow management, and analytics systems. It is now an independent 
[Apache-licensed][apache] project led by current and former Amazonians.

⚠️ This project is under active development, preparing for a 1.0 open source release. The language
itself is largely stable, but expect significant changes to Java APIs and packaging as we renovate 
everything for public development and use.
{: .notice--warning}


[apache]: {{ site.baseurl}}{% link license.md %}
[cli]:    https://docs.ion-fusion.dev/latest/tutorial_cli.html
[data]:   https://amazon-ion.github.io/ion-docs/docs/spec.html
[ion]:    https://amazon-ion.github.io/ion-docs/index.html
[library]: https://docs.ion-fusion.dev/latest/javadoc/
[Racket]: https://racket-lang.org/
