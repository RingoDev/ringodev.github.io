---
title: "Open Source SCA tooling for SBOMs and VEX on GitHub"
---

Recently, I conducted a broad search across GitHub to identify open-source tooling related to Software Bill of
Materials (SBOMs) and Vulnerability Exploitability eXchange (VEX). This exploration led to some interesting findings
about the security tooling ecosystem as well as an open source contribution.

One key takeaway was how powerful ChatGPT is at generating Python scripts that efficiently automate tasks. The ability
to quickly prototype and iterate made information gathering significantly easier. It already knew everything about
GitHub's APIs as well as how to formulate and use structured queries.
Can very much recommend!

## What did I search for?

I tried to get a general grip for open source tooling that somehow relates to SBOM or VEX documents. To achieve that I
ran following queries:

![img.png](assets/img/search-queries.png)

The 74 unique results were categorized by following dimensions:

1. **SBOM Generation**: Does the tool support the generation of SBOMs e.g. by scanning
   artifacts or package manager manifests?
2. **SBOM Consumption**: Does the tool support open-source vulnerability detection through
   SBOM integration?
3. **VEX Generation**: Is the tool capable of generating (positive or negative) VEX
   documents?
4. **VEX Consumption**: Can the tool use negative assessments from VEX data to “mute”
   non-exploitable vulnerabilities and reduce false positive matches?

## Main Findings

The main finding was that there are not that many tools capable of consuming an SBOM and using a VEX file to filter out
non-exploitable vulnerabilities. In fact, I identified only a few tools in my structured search that support this
functionality.

![img.png](assets/img/search-result.png)

However, most of the tools I analyzed rely on static, local file-based approaches rather than dynamic integration. The
burden to find and provide a VEX file to a scanner is still on the consumer, rather than the SBOM producer.

## Contributing to Trivy

To address this gap, I decided to [contribute to Trivy](https://github.com/aquasecurity/trivy/pull/8254){:target="_blank"}
by adding the capability to resolve external references from CycloneDX SBOMs. This enhancement enables Trivy to fetch relevant VEX
data dynamically from locations specified by the SBOM creator, moving towards end-to-end automation across ecosystems.

While this is a step forward, Trivy still requires an explicit SBOM scan and does not yet seem to be able to resolve
SBOM's attached with Cosign. This might be the next feature I contribute—let’s see! Writing Go
code has been a fun challenge, and I'm excited about further improvements to security automation.

## Final Thoughts

There is still a long way to go in making VEX a seamless part of security workflows. The industry needs more tooling
that supports automated, producer-driven vulnerability management. I hope that with smallish contributions like these,
we can push the ecosystem forward towards a more automated and scalable approach to supply chain security.

## PS: Random Insights from My Search

One surprising discovery was that the term "**VEX**" is also used in video production,
particularly in the [Houdini](https://www.sidefx.com/docs/houdini/index.html) project.

I love learning new stuff every day!