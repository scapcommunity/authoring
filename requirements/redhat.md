# Red Hat: SCAP Authoring Use Cases & Requirements

_Please Note: this document is a work in progress._

## Use Cases
We have several internal and customer use cases. Here is a high-level description of each.

### Automated SCAP Generation

Generating and creating SCAP content is currently too complicated. It would be preferable to
leverage an existing general-purpose OVAL authoring capability that can be utilized by system, GUI, and Web
frameworks such that:
- written in a modern language and code agnostic such that it can be used in a system language (C/C++, Rust, etc.)
  or a cloud-native language (Golang)
- could provide a simple, stable mechanism (i.e. DSL or API) for generating SCAP elements and SCAP files
- would be remain current as the SCAP schemas are updated
- could schema and schematron validate the definitions and provide results in programmatically-consumable format

### Compliance Content Authoring (internal and external)

We have customers and partners who require custom SCAP benchmarks to handle specific site-local or agency
security requirements which requires authoring SCAP content. Sometimes, we write the content for the customer and other times
they write and maintain the content themselves.

These customers have little-to-no SCAP expertise, so they require a simplified mechanism for expressing
the controls, metadata and associated checking logic. They are open to learning a DSL and/or using specialized
software so long as:

1. The learning curve is not particularly steep.
2. The DSL is not written to a particialar piece of technology (e.g. Ruby, Python, JS, etc.)

### End-user General-Purpose Content Creation

We have ISVs customers and partners that want to enable their end-users to easily create simple SCAP
content without using a GUI.

### Tailoring

In some cases, customers need to be able to add custom rules and/or checks. This can be done through tailoring
or via adding new elements to SCAP to allow external content. Changes via tailoring need to be thought through
as they have direct compliance and even security implications. For example, changing XCCDF metadata (title,
descriptions, fix text, etc.) broadens the attack vector in SCAP and shouldn't be allowed if SCAP content is
signed by the author, or prohibitChanges is set. Changing signed content invalidates that content and signature.
New attributes would probably need to be created to allow some changes but not all.

Adding a `git diff` type of functionality would be one of the best ways to add functionality to identify and
assist in the changes between upstream and downstream.

