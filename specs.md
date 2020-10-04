
# Creating Specs/Reports for W3C CCG Work Items

This page provides tips for creating specs or reports for your CCG work item. The W3C has a small set of requirements for [how community groups publish their reports](https://www.w3.org/community/reports/reqs/), and while these don't require use of the toolsets below, it will save you a lot of time to use one of these methods.

## tl;dr Guidance

When to use each type of tool

- Respec
   - For more technical or advanced specifications
   - If close change tracking is critical
- Automatic conversion from markdown
   - For example, by using the bikeshed tool and github commits
   - Recommended other community notes, commentary, and earlier stages of community specifications.
   - Note that you can switch to direct use of respec over time
- Other tools supporting conversion from doc formats
   - Largely untested and not recommended. Use at your own peril.
   
For details about this guidance, see [Overview of Standard Formats and Tools](#overview-of-standard-formats-and-tools)

## Get started

### Respec 
[Tutorial Video](https://youtu.be/0eQXU6Z-A6Q)

There are four primary parts to the video:
1. Tutorial on setting up a new github repository for ccg work (about 10 minutes)
2. Setting up a new ReSpec-enabled document (~ 10 minutes)
3. Tutorial on the basics of github branch-edit-commit-publish-pull_request cycle (~ 15 minutes)
4. Q&A (~15 minutes)

There is a time index at the beginning of the video

### Automatic Conversion from Markdown

If you choose this route, we strongly recommend using github commits to automatically convert the markdown to html. You can also use the toolset on your local machine to preview the conversion, but the on-commit action makes it easier for the broadest set of contributors.

There are several ways to accomplish this, but one tested method is using the bikeshed tool as a github commit action, which converts the bikeshed/markdown file (extension is .bs) to html. The [vc-ed-models](https://w3c-ccg.github.io/vc-ed-models/) work item demonstrates how to do this.

Note the following:
- See the [vc-ed-models repo](https://github.com/w3c-ccg/vc-ed-models)
- The "source" file is index.bs (in the main branch)
- The [github action](https://github.com/w3c-ccg/vc-ed-models/blob/main/.github/workflows/publish.yml) converts that file to index.html and pushes it to the gh-pages branch

You can also run bikeshed on your local machine to preview the conversion. [See instructions for running bikeshed locally](https://w3c-ccg.github.io/bikeshed_instructions.html).

### Gdoc 2 Respec tool (Beta)
- [Description from mailing list](https://lists.w3.org/Archives/Public/spec-prod/2018JulSep/0003.html)
- [Sandbox demo](credweb.org/signals)


## Overview of Standard Formats and Tools

At the core, [respec](https://github.com/w3c/respec/wiki) is the most widely used tool for generating W3C specs/reports with consistent structure (and look and feel). Working with respec directly involves modifying HTML documents, which some CCG members find difficult and tedious. For that reason, there are other tools to help with either the initial creation (for example, converting from google docs), or ongoing conversion (from markdown files). This describes the options, how to pick one, and instructions for getting started with each.

| Tool Type | Required knowledge | Advantages            | Disadvantages | 
|-----------|--------------------|-----------------------|---------------|
| Respec    | HTML               | Close change tracking | May be difficult for non-technical users |
| Ongoing conversion from Markdown | Markdown | Ease of use   | Moderate change tracking  |
| Conversion from doc | --        | Initial ease of use   | Output more difficult to understand; not recommended for use with ongoing conversions | 
   
### Detailed Guidance
Note that a big distinguishing characteristic is the ability to perform change tracking on the generated (html) document. This is essential for very detailed and/or technical specs with a lot of changes (for example the VC and DID specs) -- both for contributor tracking and for compliance with patent licensing commitments.

Ongoing conversion from markdown may be a sweetspot for either less technical reports or ones that are not moving to a working group (for example, community group notes and other reports). With github commit actions, it's possible to run conversion tools on commit, so that all you have to worry about is editing markdown files. Change tracking on the markdown file is easy, but may be a little more difficult on the .html file. At the same time, it's possible to use such conversion tools for a while and switch to using respec directly as a work item gets more mature.

The last category, involving use of tools that convert from .doc formats to .html are appealing but largely experimental. For that reason, this path is largely untested.
