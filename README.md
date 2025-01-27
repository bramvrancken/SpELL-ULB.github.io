# SpELL-wiki

Welcome to our lab wiki 👋! This is a collection of resources, tutorials, and guides that we have found useful. We hope that you will find them useful too.

This wiki is made with Material for MkDocs. [MKDocs](https://www.mkdocs.org/) is a static website generator specifically designed for creating documentation websites. Material for MKDocs builds on this and adds lots of bells and whistles. If you want to learn about this, the [Material for MkDocs website](https://squidfunk.github.io/mkdocs-material/) has a thorough documentation, and tutorials like [this one](https://www.youtube.com/watch?v=xlABhbnNrfI) may also be helpful.


## Modifying a file - online

Click the small icon in the top right corner of the file.

Files are structured in Classic Markdown format. You can edit them directly on GitHub by clicking the pencil icon in the top right corner of the file. Have a look at the [GitHub Markdown Guide](https://guides.github.com/features/mastering-markdown/) or [mkdocs-material](https://squidfunk.github.io/mkdocs-material/reference/) for more information on how to format your text.

Type what you are looking for in the search bar:
![Search bar video](docs/images/Screen%20Recording%202024-05-30%20at%2009.29.18.gif)

## Modifying a file - offline

You can clone this repo in the traditional way, modify its contents offline and push updates to the main branch. The dependencies are listed in requirements.txt. As always, it is good practise to work in a python virtual environment. If you are not familiar with virtual environments, is a good idea to learn about them (see for example [Python venv](https://python.land/virtual-environments/virtualenv)). The following commands can be used to create a virtual environment and install the dependencies:

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

Next time you want to work on this repo, all you need to do is `cd` into the base folder and activate the virtual environment:

```bash
# move into the repo base directory   
   $ cd SpELL-ULB.github.io
# activate the virtual environment   
   $ source ./venv/bin/activate   
```

Should additional dependencies be needed for further development, these are to be added to the list of dependencies. This list can be updated as follows:

> to do: figure out which argument to pass so as to just get the dependencies that are used

```bash
(venv) $ pip freeze > requirements.txt
```

If you want a local preview of how the website renders, you can run the following command from the base dir, and go to the URL that is shown 

```bash
(venv) $ mkdocs serve
```

Files are structured in Classic Markdown format. You can edit them directly on GitHub by clicking the pencil icon in the top right corner of the file. Have a look at the [GitHub Markdown Guide](https://guides.github.com/features/mastering-markdown/) or [mkdocs-material](https://squidfunk.github.io/mkdocs-material/reference/) for more information on how to format your text.



