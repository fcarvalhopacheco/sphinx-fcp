# MyST + Markdown 

## Images
### Add Figure-1

`![HOT](https://datadocs.bco-dmo.org/d2/images/logos/logo_HOT.jpg)`

![HOT](https://datadocs.bco-dmo.org/d2/images/logos/logo_HOT.jpg)

### Edit Figure-2
    
````
```{figure} _build/html/_images/logo_HOT.jpg
:class: bg-primary
:width: 200px
:align: center
:name: hot-logo
```
````

```{figure} _build/html/_images/logo_HOT.jpg
:class: bg-primary
:width: 200px
:align: center
:name: hot-logo

Hawaii Ocean Time-Series *University of Hawaii*.

```

## Alerts 

### Note
        
````markdown
:::{note}
Testing this NOTE.
:::

or 

```{note}
Testing this note.
```
````

:::{note}
Testing this note.
:::

### Tip

````markdown
:::{tip}
Testing this TIP.
:::

or 

```{TIP}
Testing this TIP.
```
````

:::{TIP}
Testing this TIP.
:::
    
### Important 

````markdown
:::{important}
Testing this is important.
:::

or 

```{important}
Testing this is important.
```
````

:::{important}
Testing this important.
:::

### Caution 

````markdown
:::{caution}
Testing this caution.
:::

or 

```{caution}
Testing this caution.
```
````

:::{caution}
Testing this caution.
:::

### Warning 

````markdown
:::{warning}
Testing this warning.
:::

or 

```{warning}
Testing this warning.
```
````

:::{warning}
Testing this warning.
:::


        
````markdown
:::{seealso}
Testing this see also.
:::

or 

```{seealso}
Testing this seealso.
```
````

:::{seealso}
Testing this seealso.
::: 
    
## Linking

+ Do the following to change the link title automatically. 

    ```markdown
    Add this line to test linking [](markdown_tips.md)
    ``` 
    Add this line to test linking [](markdown_tips.md)

    
(heading-role)=
### Example to link this Head
    
```
(heading-role)=
### Example to link this Head
```

```{note}
Now you can type ``` {ref}`heading-role` ``` to see {ref}`heading-role`
```

## Documenting Code 

### Emphasize lines

````markdown 
```{literalinclude} my_api.py
:emphasize-lines: 2-3
``` 
 ````

+ The a above code generates the following:

    ```{literalinclude} my_api.py
    :emphasize-lines: 2-3
    ```
  
### Documenting a Module: 
     
````markdown
```{eval-rst}
.. autoclass:: my_api.MyDemo:W

  :members:
```
````

```{eval-rst}
.. autoclass:: my_api.MyDemo
  :members:
```

```{note}
This is visually nice! Also, it's semantically rich.
```

### Referencing Symbols
 
1. First example , we can us `MyST` extended markdown syntax:

    ```markdown
    As we can see in [This is my_api.md](my_api.MyDemo), this is nice!
    ```
    As we can see in [This is my_api.md](my_api.MyDemo), this is nice!

2. Second example, we can also use `role-base` syntax:

    ```markdown
    As we can see in {py:class}`my_api.MyDemo`, this is nice!
    ```
    As we can see in {py:class}`my_api.MyDemo`, this is nice!
    
3. Third example, provide your own text:

    ```markdown 
    As we can see in {py:class}`TESTING!<my_api.MyDemo`, this is nice!
    ```
    As we can see in {py:class}`TESTING!<my_api.MyDemo>`, this is nice!

### Cross-Referencing 

#### Testing Intersphinx 

````{important}
-Make sure to activate `sphinx.ext.intersphinx` on your `conf.py` 

-See details here: {ref}`/readme.md#setting-up-intersphinx-extension`
````

- ```[](cchdo-website:oxygen)``` -> [](cchdo-website:oxygen)
- ````{ref}`cchdo-website:parameters````--> {ref}`cchdo-website:parameters`
- ````{ref}`cchdo-website:Bottle Quality Codes```` -->  {ref}`cchdo-website:Bottle Quality Codes`

#### Implicit Targets

````{important}
This requires setting ``myst_heading_anchors = 3`` in your ``conf.py``,
```{seealso}
[Auto-generated header anchors](https://myst-parser.readthedocs.io/en/v0.15.1/syntax/optional.html#auto-generated-header-anchors).
```
````
+ You can use `[](#linking)` to see [](#linking)
    
#### Numbered Reference Role     

````{important}
This requires setting ``numfig = True`` in your ``conf.py``,
````

+ The `numref` role is used to reference numbered elements of the documentation, such as tables and images.

    ````markdown
    ```{figure} _build/html/_images/kilo-moana.jpg
    :scale: 40%
    :align: center
    :name: kilo-moana-2
    
    R/V Kilo Moana 
    ```
    ````

    ```{figure} _build/html/_images/kilo-moana.jpg
    :scale: 40%
    :align: center
    :name: kilo-moana-2

    R/V Kilo Moana - Test 2
    ```

    Now you can start referencing {numref}`kilo-moana-2` --> ``` {numref}`kilo-moana-2` ```

#### Automatically Label sections

+ Sphinx can automatically create explicit targets for all sections!  

    ````{important}
    This requires the following setting on your `conf.py` file
  
    ```python
    # Add the extension
    extensions = [
       'sphinx.ext.autosectionlabel',
    ]

    # Make sure the target is unique
    autosectionlabel_prefix_document = True
    ```
    ````
    
    ` {ref}`readme:setup` ` --> {ref}`readme:setup`
 
 