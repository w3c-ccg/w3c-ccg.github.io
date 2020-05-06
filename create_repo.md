
# Creating a repo

- Create the repo:
    - If a repo exists, ask the current owner to transfer over the repo to the CCG github org
    - Otherwise create one
- Add default files
  - Option 1: Run script in `https://github.com/w3c-ccg/create-repo`, from parent dir, using repo name from above step
    - Command: `./create-repo/create.sh REPO_NAME BRANCH OWNER1 OWNER2 ...`
    - Usage example: `./create-repo/create.sh functional-identity gh-pages jandrieu ChristopherA`
  - Option 2: Manual
    - Create gh-pages branch if preferred (command line)
      - https://www.gep13.co.uk/blog/how-to-create-gh-pages-branch
    - Create CODEOWNERS file
      - Typical sample is below
    - Add LICENSE.md with content below
    - Add [CONTRIBUTING.md](CONTRIBUTING.md)
- Update collaborators (through github interface)
  - Teams
    - Chairs: Admin
    - Editors: Write
  - Collaborators: anyone not in the group who needs access
- Add repo topic: (through github interface)
  - `workitem` OR `registry`
  - `w3c-ccg`


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
All documents in this Repository are licensed by contributors under the [W3C Software and Document License](http://www.w3.org/Consortium/Legal/copyright-software).
```
