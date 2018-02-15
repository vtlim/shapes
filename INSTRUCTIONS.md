# Tutorial with Caitlin
Version: 2/15/18

## Concepts
* Starting a new Github repository
* Travis tests
* Code coverage
* Documentation (not covered on 2/15/18)

## Terms
* origin = my fork
* upstream = place where I forked from

## Notes
* [Reference from Caitlin's notes](https://github.com/bannanc/shapes/blob/master/README.md)
* Github: if you get `fatal: HTTP request failed`, see [this](https://stackoverflow.com/questions/7438313/pushing-to-git-returning-error-code-403-fatal-http-request-failed)
* [pytest flags](http://pytest.readthedocs.io/en/reorganize-docs/new-docs/user/commandlineuseful.html)
* Travis CI is Travis Continuous Integration ([notes for beginners])(https://docs.travis-ci.com/user/for-beginners/)

## Procedure

1. Forked from [https://github.com/MolSSI/python_template](https://github.com/MolSSI/python_template) on Github online
2. Get the github repo onto your computer.
    * `git clone https://github.com/MolSSI/python_template.git`
3. Check out the forks you have on this project.
    * `git remote -v`
4. Add another fork.
    * `git remote add upstream https://github.com/MolSSI/python_template.git`
    * `git remote add bannanc https://github.com/bannanc/python_template.git`
5. Make a branch called tutorial on your own fork.
    * `git checkout -b tutorial`
    * `git branch -a` to see branches
6. Pull from Caitlin's master branch into my tutorial branch.
    * `git pull bannanc master`
7. Create conda environment from Caitlin's yml file
    * From zip file on [Mobley lab Slack](https://mobleylab.slack.com/files/U1AAMLE31/F9A6PMS94/github_tutorial.zip)
    * `conda env create -n tutorial -f tutorial.yml`
    * `source activate tutorial`
8. Explore the shapes project.
    * Notice python convention of having a folder called shapes in a folder called shapes.  
      The inner folder is where the meat is.
    * Can use the `setup.py` file for future projects; not recommended to write from scratch.
    * ALWAYS HAVE A LICENSE ON YOUR PROJECT else no one else is allowed to use it.  
      MIT means provided as is, and cite me if you use this.
    * `__init__.py` tells `setup.py` to give paths of where to get modules
9. Install shapes into conda environment.
    * `pip install -e .`
    * Do this in the same directory as the `setup.py` file.
    * The `-e` means you can make changes to the python code and it will be incorporated.  
      More details [here](http://codumentary.blogspot.com/2014/11/python-tip-of-year-pip-install-editable.html).
10. Looking at tests via pytest module.
    * pytest automatically runs if function has `test_` at beginning or `_test` at end
    * `approx` handles floating point differences
    * any function that you've written, try to catch different exception cases
11. Test out the tests.
    * `py.test -v -s`
    * `v` is for verbose for the breakdown of what passes
    * `s` prints out the print statements in the test functions
12. Create a new shapes repo on Github.
    * Here, not creating new README and gitignore since we already have it in the shapes material.
13. In the outer shapes directory:
    * `git init`
    * `git remote add origin https://github.com/vtlim/shapes.git`
    * `git add .gitignore LICENSE README.md setup.py`
    * `git commit -m 'add initial files'`
    * `git push origin master`
    * `git add shapes/ tests/` and commit again
14. Go to `travis-ci.org` and turn on tests for the shapes repository.
15. Copy the travis yml file to the outer shapes directory from the `python_template` directory.
    * `cp ../../python_template/.travis.yml .`
16. Open the `.travis.yml` file:
    * This is similar to JSON format.
    * When you customize this for your own project, add the python packages that your project depends on.  
      Here, it's just numpy and pytest.
    * Also not recommended to start from scratch here.
17. Go to Travis online to check out test status.
18. Add Travis badge to top of README. 
    * Click on badge on top of Travis website to get the build status image.
    * `[![Build Status](https://travis-ci.org/vtlim/shapes.svg?branch=master)](https://travis-ci.org/vtlim/shapes)`
19. Travis file already had commands for code coverage so can go to [codecov.io](codecov.io) online to check that out.
    * Have AT LEAST 80% of your code covered.
20. Add badge for this too!
    * Add this next to the Travis badge, not on a new line.
    * `[![codecov](https://codecov.io/gh/vtlim/shapes/branch/master/graph/badge.svg)](https://codecov.io/gh/vtlim/shapes)`
