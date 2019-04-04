# Project Cloner

A little Python utility I made to make it a little faster to fork/clone/set remotes when beginning work on a new open source project.

Just put the clone-project file in you $PATH and make it executable (or use the GNU `install` utility).

## Dependencies
- PyYAML
- GitPython
- giturlparse.py
- PyGithub

## Usage

```
usage: clone-project [-h] repository

positional arguments:
  repository

optional arguments:
  -h, --help  show this help message and exit
```

Where `repository` is a valid Git URL.

## Functionality
The script will first report missing python dependencies, and walk you through first time configuration. You will
need to have created a Github Access Token with minimal `repo` access so that we can view repos and create forks.

The script will then perform the following actions:

1. Clone the repo to the directory you specified, by default `~/projects/{domain}/{owner}/{repo}`
1. Rename the `origin` remote to `upstream`
1. Add an `origin` remote pointing to `git@github.com:{github_user}/{repo_name}`
1. If the `origin` remote doesn't exist on github, and the `upstream` remote is also a github repository, 
   it will automatically create a Github fork of the repo under the specified {github_user}.
