
# Creating a CCG work item

Alternative: if the work item owners want to use markdown (instead of respec directly), you can use the [markdown-to-spec](https://github.com/w3c-ccg/markdown-to-spec) template. Follow the instructions on the [README.md](https://github.com/w3c-ccg/markdown-to-spec/README.md)

- Create the repo:
    - If a repo exists, ask the current owner to transfer over the repo to the CCG github org
    - Otherwise create one
- Add default files
  - Option 1: Run script in `https://github.com/w3c-ccg/create-repo`, from parent dir, using repo name from above step; then open a pull request
    - Command: `./create-repo/create.sh REPO_NAME OWNER1 OWNER2 ...`
    - Usage example: `./create-repo/create.sh functional-identity jandrieu ChristopherA`
  - Option 2: Manual
    - Create CODEOWNERS file
      - Typical sample is below. You will need to customize sample text with codeowner names.
    - Add LICENSE.md with content below
    - Add [CONTRIBUTING.md](CONTRIBUTING.md) You can use this boilerplate as is.
- Update collaborators (through github interface)
  - Settings > Manage Access
    - Chairs: Admin
    - Editors: Write
    - Contributors: View
  - Give the CODEOWNERS "maintain" access 
- Add repo topic: (through github interface)
  - `workitem` OR `registry`
  - `w3c-ccg`
- Add to [work items list](https://github.com/w3c-ccg/community/blob/master/work_items.md)

## CODEOWNERS sample
```
# These owners will be the default owners for everything in
# the repo. Unless a later match takes precedence,
# they will be requested for review when someone opens a 
# pull request.
*       @owner1 @owner2

# See CODEOWNERS syntax here: https://help.github.com/articles/about-codeowners/#codeowners-syntax
```

## LICENSE.md content
```
All Reports in this Repository are licensed by Contributors under the [W3C Software and Document
License](https://www.w3.org/Consortium/Legal/2015/copyright-software-and-document).

Contributions to Specifications are made under the
[W3C CLA](https://www.w3.org/community/about/agreements/cla/).

Contributions to Software, including sample implementations, are under the
[Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0).```
