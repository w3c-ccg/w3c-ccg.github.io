# The CCG - VCWG Maintenance Process

This describes the process for the Verifiable Credentials Working Group maintenance mode.



1. A W3C CCG VC Specification Maintenance Group will be created.
   1. The group will meet every 2 weeks to determine what maintenance changes need to be made to W3C VCWG documents.
2. The Verifiable Credentials WG documents will be updated to work with this process by:
   1. Having a git tag for the currently published version as "v1.0.0".
3. Any change to a VCWG specification MUST be done as a pull request (PR) to a maintenance branch of the specification ([https://github.com/w3c/vc-data-model/](https://github.com/w3c/vc-data-model/)).
   1. Any new PR must happen on a branch labeled using semantic versioning, such as "v1.0.x-&lt;maintenance-item>.
   1. New versions published with tag "v1.0.x" where the title of the specification is changed to "v1.0, 2nd Edition", "v1.0, 3rd Edition", etc.
      1. Specifically, updates MUST NOT be published as [specification errata](https://w3c.github.io/vc-data-model/errata.html).
   1. All PRs MUST pass an IPR check performed on the maintenance branch via github plugin before being sent to the VCWG for review (see details below).
   1. PRs SHOULD NOT make breaking changes by ensuring that any change is backwards compatible and does not remove features.
      1. PRs that make substantive technical changes (e.g., new features), typically signalled by the test suite having to change, will require a full W3C IPR release process which can take as long as six months; therefore, this sort of change should be avoided unless absolutely necessary.
4. PRs go to the VCWG for thumbs up/down approval. They need to consider both charter scope and IPR. If not approved, work goes back to CCG for further refinement.
    1. New publications as W3C Technical Report only happen for stable "v1.0.x" tags with the latest VCWG-approved proposal to publish in W3C TR-space on the main branch.
5. Regular call times for VCWG to approve PRs — at a minimum, every 3 months or when necessary (where two weeks advance notice is given).


## Potential maintenance items

Things that we may want to work on include the following, in this order:

1. Fix bug in JWT section
2. Move Subject-Holder appendix to Implementation Guide
3. VC Extensions Registry
4. RevocationList2020 NOTE (first as CCG Document? Then VCWG NOTE?)
5. Different representations NOTE? XML? CBOR?
6. Fix ZKP sections (This would be normative, need a rechartered WG?)


## NOTE: Performing IPR check via github plugin

When anyone makes a PR to the repository (i.e., a proposed change to the Model specification), an add-on to github will automatically do an IPR check.  If the submitter is an official member of the VC Working Group, the system will recognize this, and the submission will be accepted as part of the IPR disclosure mechanism in place for the Working Group participants. Otherwise, the PR will be temporarily blocked, and the submitter will be asked to make some IPR declaration (the modalities will depend on whether or not he/she represents a W3C Member organization).

The check can be shortcut (essentially, switched off) by the WG’s staff contact if the PR is non-substantive, meaning that it does not affect any normative statement (which is something the WG would determine).

To avoid complications, two good practice steps:



* The submitter should have his/her W3C account “bound” to the github account (go to [1](https://www.w3.org/users/myprofile/connectedaccounts)). It is a good idea for _everyone_ to make that connection!
* It is best if substantive PRs are only submitted by genuine WG members...
