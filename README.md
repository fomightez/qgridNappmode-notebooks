# Using qgrid along with creating webapps with Binder. Also have Seaborn, VPython, and other useful dependencies

[![Binder](https://mybinder.org/badge.svg)](https://beta.mybinder.org/v2/gh/fomightez/qgrid-notebooks/master?filepath=index.ipynb)

This repository demonstrates how to use both qgrid and appmode with Binder. 

qgrid is an interactive grid for sorting, filtering, and editing DataFrames in Jupyter notebooks, and is described [here](https://github.com/quantopian/qgrid). This is my fork demonstrating use in Binder and came from [here](https://github.com/quantopian/qgrid-notebooks).

Appmode is similar to how Shiny apps work in R.
Using the `appmode` Jupyter plugin, a notebook's code will be run, and then only the markdown cells and
code outputs will be shown.

You can check out the `appmode` repository here: https://github.com/oschuett/appmode

----

### Post-Fork Differences
- After forking the the base `qgrid-notebooks` example, I added appmode and my other favorite dependencies as in [my appmode repo](https://github.com/fomightez/appmode). In order to add appmode and the ones possible to the `environment.yml` and then tested. Seemed to work as appmode worked. Finally to finish adding those dependences I like, at first I tried adding a `postBuild` file with exectuable permissions (see below) to add the dependencies conda cannot handle, but that didn't work for some reason. While researching that I found a better way as described under `Issues`. 


### Issues

- I had tried adding qgrid to my working appmode repo but that didn't seem to work. I didn't see any error reports, but the dataframes weren't being rendered as they were at the demo hosted [here](https://github.com/quantopian/qgrid-notebooks) and launchable via [here](https://beta.mybinder.org/v2/gh/quantopian/qgrid-notebooks/master?filepath=index.ipynb).

- I hadn't caught before now that `postBuild` files need to be executable. However, just adding that within my fork using the github site using web interface was causing the `postBuild` file to not be executable according to error in log file and it was referring me to http://repo2docker.readthedocs.io/en/latest/samples.html#system-post-build-scripts . Turns out I don't think files you make on github site using web interface can be set to be exectuable (or it least I couldn't fugure it out). My solution was to clone the repo, add the empty `postBuild` file with `touch`, set the permission accoring to [here](http://repo2docker.readthedocs.io/en/latest/samples.html#system-post-build-scripts), commit, and push back to the remote master. While that woked to change the permissions and that error disappeared, I got another one about not being able to run the code in the `postBuild` file that was copied exactly from the appmode repo. While looking into it, I saw that I could I could actually add the items that conda doesn't handle but pip does to the `environment.yml` using the solution at http://repo2docker.readthedocs.io/en/latest/samples.html#conda-mixed-requirements.


- appmode breaks the use of the technique described by harshil's answer [here](http://stackoverflow.com/questions/27934885/how-to-hide-code-from-cells-in-ipython-notebook-visualized-with-nbviewer) for hiding all code cells with a toggle button.
