# SCAP Content Authoring Use Case Questions

Organization: Siemens

##	What type of SCAP content (vulnerability, specific compliance programs, OVAL, XCCDF, etc.) are you authoring and for what operating systems?

**Answer**

Security Configuration Baselines for OSes and Applications, corresponding
to XCCDF (authored in [Scapolite](https://github.com/scapolite/scapolite_docs/blob/master/201905_scap_v2_workshop/grobauer_siemens_scap_v2_experiences_scapolite.pdf) with proprietary extensions for expressing checks and fix
content. OVAL has not been much in focus so far
(we find that SCAP support in vulnerability scanners
is lacking in usability, even though the products are SCAP validated)), but is likely to become more important for us. 

##	Approximately how many OVAL/XCCDF authors are there in your organization?

**Answer**

I only can answer for central functions, where we have around
a dozen authors using Siemens' Scapolite format; there are some
authors using XCCDF/OVAL proper within Siemens, but 
but I have no numbers for this. But the numbers certainly
are low due to the high complexity of authoring SCAP.

##	What specific areas of content authoring are the most difficult for your authors?

- XCCDF cannot be authored and maintained in a way acceptable
  to authors without some kind of authoring tool. We have worked around this by creating the  [Scapolite](https://github.com/scapolite/scapolite_docs/blob/master/201905_scap_v2_workshop/grobauer_siemens_scap_v2_experiences_scapolite.pdf)  format, which allows us to

  - separate content into separate files
  - write Markdown rather than HTML
  - specify meta-information / machine-readable data in YAML rather than
    a mixture of XML elements and attributes

- OVAL is a huge challenge -- I see no chances that a larger
  group of people within our organization starts authoring OVAL
  because of its high complexity. 
  We need a way to specify standard checks in an easy syntax
  and then tooling to transform them into OVAL.

**Answer**

## Would some measure of automation assist in the authoring of the content that you are developing?

**Answer**

Yes, especially for creating OVAL (regarding XCCDF, we are fine
with what Scapolite gives us)

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

## Do you perform any customizations to existing SCAP content or 3rd party SCAP content?

**Answer**

Yes, we base internal baselines on externally available SCAP content.

## How do you store the content you create? 

Examples:

- Directories in a file system.
- Database.
- Content is loaded into scanning tools.
- GitHub.
- Other version control systems.

**Answer**

Text files in a git repository, see 

https://github.com/scapolite/example_iase_win_server_2016_v1r7

for an example.

## From which external SCAP sources do you collect content?

**Answer**

Mostly CIS, IASE/DISA, Compliance as Code.

## What tools do you use to create SCAP content? Are you satisfied with your current tools?

**Answer**

Own-developed format (Scapolite) and supporting tooling. 
See https://github.com/scapolite/scapolite_docs/blob/master/201905_scap_v2_workshop/grobauer_siemens_scap_v2_experiences_scapolite.pdf

for further information.

##	How willing would you be to change the tools that you are currently using if a general-purpose SCAP authoring solution was to be developed?

**Answer**

To be honest, my hope is that the input for a general-purpose SCAP  authoring solution would be close enough to what Scapolite
looks like, so that we could migrate our content and our tooling.

If that should not be the case, chances are that we would stick
with Scapolite (we already have made quite a bit of investment)
and try to use whatever we can in conjunction (e.g., a system
for compiling checks in a YAML syntax or similar into OVAL
could easily be plugged into our tooling).


##	Are there any challenges your organization would face when adopting a new SCAP authoring solution?

Examples:

- Programming language lock-in.
- Ongoing internal tool development.
- Browser-based versus compiled code.

**Answer**

As stated above: we have ongoing internal format and tool development --
whether we could adopt a SCAP authoring solution would depend
on how much we would have to change what we already have and use.


## Would your organization be willing to provide occasional feedback during the development of an authoring solution?

**Answer**

Yes.

## Would your organization consider contributing software development resources toward the development of an SCAP authoring solution?

**Answer**
 
We are co-operating with academia regarding the topic of hardening.
It could be possible to support development activities as part
of this co-operation, e.g., defining B.Sc. or M.Sc. thesis
topics with an implementation component.

## Capabilities

Which of the following capabilities would you be interested in seeing in a general-purpose SCAP authoring tool?

1. The ability to specify common actions (e.g., "check registry key," "check file presence") and have the tool generate content without forcing the author to understand the underlying OVAL/XCCDF language structures. 
2. Support for version/revision control in your tools for content.
3. The ability to define "macros" and "libraries" that can be saved to be used in future content.
4. Difference tracking between content sources.

**Answer**


- "1" with highest priority to enable our organization to
  author OVAL checks
- "4" would be very helpful, but most likely cannot be
  solved by tooling alone, but also depends on conventions
  being observed by content producers
- "2" depends at least to a part on how content is stored,
  so I am currently not sure how much a tool could help
  here (unless the "tool" is a full-blown application including
  content storage in some kind of database; my understanding
  of the authoring system is more that of a command-line tool
  for transforming a author-friendly representation into SCAP,
  along with the core library used by this tool)
- "3" has to be examined: a balance between offering short cuts
  and keeping the system usable for authors that are 
  themselves not programmers must be found.

## Requirements

Please specify importance of the following high-level features and capabilities to your organization:

*Answer* 

(Note that below, I consider things 'somewhat important', for
which we already have a solution base on Scapolite in place; 
if we did not have this, these requirements would be "very important".)


- Simplified SCAP content creation for authors with little-to-no SCAP knowledge: Somewhat important

- Tooling that makes SCAP experts more efficient (facilitating content re-use, ID management, change tracking, etc.): Very important

- Automation-friendly tooling (APIs, code libraries, etc.) that provides a simple, stable mechanism for generating SCAP component elements (OVAL elements, XCCDF Benchmarks, etc.): Very important 

- Support for the latest SCAP component specification versions (OVAL, XCCDF, etc.): Very important 

- Support for legacy SCAP component specification versions more than a few years old:  Not important

- Creating individual OVAL Definitions and OVAL Definitions Files (no XCCDF Benchmark): Very important 

- Creating XCCDF Benchmarks using existing OVAL checks (no OVAL creation): Somewhat important

- Creating XCCDF Benchmarks and corresponding OVAL checks:  Somewhat important 
