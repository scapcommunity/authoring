# Joval Continuous Monitoring: SCAP Authoring Use Cases & Requirements

_Please Note: this document is a work in progress._

## Use Cases
We have several internal and customer use cases. Here is a high-level description of each.

### Automated CVE OVAL Generation (internal)

We create and maintain an internal toolkit called the Joval Content Automation toolkit ("JCA"). 
This Python software runs continuously, monitoring external CVE-related data sources data sources
such as the Cisco OpenVuln API, the Microsoft Security Updates API, the NVD, and many others.
When new or changed CVEs are detected JCA analyzes the relevant data and generates new or updated
CVE OVAL definitions.

Currently, JCA uses its own Python-based capabilities to generate the requisite OVAL elements,
manage IDs, etc. but these only implement the specific OVAL elements/capabilities that have been
necessary so far. It would be preferable to leverage an existing general-purpose OVAL authoring
capability that:
- could be leveraged from Python
- could provide a simple, stable mechanism (i.e. DSL or API) for generating OVAL elements and OVAL definitions files
- would be remain current as the OVAL schemas are updated
- would support all OVAL features (we use variables, filters, functions, etc.)
- could generate/manage OVAL IDs to ensure uniqueness within some sort of context (e.g. a repo or org/use-case)
- could manage OVAL element version numbers
- would deduplicate OVAL elements automatically
- could schema and schematron validate the definitions and provide results in programmatically-consumable format
- would make it easy to leverage external OVAL elements (e.g. inventory definitions or commonly used elements from 3rd-party repositories)

### Compliance Content Authoring (internal and external)

We have customers and partners who require custom SCAP benchmarks to, for example, assess network
devices against their own internally-mandated configuration guidance. This requires authoring SCAP content
(OVAL & XCCDF) from the ground up. Sometimes we write the content for the customer and other times
they write and maintain the content themselves.

These customers have little-to-no SCAP expertise, so they require a simplified mechanism for expressing
the controls, metadata and associated checking logic. They are open to learning a DSL and/or using specialized
software so long as the learning curve is not particularly steep.

### End-user General-Purpose Content Creation

We have ISVs customers and partners that want to enable their end-users to easily create simple OVAL/SCAP
checks using a GUI. The ISV would like control over the implementation of the GUI (UI/UX), but would like
the rest of the authoring mechanics to be handled by an external solution.

### Upstream Content Revisions

We have customers and partners that leverage SCAP content provided by 3rd-parties ("upstream content") such as
CIS Benchmarks, DISA STIGs, Compliance as Code Benchmarks, NIST USGCB content and others. These customers often
need to make changes to the content that goes beyond the current capabilities of Tailoring including:
- changing XCCDF metadata (title, descriptions, fix text, etc.)
- adding custom metadata
- parameterizing OVAL values that haven't been exposed via external variables
- adding additional custom rules and/or checks

