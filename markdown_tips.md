# Markdown Tips

## Add Figure-1

`![HOT](https://datadocs.bco-dmo.org/d2/images/logos/logo_HOT.jpg)`

![HOT](https://datadocs.bco-dmo.org/d2/images/logos/logo_HOT.jpg)

## Edit Figure-2
    
````
```{image} _build/html/_images/logo_HOT.jpg
:alt: HOT-2
:class: bg-primary
:width: 200px
:align: center
```
````

```{image} _build/html/_images/logo_HOT.jpg
:alt: HOT-2
:class: bg-primary
:width: 200px
:align: center
```

## Edit Figure-3

```
:::{figure-md} logo-target
:class: myclass

<img src="_build/html/_images/logo_HOT.jpg" alt="HOT-2" class="bg-primary" width="300px">

Hawaii Ocean Time-Series *University of Hawaii*.
:::
```


:::{figure-md} logo-target
:class: myclass

<img src="_build/html/_images/logo_HOT.jpg" alt="HOT-2" class="bg-primary" width="300px">

Hawaii Ocean Time-Series *University of Hawaii*.
:::


## Alerts (Note, Tip, Important, Caution, Warning, See also)

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

1.  Do the following to change the link title automatically. 

    ```markdown
    Add this line to test linking [](markdown_tips.md)
    ``` 
    Add this line to test linking [](markdown_tips.md)

    
(heading-role)=
### Heading and Role 
    
```
(heading-role)=
### Heading and Role
```

```{note}
Now you can type ``` {ref}`heading-role` ``` to see {ref}`heading-role`
```

## Documenting Code 

1. Include your code from a file with lines emphasized

    ````markdown 
    ```{literalinclude} my_api.py
    :emphasize-lines: 2-3
    ``` 
     ````
2. The a above code generates the following:

    ```{literalinclude} my_api.py
    :emphasize-lines: 2-3
    ```
  
3. Documenting a Module: 
     
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

## Referencing Symbols
 
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

## Cross-Referencing 

1. Testing interphinx and cross-referencing extension using CCHDO parameters: 

    ```{important}
    Make sure to activate `sphinx.ext.intersphinx` on your `conf.py` 
    See details here: `
    ```
    - ```[](cchdo-website:oxygen)``` -> [](cchdo-website:oxygen)
    - ````{ref}`cchdo-website:parameters````--> {ref}`cchdo-website:parameters`
    - ````{ref}`cchdo-website:Bottle Quality Codes```` -->  {ref}`cchdo-website:Bottle Quality Codes`

3. Implicit Targets

    ````{important}
    This requires setting ``myst_heading_anchors = 2`` in your ``conf.py``,
    ```{seealso}
    [Auto-generated header anchors](https://myst-parser.readthedocs.io/en/v0.15.1/syntax/optional.html#auto-generated-header-anchors).
    ```
    ````
    + You can use `[](#linking)` to see [](#linking)