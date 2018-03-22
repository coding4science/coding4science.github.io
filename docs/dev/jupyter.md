#

For a live view of most of this presentation see:
[https://mybinder.org/v2/gh/raphbacher/presentation-jupyter-08-03-2018/master](https://mybinder.org/v2/gh/raphbacher/presentation-jupyter-08-03-2018/master)

## A bit of history

At the beginning :

- 2001 : IPython (F. Perez), a REPL (Read–Eval–Print Loop) client-server
- 2011 : IPython notebook : app web for documents mixing code, equations, images and text

Key concept : a client-server protocol
<div style="margin: 0 auto;width:20%">
![](images/ipy_kernel_and_terminal.png)
</div>

## Jupyter Now

- Jupyter Notebook : heir to the IPython notebook (~2015)
- JupyterHub : a multi-user version for classes, workshops etc...
- Jupyterlab : a web IDE 
- Kernels for more than 40 languages : Python, R, Julia, C++ (!) ...
- \> 6M users (2017)
- \> 1M de notebooks on Github (2017)
- ...

## Jupyter Notebook
<div class="row" style="display:flex;width:100%">
<div class="column" style="margin:10px; flex:auto">
<ul>
    <li> A document format (in JSON)
    <li> A client-server web app
    <li> Mix text, results and code (with local or remote execution).
</ul>

Limitations :
<ul>
<li>Not the only nor the first Notebook (Mathematica, Apache Zeppelin, Rmarkdown...)
<li> Bad versionning (JSON...), non-linear execution of cells...
</ul>
</div>
<div class="column" style="margin:10px; flex:auto">
<img src="images/jupyter_notebook.png">
</div>
</div>

## Ipywidgets

- Widgets allowing graphical interactions
- 2D, 3D plotting librairies built on these 

http://jupyter.org/widgets

## Jupyterlab

- Same notebook format/server but greatly improved client interface
- A web IDE (not quite there yet)
- A View/Model mechanism for all documents
  - allow e.g. to write a document in md/latex and see live preview
- Highly customizable by extensions (all curent parts are extensions) :
  - git/github
  - draw.io
  - geojson 
  - ...
  
 **To install**
 *conda install -c conda-forge jupyterlab*

 You can try it online here : [https://mybinder.org/v2/gh/jupyterlab/jupyterlab-demo/master?urlpath=lab/tree/demo/Lorenz.ipynb](https://mybinder.org/v2/gh/jupyterlab/jupyterlab-demo/master?urlpath=lab/tree/demo/Lorenz.ipynb)

## JupyterHub


<div class="row" style="display:flex;width:100%">
<div class="column" style="margin:10px; flex:auto">
<h3> Components </h3>
<ul>
<li>A web proxy
<li>An environnement image (docker)
<li>A list of users
</ul>

</div>
<div class="column" style="flex:auto;margin:10px">
<img src="images/jupyterhub_schema.png">
</div>
</div>

## BinderHub

<div class="row" style="display:flex; margin: 0 auto; width: 100%">
<div class="column" style="flex:30%; margin: 10px">
    Combine the proxy to docker instance of Jupyterhub with a project for "repo to docker image"

<ul>
<li> Put your code (demo/tuto, course...) on a github repo online
<li> Generate a link on https://mybinder.org/ from your repo link
<li> When going to this new url, any web user get a sandbox containing your code and with all wanted packages already installed.
</ul>
</div>
<div class="column" style="flex:40%; margin: 10px">
<img src="images/architecture.png">
</div>
</div>


## Summary of user stories

- Do data analysis, prototyping...
    -> Jupyterlab : Notebook + editor+console+terminal
- Publish a demo/tuto of a library
    -> BinderHub : https://mybinder.org/
- Share a static (html) version of a notebook online  :
    -> nbviewer : https://nbviewer.jupyter.org/
- Give a working environment to students  :
    -> jupyterhub : https://jupyterhub.u-ga.fr
- Give, fetch and grade exercises : -> nbgrader

 ## Lots of utilities

- [nbconvert](https://github.com/jupyter/nbconvert) (used by nbviewer and "Download as" menu) : convert notebook in md, latex, pdf, slides html
- [RISE](https://github.com/damianavila/RISE) : jupyter in slides mode
- [nteract](https://nteract.io/) : notebook in native app (no browser)
- [hydrogen](https://nteract.io/atom) : interactive coding in Atom editor
- [notedown](https://github.com/aaren/notedown)/[ipyrmd](https://github.com/chronitis/ipyrmd) : write a notebook in (r)markdown
- [nbinteract](https://github.com/SamLau95/nbinteract)/[thebelab](https://github.com/minrk/thebelab) : interactive html
- [Gallery of notebooks, books etc...](https://github.com/jupyter/jupyter/wiki/a-gallery-of-interesting-jupyter-notebooks)
- [Colaboratory](https://colab.research.google.com) : jupyter notebook in Google Drive : collaborative :-), Google :-(