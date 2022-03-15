# Sphinx and Markdown training

[Access here](https://training.talkpython.fm/courses/details/static-sites-with-sphinx-and-markdown)

> Static Website with Sphinx and Markdown
> I am using macOS Big Sur 11.6

## 1. Setup

1. Create a new project folder

```sh
mkdir /Users/fcp/workspace/1.git/sphinx-fcp
cd  /Users/fcp/workspace/1.git/sphinx-fcp
```

2. Create a python environment with `CONDA`

```sh
conda create --prefix ./.env python

# activate 
conda acvtivate .env/

#update pip
conda update pip
```

3. Installing Sphinx 

+ See all Sphinx installations [HERE](https://www.sphinx-doc.org/en/master/usage/installation.html)

```sh
conda install sphinx
```

4. Check Sphinx installation

```sh
which sphinx-quickstart
```
> For me: `/Users/fcp/workspace/1.git/sphinx-fcp/.env/bin/sphinx-quickstart`


4. Make a Sphinx Site

```sh
# On your project folder, `/Users/fcp/workspace/1.git/sphinx-fcp`, type:

sphinx-quickstart
```

+ Answer the following questions

```
> Separate source and build directories (y/n) [n]: n

The project name will occur in several places in the built documentation.
> Project name: myfirst-sphinx
> Author name(s): Fernando Carvalho Pacheco <fernando.pacheco@hawaii.edu>
> Project release []:

If the documents are to be written in a language other than English,
you can select a language here by its language code. Sphinx will then
translate text that it generates into that language.

For a list of supported codes, see
https://www.sphinx-doc.org/en/master/usage/configuration.html#confval-language.
> Project language [en]:

Creating file /Users/fcp/workspace/1.git/sphinx-fcp/conf.py.
Creating file /Users/fcp/workspace/1.git/sphinx-fcp/index.rst.
Creating file /Users/fcp/workspace/1.git/sphinx-fcp/Makefile.
Creating file /Users/fcp/workspace/1.git/sphinx-fcp/make.bat.

Finished: An initial directory structure has been created.
```

+ This is the new tree of the project

```sh
❯ tree                                                              

├── Makefile
├── README.md
├── _build
├── _static
├── _templates
├── conf.py
├── index.rst
└── make.bat
```
