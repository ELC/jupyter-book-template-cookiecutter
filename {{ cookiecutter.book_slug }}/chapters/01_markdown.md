---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: '0.8'
    jupytext_version: '1.4.1'

kernelspec:
  display_name: Python 3
  name: python3
---

# Markdown based Notebook

Jupyter Book allows Markdown Based Notebooks, these are plain text instead of the json based format of the traditional notebooks (.ipynb). There are some things to keep in mind when using this format as explained below.

There is also a [traditional Jupyter version](02_jupyter.ipynb) of this chapter.

## Advantages and Disadvantages of Markdown Based Notebooks

### Advantages

- The notebook is plain text, i.e. easier to manipulate, friendlier with git and does not require any special software.
- Load time is faster and can be modified in any text editor.
- Does not require any software to be installed, not even Python, the book can be built in a CI/CD pipeline.
- More resilient to format errors, i.e. if the ipynb is an invalid JSON the whole notebook cannot be rendered.
- It is easier to add tags to code cells, no need for plugins or addons.
- Readers will have the additional option to download the chapter as a markdown file
- Readers can execute code directly on the site with Thebe (this is also possible with ipynb)

### Disadvantages

- In Markdown notebooks the output for any code cell is not shown before building the notebook.
- The notebook needs to be executed at build time.
- Kernel details should be provide at the top as metadata.
- No actual separation "in cells", everything is a long text file.
- For local builds using Windows, Python 3.7 should be used - 3.8+ is not yet supported.
- No support for Colab (GPU) or Binder

```{warning}
If the notebook requires external tools for the kernel (e.g. Matlab), the only available format is the Traditional Jupyter (.ipynb)
```

```{warning}
If you want support for Binder and / or Colab Execution (e.g. for GPU processing), only Traditional Jupyter (.ipynb) are supported
```

## Standard Markdown

