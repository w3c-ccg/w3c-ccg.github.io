# The CCG - VCWG Maintenance Process

This describes the process for the Verifiable Credentials Working Group maintenance mode. 

## Process Overview for VC Data Model Pull Requests

1. For now, we will focus only on merging new errata PRs into the VC Data Model Repository,
   but encourage activity related to new features.
2. Once a PR is opened, chairs and editors make judgement call on whether
   changes are substantive or editorial.
   <dl>
     <dt>Editorial</dt>
     <dd>Mark with "editorial" tag, merge into branch "v1.1"</dd>
     <dt>Substantive</dt>
     <dd>Mark with "v2.0" tag. Substantial changes are merged into separate branch "v2.0" which will be addressed when a new WG is formed. New Features stay around as open PRs.</dd>
   </dl>
3. W3C CCG is notified of PRs that will be merged in the next 14 days if there
   are no objections. A weekly issue and digest list is currently sent to the CCG mailing list to handle this
4. When it's determined a new recommendation should go out, the W3C Verifiable
   Credentials Working Group members meet, review all the PRs that have been
   merged, and make a formal recommendation if agreement is reached.

## Potential maintenance items

Things that we may want to work on (in this order):



1. Fix bug in JWT section
2. Move Subject-Holder appendix to Implementation Guide
3. VC Extensions Registry
4. RevocationList2020 NOTE (first as CCG Document? Then VCWG NOTE?)
5. Different representations NOTE? XML? CBOR?
6. Fix ZKP sections (This would be normative, need a rechartered WG?)


## NOTE: Performing IPR check via github plugin

If anyone makes a PR to the repository (ie, a proposed change on the Model specification) then an add-on to github will automatically do an IPR check.  If the submitter is an official member of the VC Working Group, then the system will recognize this and the submission will be accepted as part of the IPR disclosure mechanism in place for the Working Group participants. Otherwise, the PR will be temporarily blocked and the submitter will be asked to make some IPR declaration (the modalities will depend on whether he/she represents a W3C Member organization or not). 

The check can be shortcut (essentially switched off) by the WG’s staff contact if the PR is non-substantive, meaning that it does not affect any normative statement (which is something the WG would determine).

To avoid complications, two good practice steps:



*   The submitter should have his/her W3C account “bound” to the github account (go to [1], and look for ‘connected accounts’ on the left column). It is a good idea for everyone to just make that connection once and for all
*   The best is if substantive PRs are submitted by genuine WG members...
