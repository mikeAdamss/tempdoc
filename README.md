
## Installing Python3  and Pipenv on a Mac

The data transformation part of the COGS project uses python3.
DON'T attempt to use the basic python installation that comes with your MAC. It's python2 and is used to power the desktop UI (a few of the libraries are protected, this can result in unexpected and hard to trace issues).

This guide will show the most minimalist steps required to get up and running.
* install brew via `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
* install python3 with `brew brew install python3@3.7`
* then run `export PATH="/usr/local/opt/python@3.7/bin:$PATH" >> ~/.bash_profile` to ensure it's available on your system $PATH.
* then `sudo pip3 install pipenv==2018.11.26`

Note 1 - you must  use sudo for the last step, otherwise pipenv may not be set to your global $PATH (this can cause you all kinds of issues).
Note 2 - Just remember to differentiate this install from the macbooks default python2 when you use it (i.e by using pip3 and python3).

## Create a Virtual Environment with Pipenv

All transformation tasks in production run on the following docker container: https://github.com/GSS-Cogs/databaker-docker. The best way to manage your python dependencies is to create a virtual environment from this container (i.e always be in sync with production).

From the command line clone (copy, sort of) the container repo via git clone https://github.com/GSS-Cogs/databaker-docker

Navigate to this directory in your terminal (i.e `cd databaker-docker`) then do `pipenv install` to create a virtual environment that matches the one in the container (note - this will take a while).

Activate that environment via `pipenv shell` - you'll know it's succeeded as" (databaker-docker)" will appear before you command prompt.

## Activation and Updating Dependencies

To activate without the time consuming install (you only need to install when the platform is updated) just do the last parts of the above - i.e navigate to your cloned databaker-docker repo and run pipenv shell (it's easiest to just think the virtual env "lives" in that directory).
To update and "re-install/update" your dependencies when the production container has changed:
navigate to your /databaker-docker directory.
* run `git stash` - this removes any changes to the repo since last your synced (so you can't get merge conflicts etc)
* run `git pull` - to get the latest changes
* run `pipenv install` - re-install your virtual environment
* run `pipenv shell` - to activate your newly installed/updated virtual env.`
