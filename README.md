# Drawio Presentation template and tools

Template and associate scripts to create presentations using drawio as the source file format.

Basic idea is to make it easy to create presentation that can be viewed either directly in drawio, as individual images or
as a JupyterLab RISE notebook.

The script `mkpres` should set everything up for you.

## Installation and Usage

### Install

clone this repo and run the `mkpres` script. Eg
```
$ git@github.com:jappavoo/prestemplate.git
```

Note you might find it useful to put your clone of prestemplate into your path to make your day to day live easier.

### Usage

#### Create a new presentation

Assuming you are in the parent directory of where you cloned
```
$ prestemplate/mkpres ~/myclass/lec1
$ ls ~/myclass/lec1
diox		lec1.drawio	Makefile	mknb.py
```

1. In `~/myclass/lec1` you will find your new presentation template.  Edit and modify `~/myclass/lec1.drawio` as you like.
2. The prensentation source is git friendly so recommend that you use a git repo to manage your presentation


#### Build

To create images and JupyterLab RISE Notebook versions:

```
$ make -C ~/myclass/lec1/
./diox lec1.drawio lec1.imgs
lec1.drawio -> /tmp/76947_lec1.drawio.xml
0 1 2 3 4
lec1.drawio -> lec1.imgs/000.png
lec1.drawio -> lec1.imgs/001.png
lec1.drawio -> lec1.imgs/002.png
lec1.drawio -> lec1.imgs/003.png
lec1.drawio -> lec1.imgs/004.png
python3.11 ./mknb.py lec1.imgs -o lec1.ipynb
RISE slide notebook created: lec1.ipynb
$ ls ~/mylcass/lec1
diox		lec1.drawio	lec1.imgs	lec1.ipynb	Makefile	mknb.py
```


## Under the Hood

### Template 

basicwhite.drawio is template that mimics a basic white presentation you might find in a standard presentation application

### Tools/scripts

- `mkpres` a script that creates a new presentation using the contents of this directory
- `diox` is a bash script that extracts the pages of a drawio file and saves them as images to a directory.
- `mknb.py` is a python script that will create a jupyterlab RISE notebook with each cell corresponding to an image from the specified directory.
- `Makefile` a makefile that automates this


