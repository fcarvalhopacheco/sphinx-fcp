# Sphinx and Markdown training

[Reference: talkpython](https://training.talkpython.fm/courses/details/static-sites-with-sphinx-and-markdown)

Static Website with Sphinx and Markdown

```{important}
I am using macOS Big Sur 11.6
```

## 1. Setup 
1. On your terminal, create a new project folder:

    ```shell script
    mkdir /Users/fcp/workspace/1.git/sphinx-fcp
    cd  /Users/fcp/workspace/1.git/sphinx-fcp
    ```
    ```{note}
    Replace `/Users/fcp/workspace/1.git/sphinx-fcp` with your own `path` and folder name
    ```
2. Create the following local environment:
    
    (conda/create)=
    
    ```shell script
    conda create --prefix ./.env python=3.10 ipython=8.1.1 sphinx=4.4.0 sphinx-autobuild=2021.3.14 myst-parser=0.17.0 sphinx-autodoc-typehints=1.12.0 nbsphinx=0.8.8 sphinx-book-theme=0.2.0
    ````
    
    ```{seealso}
    For more information about the packages, please check: 
    
    [ipython](https://ipython.org)
    
    [sphinx](https://sphinx-book-theme.readthedocs.io/en/stable/)
   
    [sphinx-autobuild](https://github.com/executablebooks/sphinx-autobuild)
   
    [myst-parser](https://github.com/executablebooks/MyST-Parser)
   
    [sphinx-autodoc-typehints](https://github.com/tox-dev/sphinx-autodoc-typehints)
   
    [nbsphinx](https://nbsphinx.readthedocs.io/en/0.8.8/)
   
    [sphinx-book-theme](https://sphinx-book-theme.readthedocs.io/en/stable/)
    ```
   
2. When conda asks you to proceed, type `y`:    
   
    ```shell script
    proceed ([y]/n)?
    ```
    This creates the .env/ environment on your selected `path` with the above packages with `python=3.10` version.

    ```{tip}
    Install all the programs that you want in this environment at the same time. 
    Installing 1 program at a time can lead to dependency conflicts. **I learned the hard way :/**
    ```
   
    ```{seealso}
    Check more tips [**here**](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)
    ```
3. Activate your environment created with the prefix `.env/` :
    
    ```shell script
    conda acvtivate .env/
    ```

4. Check Sphinx installation:

    ```shell script
    which sphinx-quickstart
    ```
    ```{note}
    For me: `/Users/fcp/workspace/1.git/sphinx-fcp/.env/bin/sphinx-quickstart`
    ```
5. Make a Sphinx website using our downloaded theme `sphinx-book-theme`:

    ```shell script
    sphinx-quickstart
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

    + This is the new tree of the project:

        ```shell script
        tree                                                              

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
   
6. Add `.env/` folder to `conf.py`:
    
    ```python
    exclude_patterns = ['_build', 'Thumbs.db', '.DS_Store','.env']
    ```
 
7. Render the documentation as HTML for the first time:
 
    ```shell script
    sphinx-build -b html ../sphinx-fcp _build/html  
    
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
8. Start the website and start tracking changes:

    ```shell script
    sphinx-autobuild ../sphinx-fcp _build/html    
    ```   
    
    ```{note} 
    This will start a server at [http://127.0.0.1:8000/](http://127.0.0.1:8000/) and start watching for changes
    in the `~/sphinx-fcp` directory
    ```
    
9. Add Markdown:
    
    + open `conf.py`, and add the following:
    
        ```python
        extensions = [
            "myst_parser",
        ]
        ```
   
10. Play with Markdown:

    + Create the following
        ```shell script
        touch markdown_tips.md
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

    + add `markdown_tips.md` to `index.rst`:
    
        ```rst
        TEST PAGE!
        =====================

        Welcome to the future?.

        .. toctree::
           :maxdepth: 2
           :caption: Contents:

           markdown_tips

        ```     

11. Clean up:

    + Convert `index.rst` to `index.md` 
    
    + Edit the current `index.md` text to:
    
        ````markdown
        # Test 

        Welcome to my testing.

        Testing this thing {ref}`logo-target`

        Add this line to test linking [](markdown_tips.md)

        ```{toctree}
        :maxdepth: 2
        :caption: "Contents:"

        README
        markdown_tips
        ```
        ````

12. Other themes:

+ Check [Sphinx-Themes](https://sphinx-themes.org). Then, choose one of the examples and follow their installation guide.
+ Example:
    - If choose [Sphinx-rtd-theme](https://sphinx-themes.org/sample-sites/sphinx-rtd-theme/), you can install it by 
    doing the following:
    
        1. Install the theme
            ```shell script
            python -m pip install sphinx-rtd-theme 
            ```
      
        2. Edit `conf.py` file with the following:
            ```python
            html_theme = 'sphinx_rtd_theme'
            ```

        ```{warning}
        **Last reminder!**
       
        Install all the programs that you want in this environment at the same time. 
        
        Installing 1 program at a time can lead to dependency conflicts. 
        
        Edit `conda create --prefix ./.env ...... ` with your own theme. {ref}`Check Here <conda/create>`
        ```
13. Jupyter Notebooks
    - Find jupyter notebook tutorial
 
## 2. Markdown TIPS:

1. How to display  images:
     
    `![HOT](https://datadocs.bco-dmo.org/d2/images/logos/logo_HOT.jpg)`, generates the following:

    ![HOT](https://datadocs.bco-dmo.org/d2/images/logos/logo_HOT.jpg)

2. Download the image locally:
    
    ```shell script
    curl https://datadocs.bco-dmo.org/d2/images/logos/logo_HOT.jpg > _build/hmtl/_images/logo_HOT.jpg 
    ```
    
3. Edit and display:

    + add the following in the `markdown_tips.md` file: 
   
        ````markdown
        ```{image} _build/html/_images/logo_HOT.jpg
        :alt: HOT-2
        :class: bg-primary
        :width: 200px
        :align: center
        ```
        ````
        ```{tip``` 
         You will notice that the image is now centered in the page

4. Add/Enable some MyST extensions.

    + edit your `conf.py` file with the following :
    
        ```python
        # Enable some MyST extensions.
        myst_enable_extensions = [
            "colon_fence",
        ]
        ```
    
    + Add the following into `markdown_tips.md`:
        
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
    
    ```{tip}
    Now you can type ``` {ref}`heading-role` ``` to see {ref}`heading-role`
    ```



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
        
        + Add the following on your `markdown_tips.md ` file 
            ````markdown
            ```{eval-rst}
            .. autoclas:: my_api.MyDemo
            ```
            ````
      
        + Next, edit your `conf.py` to enable both Sphinx extensions
    
             ```python
             extensions = [
                "myst_parser",
                "sphinx.ext.autodoc",
                "sphinx.ext.napoleon",
                "sphinx_autodoc_typehints",
            ]
             ```
      
 3. Referencing Symbols
 
    + Open `markdown_tips.md` for editing. Let's talk about `my_api.md` using
    markdown syntax. 
 
    + Example-1 , we can us `MyST` extended markdown syntax:

        ```markdown
        As we can see in [This is my_api.md](my_api.MyDemo), this is nice!
        ```

    + Example-2, we can also use `role-base` syntax:

        ```markdown
        As we can see in {py:class}`my_api.MyDemo`, this is nice!
        ```
    
    + Example-3, provide your own text:

        ```markdown 
        As we can see in {py:class}`TESTING!<my_api.MyDemo`, this is nice!
        ```


## Linking between sites

1. Setting up your intersphinx tool extension

    + Open your `conf.py` file and add the following:
        ```python
        extensions = [
            "sphinx.ext.intersphinx",
        ]   
        ```
    + Add also the remote site that we would like to include inventories from. For example: 
        
        ```python
        intersphinx_mapping = {
            "cchdo-website": ("https://exchange-format.readthedocs.io/en/latest/index.html", None),
            }
        myst_url_schemes = ["http", "https", ] 
        
       ```
   