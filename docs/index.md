# Homepage

!!! warning "This site is continuously evolving and information may be missing or outdated."

Thank you for being patient and passing info and stuff that should be added or updated to Bram or Simon. 
Like this, our lab wiki will remain up-to-date.
Should you find this documentation particularly useful, you're always welcome to show so by treating us one or more :beers: :wink:

## Searching for a file: 

Type what you are looking for in the search bar :fontawesome-solid-magnifying-glass:{.icons}! It is not google though, use keywords. 
![Search bar video](images/Screen%20Recording%202024-05-30%20at%2009.29.18.gif)

## Modifying a file - online

Click the small icon :fontawesome-solid-file-pen:{.icons} in the top right corner of the file.

Files are structured in Classic Markdown format. Have a look at the [GitHub Markdown Guide](https://guides.github.com/features/mastering-markdown/) or [mkdocs-material](https://squidfunk.github.io/mkdocs-material/reference/) for more information on how to format your text.

## Modifying a file - offline

If you want to contribute to the development of this wiki, ask Bram or Simon for access to the GitHub repo. You can clone it in the traditional way, modify its contents offline and push updates to the main branch. The dependencies are listed in requirements.txt. As always, it is good practise to work in a python virtual environment. If you are not familiar with virtual environments, is a good idea to learn about them (see for example [Python venv](https://python.land/virtual-environments/virtualenv)). The following commands can be used to download the repo, create a virtual environment and install the dependencies:

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

If you want a local preview of how the website renders, you can run the following command from the base dir, and go to the URL that is shown with your browser.

```bash
(venv) $ mkdocs serve
```

Files are structured in Classic Markdown format. Have a look at the [GitHub Markdown Guide](https://guides.github.com/features/mastering-markdown/) or [mkdocs-material](https://squidfunk.github.io/mkdocs-material/reference/) for more information on how to format your text.
