# [Neutrino Group Docs](https://neutrino-cern.github.io/)

This is the documentation of the CERN Neutrino Group. It contains useful information for newcomers and also points them to other useful resources. 

## How to add new articles:
Clone this repository or use the GitHub online editor directly. To do this, you must have the necessary permissions (i.e. you must be added as a collaborator in the repository- send a message in the Slack channel). 

Navigate to the `docs` directory. It consists of folders and markdown `.md` files. Each markdown file corresponds to a page on the website. A folder consisting of markdown files creates a dropdown menu
with the folder name as the parent tab of the menu.

The [ABPComputing docs](https://abpcomputing.web.cern.ch/) serves as an example of what our wiki should look like. 

There is a great [guide](https://squidfunk.github.io/mkdocs-material/reference/) in the official `mkdocs-material` documentation on how to write Markdown files for this framework.

## Test locally 
To test that your changes are displayed correctly you can install [`mkdocs-material`](https://squidfunk.github.io/mkdocs-material/getting-started/): 
```
pip install mkdocs-material
```

Then you can test locally by running:
```
mkdocs serve
```