These features are supported by all renderers as they are part of the basic set of features of Markdown. Some examples were extracted from the [official docs](https://www.markdownguide.org/basic-syntax).

```{code-cell}
print("Here is a Python cell2")
```

### Text Formating

In a Markdown text one can use **bold**, *italics* or ***both***. It is also posible to combine it with `monospace`.

### Quotes

>It is also possible to quote

### Lists

To keep everything organize, one usually use lists either ordered

1. Step 1
1. Step 2
1. Step 3


Or without any order

- Requirement 1
- Requirement 2
- Requirement 3

### Horizontal Rule

Useful to separate sections

---

From other non-related topic

### Links

You know that there many search engines online? 

There are [some](https://duckduckgo.com/) which focus on privacy, [others](https://www.startpage.com/) just work arround Google and [there is also one](https://www.searchencrypt.com/) that uses ecryption!

### Images

One image is worth a thousand words some say

![Alternative text](https://upload.wikimedia.org/wikipedia/commons/thumb/3/38/Jupyter_logo.svg/663px-Jupyter_logo.svg.png)

But it is even better if you can click them

[![Alternative text](https://upload.wikimedia.org/wikipedia/commons/thumb/3/38/Jupyter_logo.svg/663px-Jupyter_logo.svg.png)](https://jupyter.org/)


## Limited Support

These features are part of some flavours of Markdown but not all renderers can process them. It is recommended to visualize this document in the target platform to check exactly which features are supported

### Tables

Tables are really complicated in Markdown and should only be generated by [a specialized tool](http://www.tablesgenerator.com/markdown_tables). Don't modify markdown tables manually

| Syntax | Description |
| ----------- | ----------- |
| Header | Title |
| Paragraph | Text |

### Block of Code

For code blocks, Jupyter Book will add a ```Copy``` button in the top left corner to easily copy all the text in the block.

Some times one wants to share data

(data)=
```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

Or simply say hello

```python
print("Hello World!")
```

### Footnotes

Here's a sentence with a footnote. [^1]

[^1]: This is the footnote.


### Math

Some renderers can process inline math, $x=2$ and other can also process whole line math

$$
  \int_0^\infty \frac{x^3}{e^x-1}\,dx = \frac{\pi^4}{15}
$$


If supported, alignment can be done with array

$$
\begin{array}{llll}
a_{11}& =b_{11}& a_{12}& =b_{12}\\
a_{21}& =b_{21}& a_{22}& =b_{22}+c_{22}
\end{array}
$$

### Not supported in Jupyter Book

These are features that some renderers support but are not supported by Jupyter Book

#### Strikethrough

Some times you ~~make a mistake~~ have a great idea

However, a HTML approach can produce the desired result

Some times you <s>make a mistake</s> have a great idea

#### Check List

- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

However, a HTML approach can produce the desired result

<label><input type="checkbox"> Write the press release</input></label><br>
<label><input type="checkbox"> Update the website</input></label><br>
<label><input type="checkbox"> Contact the media</input></label><br>


## MyST Specific

These are some features that are the moment are only compatible with Jupyter Book. That means that rendering the notebook in other services (Github, NBviewer, Nteract, Data Lore, etc.) might not work as shown below. If your only target platform is Jupyter Book, you can use any of the following.


### Colored Admonitions

```{note}
Here is a Note
```

```{important} 
Here is an important
```

```{admonition} Tip
:class: tip
Here is a Tip
```

```{attention} text
Here is an attention
```

```{warning}
Here is a Warning
```

```{error}
Here is an error
```

```{admonition} admonition
Here is a custom admonition
```

### Hidden Toggles

```{toggle} Click the button to reveal!
Some hidden toggle content!
```


### Dropdowns

```{dropdown} Outside Content
Inside Content
```

(homework)=
### Dropdowns with Admonitions

```{note}
:class: dropdown
The note body will be hidden!
```


### Panels


```{panels}
Panel header 1
^^^
Panel body 1
+++
Panel footer 1
---

Panel header 2
^^^
Panel body 2
+++
Panel footer 2
```

### Tabs

```{tabbed} Tab 1 title
My first tab
```

```{tabbed} Tab 2 title
My second tab with `some code`!
```


### Sidebars

```{sidebar} My sidebar title
My sidebar content
```

Sidebars are shown in parallel to the main text, but they span inwards from the margins.


### Margin Note

```{margin} An optional title
My margin content
```

Margin notes are more discrete, useful for pointing minor details or add extra information.

They span from the margin outwards


### Labels

Would you like to write homework for your students? Check the [dropdowns](homework)!

It is always important to provide enough [data](data) to support claims!


### Equations

#### Without Label

```{math}
x^2 + y^2 = 1
```

#### With Label

```{math}
:label: algebra
x^2 + y^2 = 1
```


If the equation has a label, it can be then referenced [](algebra)


### Citation

There are two types of citations, by name (similar to APA style) and by number (similar to IEEE style).

Citations can be customized, for more detailed explanations please refer to one of the Jupyter Book docs ([here](https://jupyterbook.org/tutorials/references.html), [here](https://jupyterbook.org/content/references.html) or [here](https://jupyterbook.org/content/citations.html)) and the [associated extension docs](https://sphinxcontrib-bibtex.readthedocs.io/en/latest/usage.html).

#### By Name

This project uses the Python Language {cite}`perez2011python`.to build Jupyter Book {cite}`executable_book`

This will not work unless there is a section called `bibliography``

#### Bibliography for Names

There are different styles for the bibliography in this case

##### Alphanumeric - Sorted by Author, year

```{bibliography}
:style: alpha
```

##### Alphanumeric - Sorted by order of appearance

```{bibliography}
:style: unsrtalpha
```

##### Numeric - Sorted by Author, year

```{bibliography}
:style: plain
```

##### Numeric - Sorted by order of appearance

```{bibliography}
:style: unsrt
```


#### By Number

This project uses the Python Language {footcite}`perez2011python`.to build Jupyter Book {footcite}`executable_book`

This will not work unless there is a section called `footbibliography`

For different citation styles, check the [official docs](https://sphinxcontrib-bibtex.readthedocs.io/en/latest/usage.html#roles-and-directives)

When using `footcite` and `footbibliography`, the numbers will be arranged in combination with the footnotes. This could lead to confusion for the reader if this type of references are used in combination with footnotes. To mitigate this issue, a similar result can be achieve using `cite` and `bibliography` with the `unsrt` style.


#### Bibliography for Numbers

In this case, there is a single style

```{footbibliography}
```
