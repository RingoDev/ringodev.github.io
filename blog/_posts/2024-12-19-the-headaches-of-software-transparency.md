---
title: "The headaches of software transparency"
---

When non-techies hear the term supply chain, they might think of factories, logistics hubs, or shipping containers. But
in the world of software, the supply chain looks entirely different—and far more invisible. It’s a web of interconnected
components, dependencies, and libraries sourced from an array of open-source contributors, many of whom are unknown to
the end user.

While this model that is built on largely unpaid labor has revolutionized how we build software, it has also opened a
Pandora’s box of security risks. According to Sonatype’s 2024 report on
the [State of the Software Supply Chain](https://www.sonatype.com/state-of-the-software-supply-chain/introduction){:
target="_blank"}, the average application is now composed of 180 open-source components. This level of complexity is one
of the main reasons why the software supply chain has become a prime target for attackers.

And the stakes? They’re massive. A single breach can ripple through hundreds of organizations, leaving a trail of
compromised systems and breached data in its wake. Take
the [SolarWinds attack](https://www.ncsc.gov.uk/collection/ncsc-annual-review-2021/the-threat/solarwinds)
{:target="_blank"}, a cyber-espionage campaign so brazen it made global headlines. Attackers slipped malicious code into
routine software updates, creating a backdoor that infiltrated thousands of customers government agencies included.

Such incidents aren’t just cautionary tales; they’re road signs screaming _Danger Ahead_. They highlight a harsh
reality:
our reliance on open-source components and shared code isn’t just a strength it’s also a liability.

## Enter SBOMs: The One to Rule Them All

To combat these threats,
the [US government is pushing for greater transparency](https://www.whitehouse.gov/briefing-room/presidential-actions/2021/05/12/executive-order-on-improving-the-nations-cybersecurity/){:
target="_blank} in software development. Enter the Software Bill of Materials (SBOM). Think of an SBOM as a detailed
ingredients list for software.

It tells you exactly what’s under the hood; every library, dependency, and component. With an SBOM, organizations can
monitor their software for components with known vulnerabilities and act fast when issues arise.

In theory, it sounds like a win-win. But in practice, publishing an SBOM isn’t as simple as it seems. Imagine sharing
your software’s recipe with the world; now anyone can scrutinize it, scanning for vulnerabilities with tools
like [Trivy](https://trivy.dev/){:target="_blank"} or [Grype](https://github.com/anchore/grype){:target="_blank"}. Even
when those vulnerable components don’t pose a real risk in the way they are used in the distributed product, vendors are
left explaining themselves to concerned customers, creating a new kind of operational headache.

## Bridging the Gap with VEX

Enter VEX: the Vulnerability Exploitability eXchange standard. While SBOMs list every ingredient, VEX answers the
critical follow-up question: Does this vulnerability actually affect me?
Being [endorsed by CISA](https://www.cisa.gov/sites/default/files/2023-01/VEX_Status_Justification_Jun22.pdf){:target="_
blank"}, VEX allows vendors to communicate whether a disclosed vulnerability is exploitable in their product, cutting
through the noise and reducing unnecessary panic.

But as promising as VEX is, it’s no silver bullet. The surrounding ecosystem is fragmented, with multiple standards like
CSAF, OpenVEX, CycloneDX Vulnerabilities, and SPDX Vulnerability Profiles all serving similar use cases, but none of
them being quite compatible with each other.

Beyond the challenge of standardization lies another critical hurdle: how to distribute that VEX information
effectively. Unlike SBOMs, which are typically static and can be distributed as files alongside the shipped product, VEX
information is inherently dynamic. Vulnerabilities are constantly being discovered, analyzed, and re-evaluated, meaning
VEX statements need frequent updates to remain relevant.

This dynamic nature poses several questions: Should VEX information be distributed through files, similar to SBOMs, or
through APIs that allow for real-time updates? How can organizations ensure that the latest VEX information reaches the
right stakeholders across the supply chain, especially in industries with continuous release cycles? And what happens
when an outdated VEX statement lingers in a system, potentially misleading decision-makers?

These challenges are not trivial. Effective distribution requires more than just technical solutions; it demands robust
workflows, automation, and interoperability between tools. Without these, the promise of VEX as a scalable solution to
vulnerability management remains out of reach, leaving organizations to grapple with the complexity of an ever-evolving
threat landscape.

## What Does the Future Hold?

These challenges have not gone unnoticed. Both OWASP and OpenSSF are rolling up their sleeves to tackle these issues
head-on with dedicated working groups and innovative ideas.

A working group lead by OWASP is brewing up something exciting:
the [Transparency Exchange API (TEA) and the Transparency Exchange Identifier (TEI)](https://github.com/CycloneDX/transparency-exchange-api){:
target="_blank"}. Picture it as unique code such as GTIN, UPC or EAN for every shipped software product that allows to
discover a standardized API for transparency data, designed to streamline how artifacts like SBOM or VEX documents are
discovered and shared. It’s an ambitious project with the potential to reshape how organizations exchange critical
software metadata, making the process automatable, and more reliable.

On the other side, the [OpenVEX Special Interest Group (SIG)](https://github.com/ossf/OpenVEX){:target="_blank"} is
doubling down on simplicity and integration. Their minimalist approach to VEX with the OpenVEX format is all about
adaptability in building a format that doesn’t just work on its own but plays well with others. They’ve also released
a [Go module on GitHub](https://github.com/openvex/discovery){:target="_blank"} that lets you discover VEX data directly
from containers in OCI registries, where much of today’s software lives and breathes. This could make accessing VEX data
as seamless as pulling the latest Docker image.

These initiatives are promising. They’re lighting the way toward a future where software transparency isn’t a headache
but a given. However, like all great ideas, they’ll need time to grow and a helping hand from the open-source community.
The tools are being built, but it’s collective action that will bring these solutions to life and ensure they deliver on
their potential.

The bottom line? The future is bright, but it needs nurturing. With the right support, these efforts could redefine how
we get a grip as an industry on software supply chain security.

---

Stay tuned for the next post where I'll go down the rabbit hole of the current state of VEX adoption by open-source
security tooling and where it can bring value **today**.
