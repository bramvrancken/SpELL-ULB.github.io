# SpELL-wiki

Welcome to our lab wiki 👋! This is a collection of resources, tutorials, and guides that we have found useful. We hope that you will find them useful too.

## Modifying a file:

Click the small icon in the top right corner of the file.

Files are structured in Classic Markdown format. You can edit them directly on GitHub by clicking the pencil icon in the top right corner of the file. Have a look at the [GitHub Markdown Guide](https://guides.github.com/features/mastering-markdown/) or [mkdocs-material](https://squidfunk.github.io/mkdocs-material/reference/) for more information on how to format your text.

Type what you are looking for in the search bar:
![Search bar video](docs/images/Screen%20Recording%202024-05-30%20at%2009.29.18.gif)

## Working offline on these docs 

You can clone this repo in the traditional way, modify its contents offline and push updates to the master branch. The dependencies are listed in requirements.txt. As always, it is good practise to work in a python virtual environment. If you are not familiar with virtual environments, is a good idea to learn about them (see for example [Python venv](https://python.land/virtual-environments/virtualenv)). The following commands can be used to create a virtual environment and install the dependencies:

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






