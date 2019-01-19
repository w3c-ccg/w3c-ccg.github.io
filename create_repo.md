
# Creating a repo

- Create the repo 
- Create gh-pages branch (command line)
  - https://www.gep13.co.uk/blog/how-to-create-gh-pages-branch
- Switch default branch:
  - github repo > settings > branches
- Update collaborators
  - Teams
    - Chairs: Admin
    - Editors: Write
  - Collaborators: anyone not in the group who needs access
- Add repo topic: 
  - `workitem` OR `registry`
  - `w3c-ccg`
- Create CODEOWNERS file
  - Typical sample is below
- Add LICENSE.md with content below
- Add [CONTRIBUTING.md](CONTRIBUTING.md)


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
