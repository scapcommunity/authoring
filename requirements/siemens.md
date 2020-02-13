# Siemens: SCAP Authoring Use Cases & Requirements

_Please Note: this document is a work in progress._

## Use Cases
We have several use cases. Here is a high-level description of each.

### Lightweight OVAL generation

In Scapolite, we write down checks and implementations in a YAML syntax that is (hopefully) easy
to read and write. Just as OVAL has system/OS-specific extensions, syntax and semantics for
these YAML parts are defined per use-case (e.g., implementing/checking Windows registry entries)
Where possible, we would like to generate OVAL from these entries rather than maintaining an
OVAL check in parallel. Thus, a library that can be extended with plugins for generating
OVAL for certain use-cases would be extremely benefitial.

Here are some examples of what we would like to transform into OVAL:

- a simple registry entry:

  ~~~
   - system: org.scapolite.implementation.windows_registry
     config: User
     registry_key: Software\Policies\Microsoft\Assistance\Client\1.0
     value_name: NoImplicitFeedback
     action: DWORD:1
  ~~~

- an entry which manifests itself in the `.inf` file which is part of an GPO export in the `System Access` section
  (note that here, we have both a value, which is the default value used for implementation and constraints on the
   value for checking)

  ~~~
  - system: org.scapolite.implementation.win_secedit
    setting_name: MaximumPasswordAge
    section: System Access
    value: 60
    constraints:
      max: 60
      min: 1
  ~~~

The "general-purpose OVAL authoring capability" as proposed by JOVAL would be 
extremely helpful for us, too.

### XCCDF and SCAP content generation

We are using our own "Scapolite" format to author and maintain content. Currently, the
export back to XCCDF and other SCAP formats is in a PoC stage and very much tailored
to our current needs. Better quality and better extensibility to features that we currently
are not using could be achieved with the help of a library for generating not only OVAL, but
also (e.g., XCCDF) (for the composition of datastreams from XCCDF and OVAL, Redhat's `oscap` tool is working very nicely.)

We have customers and partners who require custom SCAP benchmarks to, for example, assess network
devices against their own internally-mandated configuration guidance. This requires authoring SCAP content
(OVAL & XCCDF) from the ground up. Sometimes we write the content for the customer and other times
they write and maintain the content themselves.

Regarding the DSL mentioned by Joval: with Scapolite, we already have a DSL. Obviously, not all
design decisions we have taken in Scapolite will be a good fit for everybody, but we
think that taking Scapolite as a starting point for a possible content-authoring DSL
will yield faster and better results than starting from scratch.

### Upstream Content Revisions

We have the same requirement as JOVAL for enhanced possiblities for tailoring content.
I quote the list of required tailoring capabilities provided by JOVAL:

- changing XCCDF metadata (title, descriptions, fix text, etc.)
- adding custom metadata
- parameterizing OVAL values that haven't been exposed via external variables
- adding additional custom rules and/or checks
