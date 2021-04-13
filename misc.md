This notebook was prepared by [Donne Martin](http://donnemartin.com). Source and license info is on [GitHub](https://github.com/donnemartin/data-science-ipython-notebooks).

# Misc Commands

* Anaconda
* IPython Notebook
* Git
* Ruby
* Jekyll
* Pelican
* Django

<h2 id="anaconda">Anaconda</h2>

[Anaconda](https://store.continuum.io/cshop/anaconda/) is a scientific python distribution containing Python, NumPy, SciPy, Pandas, IPython, Matplotlib, Numba, Blaze, Bokeh, and other great Python data analysis tools.


```python
# See Anaconda installed packages
!conda list

# List environments
!conda info -e

# Create Python 3 environment
!conda create -n py3k python=3 anaconda

# Activate Python 3 environment
!source activate py3k

# Deactivate Python 3 environment
!source deactivate

# Update Anaconda
!conda update conda

# Update a package with Anaconda
!conda update ipython

# Update a package
!conda update scipy

# Update all packages
!conda update all

# Install specific version of a package
!conda install scipy=0.12.0

# Cleanup: Conda can accumulate a lot of disk space
# because it doesn’t remove old unused packages
!conda clean -p

# Cleanup tarballs which are kept for caching purposes
!conda clean -t
```

<h2 id="ipython-notebook">IPython Notebook</h2>

[IPython Notebook](http://ipython.org/notebook.html) is a "web-based interactive computational environment where you can combine code execution, text, mathematics, plots and rich media into a single document."


```python
# Start IPython Notebook
ipython notebook

# Start IPython Notebook with built-in mode to work cleanly 
# with matplotlib figures
ipython notebook --pylab inline

# Start IPython Notebook with a profile
ipython notebook --profile=dark-bg

# Load the contents of a file
%load dir/file.py

# Time execution of a Python statement or expression
%timeit
%%time

# Activate the interactive debugger
%debug

# Write the contents of the cell to a file
%writefile

# Run a cell via a shell command
%%script

# Run cells with bash in a subprocess
# This is a shortcut for %%script bash
%%bash

# Run cells with python2 in a subprocess
%%python2

# Run cells with python3 in a subprocess
%%python3

# Convert a notebook to a basic HTML file 
!ipython nbconvert --to html --template basic file.ipynb 
```

| Command   | Description                              |
|-----------|------------------------------------------|
| ?         | Intro and overview of IPython's features |
| %quickref | Quick reference                          |
| help      | Python help                              |
| object?   | Object details, also use object??        |

Apply css styling based on a css file:


```python
from IPython.core.display import HTML

def css_styling():
    styles = open("styles/custom.css", "r").read()
    return HTML(styles)
css_styling()
```

<h2 id="git">Git</h2>

[Git](http://git-scm.com/) is a distributed revision control system.


```python
# Configure git
!git config --global user.name 'First Last'
!git config --global user.email 'name@domain.com'
!git init

# View status and log
!git status
!git log

# Add or remove from staging area
!git add [target]
!git reset [target file or commit]
!git reset --hard origin/master

# Automatically stage tracked files, 
# including deleting the previously tracked files
# Does not add untracked files
!git add -u

# Delete files and stage them
!git rm [target]

# Commit
!git commit -m “Add commit message here”

# Add new origin
!git remote add origin https://github.com/donnemartin/ipython-data-notebooks.git

# Set to new origin
!git remote set-url origin https://github.com/donnemartin/pydatasnippets.git
    
# Push to master, -u saves config so you can just do "git push" afterwards
!git push -u origin master
!git push

# Diff files
!git diff HEAD
!git diff --staged
!git diff --cached

# Show log message of commit and diff
!git show $COMMIT

# Undo a file that has not been added
!git checkout — [target]

# Revert a commit
!git revert

# Undo a push and leave local repo intact
!git push -f origin HEAD^:master

# Undo commit but leave files and index
!git reset --soft HEAD~1

# Amend commit message of most recent change
!git commit --amend
!git push --force [branch]

# Take the dirty state of your working directory
# and save it on a stack of unfinished changes
!git stash

# Get list of stashes
!git stash list

# Apply the top stash, re-modifying the 
# uncommitted files when the stash was saved
!git stash apply

# Apply a stash at the specified index
!git stash apply stash@{1}

# Create a branch
!git branch [branch]

# Check branches
!git branch

# Switch branches
!git checkout [branch]

# Merge branch to master
!git merge [branch]

# Delete branch
!git branch -d [branch]

# Clone
!git clone git@github.com:repo folder-name
!git clone https://donnemartin@bitbucket.org/donnemartin/tutorial.git
    
# Update a local repository with changes from a remote repository
# (pull down from master)
!git pull origin master

# Configuring a remote for a fork
!git remote add upstream [target]

# Set remote upstream
git branch --set-upstream-to origin/branch

# Check remotes
!git remote -v

# Syncing a fork
!git fetch upstream
!git checkout master
!git merge upstream/master

# Create a file containing a patch
# git format-patch are like normal patch files, but they also carry information 
# about the git commit that created the patch: the author, the date, and the 
# commit log message are all there at the top of the patch.
!git format-patch origin/master

# Clean up .git folder:
!git repack -a -d --depth=250 --window=250

# GitHub tutorial:
http://try.github.io/levels/1/challenges/9

# BitBucket Setup
!cd /path/to/my/repo
!git init
!git remote add origin https://donnemartin@bitbucket.org/donnemartin/repo.git
!git push -u origin --all # pushes up the repo and its refs for the first time
!git push -u origin --tags # pushes up any tags

# Open Hatch missions
!git clone https://openhatch.org/git-mission-data/git/dmartin git_missions
```

<h2 id="ruby">Ruby</h2>

[Ruby](https://www.ruby-lang.org/en/) is used to interact with the AWS command line and for Jekyll, a blog framework that can be hosted on GitHub Pages.


```python
# Update Ruby
!rvm get stable

# Reload Ruby (or open a new terminal)
!rvm reload

# List all known RVM installable rubies
!rvm list known

# List all installed Ruby versions
!rvm list

# Install a specific Ruby version
!rvm install 2.1.5

# Set Ruby version
!rvm --default ruby-1.8.7
!rvm --default ruby-2.1.5

# Check Ruby version
!ruby -v
```

<h2 id="jekyll">Jekyll</h2>

[Jekyll](http://jekyllrb.com/) is a blog framework that can be hosted on GitHub Pages.

In addition to donnemartin.com, I’ve started to build up its mirror site donnemartin.github.io to try out Jekyll. So far I love that I can use my existing developer tools to generate content (SublimeText, Terminal, and GitHub).

Here are other features I like about Jekyll:

* Converts Markdown to produce fast, static pages
* Simple to get started, no backend or manual updates
* Hosted on GitHub Pages
* Open source on GitHub

Many Jekyll themes require a Ruby version of 2 and above.  However, the AWS CLI requires Ruby 1.8.7.  Run the proper version of Ruby for Jekyll:


```python
!rvm --default ruby-2.1.5
```

Build and run the localy Jekyll server:


```python
# => The current folder will be generated into ./_site
!bundle exec jekyll build

# => A development server will run at http://localhost:4000/
# Auto-regeneration: enabled. Use `--no-watch` to disable.
!bundle exec jekyll serve
```

<h2 id="pelican">Pelican</h2>

I've switched my personal website [donnemartin.com](http://donnemartin.com/) to run off Pelican, a python-based alternative to Jekyll.  Previous iterations ran off Wordpress and Jekyll.

Setup [reference](http://nafiulis.me/making-a-static-blog-with-pelican.html).


```python
# Install
!pip install pelican
!pip install markdown
!pip install ghp-import

# Quick retup
!pelican-quickstart

# Run server
!make devserver

# Stop server
!make stopserver

# Run ghp-import on output folder
# Review https://pypi.python.org/pypi/ghp-import
# There's a "Big Fat Warning" section
!ghp-import output

# Update gh-pages (if using a project page)
!git push origin gh-pages

# Update gh-pages (if using a user or org page)
!git merge gh-pages master
```

## Django

[Django](https://www.djangoproject.com) is a high-level Python Web framework that encourages rapid development and clean, pragmatic design.  It can be useful to share reports/analyses and for blogging. Lighter-weight alternatives include [Pyramid](https://github.com/Pylons/pyramid), [Flask](https://github.com/mitsuhiko/flask), [Tornado](https://github.com/tornadoweb/tornado), and [Bottle](https://github.com/bottlepy/bottle).


```python
# Check version of Django
!python -c "import django; print(django.get_version())"

# Create and setup a project
!django-admin startproject mysite

# Sync db
!python manage.py syncdb

# The migrate command looks at the INSTALLED_APPS setting and 
# creates any necessary database tables according to the database 
# settings in your mysite/settings.py file and the database 
# migrations shipped with the app
!python manage.py migrate

# Run the dev server
!python manage.py runserver
1python manage.py runserver 8080
!python manage.py runserver 0.0.0.0:8000

# Create app
!python manage.py startapp [app_label]

# Run tests
python manage.py test [app_label]

# Tell Django that you’ve made some changes to your models 
# and that you’d like the changes to be stored as a migration.
!python manage.py makemigrations [app_label]

# Take migration names and returns their SQL
!python manage.py sqlmigrate [app_label] [migration_number]

# Checks for any problems in your project without making 
# migrations or touching the database.
!python manage.py check

# Create a user who can login to the admin site
!python manage.py createsuperuser

# Locate Django source files
!python -c "
import sys
sys.path = sys.path[1:]
import django
print(django.__path__)"
```
