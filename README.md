# Sphinx and Markdown training

[Reference: talkpython](https://training.talkpython.fm/courses/details/static-sites-with-sphinx-and-markdown)

> Static Website with Sphinx and Markdown
> I am using macOS Big Sur 11.6

## 1. Setup 
1. Create a new project folder

    ```shell script
    $mkdir /Users/fcp/workspace/1.git/sphinx-fcp
    $cd  /Users/fcp/workspace/1.git/sphinx-fcp
    ```

2. Create a python environment with `CONDA`

    ```shell script
    $conda create --prefix ./.env python

    # activate 
    $conda acvtivate .env/

    #update pip
    $conda update pip
    ```

3. Installing Sphinx 

    + See all Sphinx installations [HERE](https://www.sphinx-doc.org/en/master/usage/installation.html)

    ```shell script
    $conda install sphinx
    ```

4. Check Sphinx installation

    ```shell script
    $which sphinx-quickstart
    ```
    > For me: `/Users/fcp/workspace/1.git/sphinx-fcp/.env/bin/sphinx-quickstart`

5. Make a Sphinx Site

    ```shell script
    # On your project folder, `/Users/fcp/workspace/1.git/sphinx-fcp`, type:

    $sphinx-quickstart
    ```

    + Answer the following questions

    ```shell script
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

    ```shell script
    $tree                                                              

        ├── Makefile
        ├── README.md
        ├── _build          -> An empty directory (for now) that will hold the rendered documentation.
        ├── _static         -> An empty directory (custom site assets)
        ├── _templates      -> An empty directory (custom templates)
        ├── conf.py         -> A Python script holding the configuration of the Sphinx project. It contains the 
        ├                      project name and release you specified to sphinx-quickstart, as well as some extra 
        ├                      configuration keys.
        ├
        ├── index.rst       -> The root document of the project, which serves as welcome page and contains 
        ├                     the root of the “table of contents tree” (or toctree).
        ├ 
        └── make.bat        -> Convenience scripts to simplify some common Sphinx operations, 
                               such as rendering the content.
    ```
6. Livereload
    > LiveReload monitors changes in the file system. As soon as you save a file, it is preprocessed as needed, 
                 and the browser is refreshed.
    + Install livereload:
    
    ```shell script
    $conda install -c conda-forge livereload    
    ```

    + Create a python file to run livereload   
    ```shell script
    $touch run_livereload
    ```
    + Edit `run_livereload.py` with the following:
    
    ```python
    from livereload import Server, shell

    if __name__ == '__main__':
    server = Server()
    server.watch('*.rst', shell('make html'), delay=1)
    server.watch('*.md', shell('make html'), delay=1)
    server.watch('*.py', shell('make html'), delay=1)
    server.watch('_static/*', shell('make html'), delay=1)
    server.watch('_templates/*', shell('make html'), delay=1)
    server.serve(root='_build/html')
    ```
   
7. Added `.env/` folder to `conf.py`.
    
    ```python
    exclude_patterns = ['_build', 'Thumbs.db', '.DS_Store','.env']
    ```
 
8. Render the documentation as HTML for the first time
 
    ```shell script
    $sphinx-build -b html ../sphinx-fcp _build/html  
    
    # you should see
    Running Sphinx v4.4.0
    making output directory... done
    building [mo]: targets for 0 po files that are out of date
    building [html]: targets for 1 source files that are out of date
    updating environment: [new config] 1 added, 0 changed, 0 removed
    reading sources... [100%] index                                                                                                                                                                                                            
    looking for now-outdated files... none found
    pickling environment... done
    checking consistency... done
    preparing documents... done
    writing output... [100%] index                                                                                                                                                                                                             
    generating indices... genindex done
    writing additional pages... search done
    copying static files... done
    copying extra files... done
    dumping search index in English (code: en)... done
    dumping object inventory... done
    build succeeded.

    The HTML pages are in _build/html.
    ```   
   
9. Testing the installation

    ```shell script
    $ python ./run_livereload.py
    # go to http://127.0.0.1:5500, and check the website 
    ```
   
10. Add Markdown

    + Install MyST - Markedly Structured Text
        >   Allows you to write sphinx documentation entirely in markdown.
    
    ```shell script
    $conda install -c conda-forge myst-parser
    ```
    
    + open `conf.py`, and add the following:
    
    ```python
    extensions = [
        "myst_parser",
    ]
    ```
   
11. Testing the markdown file

    + Create the following
    ```shell script
    $touch about_us.md
    ```
    
    + Add the following:
    
    ```markdown
    # This is us =)  

    > Testing! 

    ### 1. Test
    ### 1.1 Testing 

    1. Test1
    2. Test2

    + Test3 
    - Test4
    ```

    + add `about_us.md` to `index.rst`
    
    ```rst
    TEST PAGE!
    =====================

    Welcome to the future?.

    .. toctree::
       :maxdepth: 2
       :caption: Contents:

       about_us

    ```     

12. Clean up

    + Rename `index.rst`
    
    ```shell script
    mv index.rst index.md
    ```
    
    + convert the text to:
    
    ```markdown
    # Testing our First Sphinx Homepage

    Welcome to the future.

        ```{toctree}
        :maxdepth: 2
        :caption: "Contents:"
           
        about_us
        ```
    ```
 
## 2. Markdown TIPS:

1. How to display  images:
     
    `![HOT](https://datadocs.bco-dmo.org/d2/images/logos/logo_HOT.jpg)`, generates the following:

    ![HOT](https://datadocs.bco-dmo.org/d2/images/logos/logo_HOT.jpg)

2. Download the image locally:
    
    ```shell script
    curl https://datadocs.bco-dmo.org/d2/images/logos/logo_HOT.jpg > _build/hmtl/_images/logo_HOT.jpg 
    ```
    
3. Edit and display:

    + add the following in the `about_us.md` file: 
   
    ```markdown
        ```{image} _build/html/_images/logo_HOT.jpg
        :alt: HOT-2
        :class: bg-primary
        :width: 200px
        :align: center
        ```
    ```
    > You will notice that the image is now centered in the page

4. Add/Enable some MyST extensions.

    + edit your `conf.py` file with the following :
    
    ```python
    # Enable some MyST extensions.
    myst_enable_extensions = [
        "colon_fence",
    ]
    ```
    
    + Add the following into `about_us.md`:
    ```markdown
    :::{figure-md} logo-target
    :class: myclass

    <img src="_build/html/_images/logo_HOT.jpg" alt="HOT-2" class="bg-primary" width="300px">

    Hawaii Ocean Time-Series *University of Hawaii*.
    :::
    ```
   
   + Add the following in the `index.md` file.
   
   ```markdown
   Testing this thing {ref}`logo-target`.
   ```

5. Adding Warnings
    
    ```markdown
    :::{warning}
    Testing this warning.
  
    - Careful, I am watching you =)
    
    :::
    ```

6.  Do the following to change the link title automatically 

    ```markdown
    Add this line to test linking [](markdown_tips.md)
    ``` 
    
7. For  heading references:     
    
   ```markdown
    (heading-role)=
    ### Heading and Role
    ```
    > Now you can type ``` {ref}`heading-role` ``` to see {ref}`heading-role`

## 3. Documenting your Code
 
1. Literalinclude   
 
    ````markdown   
    ```{literalinclude} run_livereload.py
    :emphasize-lines: 2-4  
    ``` 
    ````

2. Autodoc

    With Autodoc, your sphinx doc will automatically create a structure,
    highlighted, interlinked collection of sections. Also, symbols in the code
    will become `roles` in sphinx which you can directly to.  
       
    + Turn on `autodoc` by editing `conf.py`. Also, add the current directory 
    to the front of our `PYTHONPATH`, so our module can be imported. 

    ```python
    import os
    import sys
    sys.path.insert(0, os.path.abspath('.'))

    extensions = [
       "myst_parser",
       "sphinx.ext.autodoc",
    ]
    ```

    + Documenting a Python Module
    
    Let's create a page called `my_api.py` into which we would like
    to include some module documentation.
    
    ```markdown
    touch my_api.py
    ```
    
    The [Sphinx extension `autodoc`](https://myst-parser.readthedocs.io/en/latest/sphinx/use.html?highlight=sphinx.ext.autodoc#use-sphinx-ext-autodoc-in-markdown-files)
    , which pulls in code documentation from docstrings, is currently hard-coded to 
    parse reStructuredText. This is incompatible with our MyST extension. However, we can use `eval-rst` to make  
    `autodoc` work.
    
    ````markdown
    ```{eval-rst}
    .. autoclas:: my_api.MyDemo
    ```
    ````
      
    + Lets install the `sphinx-autodoc-typehints` and also enable [`sphinx.ext.napoleon`](https://www.sphinx-doc.org/en/master/usage/extensions/napoleon.html).
    These is to teach Sphinx to interpret the docstring and typehints.
   
    ```shell script
    # use the module flag -m with python so that it uses the conda python for the installation
    python -m pip install sphinx-autodoc-typehints        
i   ``` 