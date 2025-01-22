# Homepage

!!! warning "This site is continuously evolving and information may be missing or outdated."

Thank you for being patient and passing info and stuff that should be added or adjusted to Bram or Simon. 
Like this, our wiki will remain up-to-date.
Should you find this documentation particularly useful, you're always welcome to show so by treating us one or more :beers: :wink:

## Sitemap

-   Practical
    -   Getting started manual
    -   Belgium
    -   KU Leuven
    -   Work/Rega
-   Theory
    -   Phylogenetics
    -   Bayesian statistics
    -   Key papers
-   Helpful files
    -   Bank of slides
    -   Doctoral milestone examples
    -   Templates
    -   XML snippets
    -   Icons for presentations

## Searching for a file: 
Type what you are looking for in the search bar :fontawesome-solid-magnifying-glass:{.icons}! It is not google though, use keywords. 
![Search bar video](images/Screen%20Recording%202024-05-30%20at%2009.29.18.gif)

## Modifying a file - online

Click the small icon :fontawesome-solid-file-pen:{.icons} in the top right corner of the file.

Files are structured in Classic Markdown format. Have a look at the [GitHub Markdown Guide](https://guides.github.com/features/mastering-markdown/) or [mkdocs-material](https://squidfunk.github.io/mkdocs-material/reference/) for more information on how to format your text.

## Modifying a file - offline

You can clone the GitHub repo in the traditional way, modify its contents offline and push updates to the main branch. The dependencies are listed in requirements.txt. As always, it is good practise to work in a python virtual environment. If you are not familiar with virtual environments, is a good idea to learn about them (see for example [Python venv](https://python.land/virtual-environments/virtualenv)). The following commands can be used to create a virtual environment and install the dependencies:

```bash
# clone this repo
   $ git clone git@github.com:bramvrancken/SpELL-ULB.github.io.git   
# move into the repo directory   
   $ cd SpELL-ULB.github.io   
# create a virtual environment   
   $ python3 -m venv venv   
# activate the virtual environment   
   $ source ./venv/bin/activate   
# install dependencies   
   (venv) $ pip install -r requirements.txt   
```

Do not forget to add `venv` to the `.gitignore` file by adding the following lines:

```bash
# Ignore the virtual environment directory [mind the '/']
venv/
```

The list of dependencies can be updated as follows should additional dependencies be needed for further development:

```bash
(venv) $ pip freeze > requirements.txt
```