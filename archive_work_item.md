# Archive a CCG work item

An example is the [DID-method-registry](https://github.com/w3c-ccg/did-method-registry)

1. Prepare to archive
  - 1a. If transferring a work item:
    - Redirect github page [as described here](https://gist.github.com/domenic/1f286d415559b56d725bee51a62c24a7)
    - Move/close issues. If multiple, can use bulk export:
      - Export with bulk issue mover: https://github.com/gavinr/github-csv-tools
      - Upload as .xlsx to new repo
    - If there are open pull requests (PRs), add a comment that you are closing it and direct to the new repo.
    - Update README.md, first line should say "This repo has moved to LINK".
    - Update the [work items list](https://github.com/w3c-ccg/community/blob/master/work_items.md). Move from "in progress" to "completed" section
    - Update website in repo settings to point to the new website
  - 1b. Else, if retiring a work item (it's not transferred anywhere)
    - Update README.md, first line should say "This repo has been archived".
    - Update the [work items list](https://github.com/w3c-ccg/community/blob/master/work_items.md). Move from "in progress" to "archived" section
2. Lastly, mark repo as archived (settings > danger zone > archive this repository)
