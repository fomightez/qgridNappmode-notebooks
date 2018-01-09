# Using qgrid along with creating webapps with Binder. Also have Seaborn, VPython, and other useful dependencies

[![Binder](https://mybinder.org/badge.svg)](https://beta.mybinder.org/v2/gh/fomightez/qgrid-notebooks/master?filepath=index.ipynb)

This repository demonstrates how to use both qgrid and appmode with Binder. 

qgrid is an interactive grid for sorting, filtering, and editing DataFrames in Jupyter notebooks, and is described [here](https://github.com/quantopian/qgrid).

Appmode is similar to how Shiny apps work in R.
Using the `appmode` Jupyter plugin, a notebook's code will be run, and then only the markdown cells and
code outputs will be shown.

You can check out the `appmode` repository here: https://github.com/oschuett/appmode

----

### Post-Fork Differences
- I added appmode and my other favorite dependencies as in my appmode repo. In order to add appmode and the ones possible to the `environment.yml` and then tested. Seemed to work as appmode worked. Then I added a postBuild file to add the dependencies conda cannot handle. 


### Issues

I had tried adding ggrid to my working appmode repo but that didn't seem to work in that although I got no errors, the dataframes weren't being rendered as they were at the demo hosted [here](https://github.com/quantopian/qgrid-notebooks) and launchable via [here](https://beta.mybinder.org/v2/gh/quantopian/qgrid-notebooks/master?filepath=index.ipynb).
