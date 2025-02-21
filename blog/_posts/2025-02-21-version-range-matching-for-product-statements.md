---
title: "Version Ranges and OS Contributions"
---

With the research I've been doing on and off over the past few months on the [Vulnerability Exploitability eXchange
(VEX)](./os-sca-tooling-for-sboms-and-vex-on-github), I took a deep dive into how it's possible to declare statements for any software component. For example, if a
product is *not affected* by a certain vulnerability, you probably want to communicate this to your customer, but don't
want to manage a long list of all the potential product versions you have out there in the wild. This is why you likely
want to apply that statement to a specific set of (existing or future) versions of your shipped product.

To address this, I looked into the **VERS** standard, which is currently part of
the [purl-spec repository](https://github.com/package-url/purl-spec){:target="_blank"}.

VERS allows the creation of a concise yet human-readable URI such as `pkg:generic/>1.2|!1.2.1|<1.3|2.1` that enables
anyone to define and match version ranges, no matter if explicit versions are already known.

### Implementing VERS Overlap Support

As part of my personal project, where I'm working on a management layer for publishing and providing such statements, I
decided to use a [library that implements VERS support](https://github.com/nscuro/versatile){:target="_blank"}.

However, I noticed something missing: there was no way to validate whether two version range specifiers could
potentially overlap, which could lead to conflicting statements.

Thankfully, implementing this check was quite straightforward. Even better, after
opening [a pull request](https://github.com/nscuro/versatile/pull/167){:target="_blank"}, my feature was
merged upstream within minutes.

**Open Source is kind of addictive!** 🚀  
