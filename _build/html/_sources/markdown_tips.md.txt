# Markdown Tips

We are cooking, baby! 

We are **Testing** .

+ Our `images` works really well:
    
## Test-1

`![HOT](https://datadocs.bco-dmo.org/d2/images/logos/logo_HOT.jpg)`

![HOT](https://datadocs.bco-dmo.org/d2/images/logos/logo_HOT.jpg)

## Test-2
    
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

## Test-3

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


## Test-4

:::{warning}
Testing this warning.

- Careful, I am watching you =)

:::