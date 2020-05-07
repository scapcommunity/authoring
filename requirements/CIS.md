# SCAP Content Authoring Use Case Questions

Organization: CIS

##	What type of SCAP content (vulnerability, specific compliance programs, OVAL, XCCDF, etc.) are you authoring and for what operating systems?

CIS benchmark developers, consensus teams, and members contribute to the authoring and tailoring of configuration/compliance recommendations, ultimately generating SCAP content in the form of XCCDF, OVAL, CPE-Dictionary, and CPE-OVAL format.

##	Approximately how many OVAL/XCCDF authors are there in your organization?

The internal CIS benchmark development team is approximately 15 regular authors.  Many more (100+) end users are involved in tailoring activities specific to their organization.

##	What specific areas of content authoring are the most difficult for your authors?

New platform coverage in SCAP formats.  As technologies advance, and new CIS Benchmarks are developed, we have a difficult time keeping up with those new technologies in OVAL content.  We have limited resources who are well-enough versed in OVAL schema authoring.

## Would some measure of automation assist in the authoring of the content that you are developing?

If that automation assists in the creation of new OVAL schema documentation and proposal to the OVAL community, yes.

## Do you perform any customizations to existing SCAP content or 3rd party SCAP content?

CIS is a content creator.  Our authoring platform allows for the creation of CIS SCAP content and allows our SecureSuite members to tailor that content as well.

## How do you store the content you create? 

The content is stored in an in-house built application database.

## From which external SCAP sources do you collect content?

Our Configuration Assessment Tool (CIS-CAT) is capable of downloading SCAP content (specifically OVAL vulnerability definitions) from the following sources:
- The CIS-hosted OVAL repository
- Red Hat
- Novell (SuSE)
- Canonical (Ubuntu)

This content is used specifically within the CIS-CAT software.  It is not used to assist in content authoring.

## What tools do you use to create SCAP content? Are you satisfied with your current tools?

CIS uses in-house built software to transform information entered into our WorkBench authoring tool into SCAP content.  Yes, we're very satisfied with the toolchain.


##	How willing would you be to change the tools that you are currently using if a general-purpose SCAP authoring solution was to be developed?

Depending on evaluation of an authoring solution, and if there's potential for integration with existing tools, CIS would be willing.

##	Are there any challenges your organization would face when adopting a new SCAP authoring solution?

Given that CIS currently supports multiple teams involved in both Benchmark and SCAP content creation, there are a number of challenges.  A new SCAP authoring solution would need to meet a very high threshold/standard in order to be adopted internally.

## Would your organization be willing to provide occasional feedback during the development of an authoring solution?

Yes

## Would your organization consider contributing software development resources toward the development of an SCAP authoring solution?

Yes
 
## Capabilities

Which of the following capabilities would you be interested in seeing in a general-purpose SCAP authoring tool?

- Integration capabilities into existing tools, 
- Ability to allow different levels of authoring:
	- Policy Level: Given a path to group policy, construct the appropriate SCAP content
	- Mid Level: "Check registry key", or "check file presence"
	- Technical Level: Allow users to construct OVAL directly
- Per the first 2 bullets above, allow for the ability to abstract SCAP technical details from the author.
- Schema authoring: The ability to use the tool to create new OVAL constructs.


## Requirements

Please specify importance of the following high-level features and capabilities to your organization:

**Answer**

- Simplified SCAP content creation for authors with little-to-no SCAP knowledge: Very important | ***Somewhat important*** | Not important

- Tooling that makes SCAP experts more efficient (facilitating content re-use, ID management, change tracking, etc.): ***Very important*** | Somewhat important | Not important

- Automation-friendly tooling (APIs, code libraries, etc.) that provides a simple, stable mechanism for generating SCAP component elements (OVAL elements, XCCDF Benchmarks, etc.): ***Very important*** | Somewhat important | Not important

- Support for the latest SCAP component specification versions (OVAL, XCCDF, etc.): ***Very important*** | Somewhat important | Not important
> Yes, for new device support and various SCAP performance improvements it is important that the toll support SCAP in development (“Dev Branch” in OVAL for example) prior to actual final SCAP release

- Support for legacy SCAP component specification versions more than a few years old: Very important | ***Somewhat important*** | Not important
> Something like “flagging” deprecated content features would be very useful when importing “older” content into the tool.

- Creating individual OVAL Definitions and OVAL Definitions Files (no XCCDF Benchmark): Very important | ***Somewhat important*** | Not important

- Creating XCCDF Benchmarks using existing OVAL checks (no OVAL creation): Very important | ***Somewhat important*** | Not important

- Creating XCCDF Benchmarks and corresponding OVAL checks: ***Very important*** | Somewhat important | Not important


**Additional Requirement**
- Support for creation of SCAP-compatible Data-Stream Collections containing appropriate component structure: Very important | ***Somewhat important*** | Not important