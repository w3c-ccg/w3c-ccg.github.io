
# Creating a repo

- Create the repo 
- Create gh-pages branch (command line)
  - https://www.gep13.co.uk/blog/how-to-create-gh-pages-branch
- Switch default branch:
  - github repo > settings > branches
- Create CODEOWNERS file
  - Typical sample is below
- Update collaborators
  - Teams
    - Chairs: Admin
		- Editors: Write
  - Collaborators: anyone not in the group who needs access
- Add repo topic: 
  - `workitem` OR `registry`
  - `w3c-ccg`
- TODO: deal with IP issues


CODEOWNERS sample
```
# These owners will be the default owners for everything in
# the repo. Unless a later match takes precedence,
# they will be requested for review when someone opens a 
# pull request.
*       @owner1 @owner2

# See CODEOWNERS syntax here: https://help.github.com/articles/about-codeowners/#codeowners-syntax
```
