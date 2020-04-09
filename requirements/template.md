# SCAP Content Authoring Use Case Questions

Organization: TODO

##	What type of SCAP content (vulnerability, specific compliance programs, OVAL, XCCDF, etc.) are you authoring and for what operating systems?

**Answer**

##	Approximately how many OVAL/XCCDF authors are there in your organization?

**Answer**

##	What specific areas of content authoring are the most difficult for your authors?

Examples:

- Getting content to run on multiple OVAL engines.
- It is difficult to know what OVAL schemas to use.
- Writing XML is difficult.

**Answer**

## Would some measure of automation assist in the authoring of the content that you are developing?

**Answer**

## Do you perform any customizations to existing SCAP content or 3rd party SCAP content?

**Answer**

## How do you store the content you create? 

Examples:

- Directories in a file system.
- Database.
- Content is loaded into scanning tools.
- GitHub.
- Other version control systems.

**Answer**


## From which external SCAP sources do you collect content?

**Answer**


## What tools do you use to create SCAP content? Are you satisfied with your current tools?

**Answer**


##	How willing would you be to change the tools that you are currently using if a general-purpose SCAP authoring solution was to be developed?

**Answer**

##	Are there any challenges your organization would face when adopting a new SCAP authoring solution?

Examples:

- Programming language lock-in.
- Ongoing internal tool development.
- Browser-based versus compiled code.

**Answer**

## Would your organization be willing to provide occasional feedback during the development of an authoring solution?

**Answer**

## Would your organization consider contributing software development resources toward the development of an SCAP authoring solution?

**Answer**
 
## Capabilities

Which of the following capabilities would you be interested in seeing in a general-purpose SCAP authoring tool?

1. The ability to specify common actions (e.g., "check registry key," "check file presence") and have the tool generate content without forcing the author to understand the underlying OVAL/XCCDF language structures. 
2. Support for version/revision control in your tools for content.
3. The ability to define "macros" and "libraries" that can be saved to be used in future content.
4. Difference tracking between content sources.

**Answer**


## Requirements

Please specify importance of the following high-level features and capabilities to your organization:

**Answer**

- Simplified SCAP content creation for authors with little-to-no SCAP knowledge: Very important | Somewhat important | Not important

- Tooling that makes SCAP experts more efficient (facilitating content re-use, ID management, change tracking, etc.): Very important | Somewhat important | Not important

- Automation-friendly tooling (APIs, code libraries, etc.) that provides a simple, stable mechanism for generating SCAP component elements (OVAL elements, XCCDF Benchmarks, etc.): Very important | Somewhat important | Not important

- Support for the latest SCAP component specification versions (OVAL, XCCDF, etc.): Very important | Somewhat important | Not important

- Support for legacy SCAP component specification versions more than a few years old: Very important | Somewhat important | Not important

- Creating individual OVAL Definitions and OVAL Definitions Files (no XCCDF Benchmark): Very important | Somewhat important | Not important

- Creating XCCDF Benchmarks using existing OVAL checks (no OVAL creation): Very important | Somewhat important | Not important

- Creating XCCDF Benchmarks and corresponding OVAL checks: Very important | Somewhat important | Not important


