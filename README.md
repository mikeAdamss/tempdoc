## Installing Python3  and Pipenv on a Mac

The data transformation part of the COGS project uses python3.
DON'T attempt to use the basic python installation that comes with your MAC. It's python2 and is used to power the desktop UI (a few of the libraries are protected, this can result in unexpected and hard to trace issues).

This guide will show the most minimalist steps required to get up and running.

* install brew via `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
* install python3 with `brew brew install python@3.7`
* find out if your mac is defaulting to bash (older macos) or zshell (newer macos) via `echo ${SHELL}` (if you're unsure about this step - ask).
* If its bash:  run `export PATH="/usr/local/opt/python@3.7/bin:$PATH" >> ~/.bash_profile` to ensure it's available on your system $PATH.
* If its zshell:  run cat `PATH="/usr/local/opt/python@3.7/bin:$PATH" >> .zshenv` to ensure it's available on your system $PATH.
* `sudo pip3 install pipenv==2018.11.26`

Note 1 - you must  use sudo for the last step, otherwise pipenv may not be set to your global $PATH (this can cause you all kinds of issues).Note 2 - Just remember to differentiate this install from the macbooks default python2 when you use it (i.e by using pip3 and python3).
