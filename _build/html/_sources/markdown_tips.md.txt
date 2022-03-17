# Markdown Tips

We are cooking, baby! 

We are **Testing** .

+ Our `images` works really well:
    
## Add Figure

`![HOT](https://datadocs.bco-dmo.org/d2/images/logos/logo_HOT.jpg)`

![HOT](https://datadocs.bco-dmo.org/d2/images/logos/logo_HOT.jpg)

## Edit Figure
    
```
    ```{image} _build/html/_images/logo_HOT.jpg
    :alt: HOT-2
    :class: bg-primary
    :width: 200px
    :align: center
    ```
```

```{image} _build/html/_images/logo_HOT.jpg
:alt: HOT-2
:class: bg-primary
:width: 200px
:align: center
```

## Edit Figure -2

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


## Warnings

```markdown
:::{warning}
Testing this warning.

- Careful, I am watching you =)

:::
```

Generates:

:::{warning}
Testing this warning.

- Careful, I am watching you =)

:::

## Linking

+  Do the following to change the link title automatically. 

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
+ Now you can type ``` {ref}`heading-role` ``` to see {ref}`heading-role`


## Documenting Code 

+ Include your code from a file with lines emphasized

    ````markdown 
    ```{literalinclude} run_livereload.py
    :emphasize-lines: 2-3
    ``` 
     ````
+ The a above code generates the following:

    ```{literalinclude} run_livereload.py
    :emphasize-lines: 2-3
    ```
  
+ Documenting a Module: 
     
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
    > This is visually nice! Also, it's semantically rich.
    
## Referencing Symbols
 
+ Example-1 , we can us `MyST` extended markdown syntax:

    ```markdown
    As we can see in [This is my_api.md](my_api.MyDemo), this is nice!
    ```
    As we can see in [This is my_api.md](my_api.MyDemo), this is nice!

+ Example-2, we can also use `role-base` syntax:

    ```markdown
    As we can see in {py:class}`my_api.MyDemo`, this is nice!
    ```
    As we can see in {py:class}`my_api.MyDemo`, this is nice!
    
+ Example-3, provide your own text:

    ```markdown 
    As we can see in {py:class}`TESTING!<my_api.MyDemo`, this is nice!
    ```
    As we can see in {py:class}`TESTING!<my_api.MyDemo>`, this is nice!

## Linking Between Sites with Intersphinx