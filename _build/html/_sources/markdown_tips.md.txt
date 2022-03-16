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