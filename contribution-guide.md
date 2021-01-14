# Contribution Guide

This document aims to serve as a how-to that provides step by
step instructions on the set up, develop, and submission of updated
documentation for this project using [MkDocs](https://www.mkdocs.org/).
Here is a high level overview of the process:

- fork the project
- clone to your local machine
- setup local environment with docker
- use the local container to update documentation

### Install Requirements

This section assumes that you are using macOS. Use the [brew](https://brew.sh/)
package manager where noted below (and generally whenever possible).  

1. Install Git: $ `brew install git`
  - instructions for installing brew can be found [here](https://brew.sh/)

2. Install Docker
    - instructions [here](https://docs.docker.com/docker-for-mac/install/)
    - ensure docker is running with $ `docker -v`

3. Install Docker Compose
  $ `brew install docker-compose`

4. Python Environment Setup: unless you're a python master and already 
know what you're doing, we _highly recommend_ using `pyenv` to manage your local environment
    - install [pyenv](https://github.com/pyenv/pyenv/#installation) on your system
    - install [build dependencies](https://github.com/pyenv/pyenv/wiki#suggested-build-environment)
    - install your preferred version of python. ex: `pyenv install -v 3.8.6`
    - set this new version as active for your user: `pyenv global 3.8.6`
    - this can be confirmed by running: `pyenv versions`
    - install mkdocs and addons with your new clean python env: `pip3 install -r requirements.txt`

### Git the Things

1. Clone the repo locally by copy / pasting the full command by clicking the "Clone" in the top right corner of the web UI:  
  $ `# example command:  git clone <CLONE_URL>`

2. Change directory into the project folder:
  $ `cd thremulation-station`

3. Create an new branch (alternate timeline) for later pull request / merging operations:
  $ `git branch <BRANCH_NAME>`

4. Jump into your new personal branch:
  $ `git checkout <BRANCH_NAME>`

### Content Development

From the root level of the repo (where `mkdocs.yml` file resides) use docker-compose
to start the local server:

$ `docker-compose up`

This will cause docker-compose to capture your prompt as it is running as a forground service.
Use `ctrl + c` to stop this _foreground_ process. If you don't want to lose you current prompt, start the container as a _background_ service:

$ `docker-compose up -d`

> The -d specifies detached mode. Run `docker-compose stop` when you're ready to kill the running server.

Browse to http://localhost:8000 in order to preview changes. Content will
refresh automatically as files are edited and **saved**.

#### Building Web Content

After you've got things looking good in your local environment it's time to use
MkDocs to build the static web files (html, css, etc.) that will be placed on
some kind of hosting solution.

1. Stop the local server by running `docker-compose stop`

2. Use the mkdocs build option to generate the static files:
  $ `docker-compose run kit-docs build`

3. The full rendered site will then be output into the site/ directory.  

<!-- 3. Use the mkdocs deploy option to send the previously built static files to :
  $ `mkdocs gh-deploy` -->

#### Submitting Changes

After the above workflow is complete, it's time to submit your work for
approval:

1. With all your work committed, push your changes up to your project fork:
  $ `git push`

2. Use the Github graphical interface to submit an official Pull Request to
merge in all your changes.  
