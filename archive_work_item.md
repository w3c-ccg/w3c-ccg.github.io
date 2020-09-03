# Archive a CCG work item

An example is the [DID-method-registry](https://github.com/w3c-ccg/did-method-registry)

First, prepare to archive. There are 2 different paths depending on whether the work item is being transferred somewhere (1a) or being retired (1b)

(1a) If transferring a work item:

1. Redirect github page [as described here](https://gist.github.com/domenic/1f286d415559b56d725bee51a62c24a7)
2. Move/close issues. If multiple, can use bulk export:
3. Export with bulk issue mover: https://github.com/gavinr/github-csv-tools
    - Upload as .xlsx to new repo
4. If there are open pull requests (PRs), add a comment that you are closing it and direct to the new repo.
5. Update README.md, first line should say "This repo has moved to LINK".
6. Update the [work items list](https://github.com/w3c-ccg/community/blob/master/work_items.md). Move from "in progress" to "completed" section
7. Update website in repo settings to point to the new website
    
(1b) else, if you're retiring a work item (it's not transferred anywhere)
1. Update README.md, first line should say "This repo has been archived".
2. Update the [work items list](https://github.com/w3c-ccg/community/blob/master/work_items.md). Move from "in progress" to "archived" section
    
    
(2) Archive the repo

Lastly, mark the repo as archived (settings > danger zone > archive this repository)
