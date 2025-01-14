# Odious ADO

Goodbye microsoft thanks for not a good project management tool!

Official documentation: [odious-ado]()

Please note: This is not complete but is kind of in the ballpark.

<!-- start elevator-pitch -->

The project has three components an API, SDK, and CLI. All of which are still a work in progress and
will need to be continually improved to meeting the requirements of the original spec.

<!-- end elevator-pitch -->

<!-- start quickstart -->

## Working On the Code Base (Local Development Environment)

There are pre-commit hook that should be setup and followed. However, at this time they can just be bypassed.

### Installation

A few prerequisite dependencies:
* [just](https://github.com/casey/just) a makefile replacement in rust.
* [pyenv](https://github.com/pyenv/pyenv#installation) python version manager.

After installing [just](https://github.com/casey/just) and [pyenv](https://github.com/pyenv/pyenv#installation).

---
### Use one of the following methods

* Follow the steps below. Both tools must be in your shell path.

```shell
pyenv install 3.11.3
# pyenv will change the local python version based on the .python-version file in root.
just dev install
# After running the just command running the following to verify configuration.
poetry run odious-ado --help
```

* Follow these steps to use pyenv to manage python virtual envs.

```shell
# install python
pyenv install 3.11.3

# create a python virtual env
pyenv virtualenv 3.11.3 odious-ado

# activate that python env for usage
pyenv activate odious-ado

# create a new local wheel to be used for the project 
poetry install

# pyenv will change the local python version based on the .python-version file in root.
just dev

# verify the python template install
python-template version
``` 
### stupid hacks

update pyproject.toml to add these packages correctly - abanna
```bash 
$ pip install github3.py 
 
$ pip install pytz
```

This ADO SDK is a bit wack regarding the amount of boilerplate code required to do much of anything...
The docs are somewhat lack luster. With that said This project can likely have an MVP built out in a
few days. 

A few unknowns.  How does one release GitHub action... Would like to test this early in the hackation to 
allow for a smooth ending and time to focus on a nice video presentation.

Main things that we need to do.  Get data from workflow action yaml. Use that data to map fields and labels to 
ado fields etc. 

We need the issues to be assigned to Github project.

The labels on that github project need to include the ADO_PROJECT_NAME.

assignees might be somewhat painful if there isn't a way to map github users to ado users. (not really required atm)

update ADO with issue title comments and any other requirements.

iterations might be a bit of a stretch for mvp - though probably a requirement for real life use.

swimlane mapping -> Github project Status has to be mapped to ADO swim lanes.

The lanes will have to have a mapping or match otherwise we will not be able to track the work.

points to estimates update prs in ado comments.

repo and reviews can be updated. 



when pr is created link pr in newly created issue and also ADO. Or if any existing issue has a pr create a new ado ticket with pr link included.
- add ado link to github issue.

anytime a an issue or pr get create up date ado ticket wit comments and other data. link to pr 

 - if possible we can attempt to update github issues from ado events.

video demo --- patrick will spear head this. cool 90s music --- add some nick cage 


```yaml

action:
  mappings:
    mymappings:
       thing: thing2

```

```yaml
  action: odious_ado@v1
  with:
       mappings:
        thing: thing2
    title: Monthly issue metrics report
     token: ${{ secrets.GITHUB_TOKEN }}
        content-filepath: ./issue_metrics.md
        assignees: <YOUR_GITHUB_HANDLE_HERE>
```

```yaml
lanes:
  NoStatus: Proposed
  Blocked: things
  New: New
  Backlog: Backlog
  Ready: Ready
  InProgress: InProgress
  InReview: CodeReview
  Done: Done
```

Also, thing to consider is if we want to update github issues based on what has been updated or added to ADO?

This might also be some additional fun stuff to automate with PR's and other such things.


