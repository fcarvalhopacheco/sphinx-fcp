# Sphinx and Markdown training

[Access here](https://training.talkpython.fm/courses/details/static-sites-with-sphinx-and-markdown)

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