# image-processing-python-pillow-jupyter

Companion Jupyter Notebook for the “Image Processing in Python with Pillow and Jupyter Notebook” article.

## Required packages

To run this example you'll have to install the following libraries:

```
python3 -m pip install --upgrade jupyter
python3 -m pip install --upgrade pillow
```

These commands install the following modules:

- [**jupyter**](https://jupyter.org/) For managing and running our code effectively.
- [**pillow**]() For reading and modifying EXIF metadata. Most of the code in this article will use this module.

## Jupyter Notebook

<a href="https://jupyter.org/"><img src="https://images.ctfassets.net/23aumh6u8s0i/3WWvmj38IXJROqk5shzker/6a1e23405155f09b048e8b99a983aa24/jupyter_logo.png" alt="Jupyter logo" style="float: right;"></a>To make experimenting with Pillow easier, you’ll edit and run the code in this article using [Jupyter Notebook](https://jupyter.org/). It’s a web application for creating interactive documents called notebooks containing code and text.

Think of Jupyter Notebook as a web-based one-column spreadsheet where you can enter either text (in Markdown form) or code (in Python or several other programming languages) in each cell.

You can enter a single line of code into a cell and run it. You can also enter a function, several functions, or an entire class into a cell and run it. Once you run a cell, the notebook will remember any functions and classes you defined and any variables you declared within until you reload the page or restart the kernel running the code. You can update functions, classes, and variables by updating their cell and running it again.

Since it’s a web application and not a command-line one, Jupyter Notebook can display more than just text results. It can also display charts, graphs, images, and even interactive user interface controls without the need to launch an external application. Notebooks let you see graphical results right beside the code that produced them, and you’ll use this capability in this article’s exercises.


## Installation and Project Setup

As the title of this article implies, Python should be installed on your system. You can find the latest version at the official site, [Python.org](https://www.python.org/), as well as with other distributions such as [Anaconda](https://www.anaconda.com/), whose installer includes a lot of Python packages (including Jupyter Notebook) and tools for data scientists. 

### Installing and updating pip

If Python is installed on your system, chances are it also has `pip`, the Python Package Installer, but it might not be the current version. The commands below install `pip` if it isn’t on your system or update it if necessary.

On Windows, do this by entering the following into PowerShell:

```bash
python -m pip install --upgrade pip
```

On macOS and Linux, enter the following into Terminal:

```bash
python3 -m pip install --upgrade pip
```

### Installing and launching Jupyter Notebook

The next step is to install Jupyter Notebook, the environment you’ll use to run the code in this article. The commands below install Jupyter Notebook’s packages if they aren’t on your system or update them if necessary.

On Windows, install Jupyter Notebook by entering the following into PowerShell:

```bash
python -m pip install --upgrade jupyter
```

On macOS and Linux, enter the following into Terminal:

```bash
python3 -m pip install --upgrade jupyter
```

Once you’ve installed Jupyter Notebook, launch it by entering the following into PowerShell (if you’re on Windows) or Terminal (if you’re on macOS or Linux):

```bash
jupyter notebook
```

Jupyter Notebook will start and open the page at `http://localhost:8888/tree` with your default web browser. This is the Jupyter Notebook home page, and it looks like this:

![Jupyter Notebook home page](https://images.ctfassets.net/23aumh6u8s0i/50I7DliE55CZb8rc1vgnqa/ccf5df29ee33c1e5ea3eb5f98862f43f/jupyter_home_page.png)

### Creating a new notebook

The home page is for navigating your computer’s filesystem. Use it to find a place on your local drive to store the file for this article’s exercise (to open a folder on the home page, simply double-click it as if you were navigating the filesystem using your OS’ GUI).

Once you’ve found a place to store the file, create a new notebook by clicking on the _New_ button near the upper right corner of the page and selecting _Notebook_ from the menu that appears:

![Creating a new notebook](https://images.ctfassets.net/23aumh6u8s0i/4rW33TUtCrZsV9gi5dTH8u/fb3ab544b257af157ba620230e9ab28e/creating_a_new_notebook.png)

A dialog box asking you to select a kernel will appear. Kernels are processes that Jupyter Notebook uses to support programming languages. You’ll be working in Python, so make sure _Python 3 (ipykernel)_ is selected and click the _Select_ button:

![Selecting a kernel](https://images.ctfassets.net/23aumh6u8s0i/aHCQeFJP6WRVpK3Y5UmYI/8a9d6689f03afbc55a567a785ae77fb5/selecting_a_kernel.png)

> The default installation of Jupyter Notebook includes only the _Python 3_ kernel. It supports several other languages, including JavaScript, Java, Kotlin, Ruby, Scala, and others — see [this list](https://github.com/jupyter/jupyter/wiki/Jupyter-kernels) to find out which languages are supported and how to install other kernels.
You’ll see an empty notebook with a single cell. Let’s enter some code into it.

### Running a code cell

Enter the following into the cell:

```python
print("Hello, Notebook!")
print("Let’s process some images.")
```

Run the cell by either clicking on the _Run_ button in the toolbar or typing _Shift-Enter_:

![Running a code cell](https://images.ctfassets.net/23aumh6u8s0i/1PgYhptWQF5Yj6D71oXDKB/433bda3f843ae5dc12854672468a1a00/running_a_code_cell.png)

The code in the cell will execute, and you’ll see the following output:

![Results of running the code cell](https://images.ctfassets.net/23aumh6u8s0i/1gkECMuQGK4txuxZjBGgXM/6c1996d51354190e455ab8f270eea913/results.png)

Note that after running the cell, Jupyter Notebook provided you with a new cell. You can create additional cells by clicking the **+** button in the toolbar.

### Renaming and saving the notebook

Rename the notebook by clicking on its title near the upper left corner of the page. You’ll see the _Rename File_ dialog box. Give the file a suitable name, such as `Image Processing.ipynb` and click the _Rename_ button to make the change:

![Editing the notebook title](https://images.ctfassets.net/23aumh6u8s0i/1N0JG0avYhy6kVyabj1a3l/f634d3c434df9f0d934601366e2b9e09/editing_the_notebook_title.png)

> In case you’re wondering why Jupyter Notebook’s filename extension is `.ipynb`, it’s because it used to be called “IPython Notebook.”
Save the file by clicking the _Save_ icon in the notebook’s toolbar, selecting File → Save in the notebook’s menu bar, or using the control/command-S keyboard shortcut.

### Running a Markdown cell

Cells in Jupyter Notebook are _code cells_ by default. When run, the notebook interprets a code cell’s contents as code, executes that code, and displays any output.

Jupyter Notebook also supports _Markdown cells_, which are for text. When run, the notebook interprets a Markdown cell’s contents as Markdown, converts that Markdown to HTML, and renders the HTML.

Change the newly-created empty cell into a Markdown cell by making sure it’s selected and selecting _Markdown_ from the drop-down menu in the toolbar, as shown below:

![Changing the new cell to Markdown](https://images.ctfassets.net/23aumh6u8s0i/t7TGRAME0BoilbDYpkiaj/83e0254901f62403466d035cc2c8b7cd/change_cell_to_markdown.png)

Enter this into the cell:

```python
# Image Processing

This is a Jupyter Notebook that demonstrates image processing with Pillow.
```

The notebook should look like this:

![Makrdown entered into the new cell](https://images.ctfassets.net/23aumh6u8s0i/5CHyMIQNXcXYJWRVqAozWU/9b4a6120d5979ead6a8fd7935a94787a/markdown_cell_1.png)

Run the cell by either clicking on the _Run_ button in the toolbar or typing _Shift-Enter_. The notebook will render the Markdown into HTML and display it:

![The Markdown cell, rendered](https://images.ctfassets.net/23aumh6u8s0i/5zdqmmdqTcIQUDTdFXlvJk/79ef94c454f00da448df5b73a90cc8db/markdown_cell_2.png)

To edit the Markdown cell, double-click it. The rendered version will be replaced with the editable version.

This ability to hold both code that can be executed and Markdown that can be rendered makes it possible to create documents that can be treated as:

- Code with excellent documentation, and in the spirit of [literate programming](https://thenewstack.io/why-literate-programming-might-help-you-write-better-code), or
- Documents whose theses are proven or backed by code. Economist Paul Romer, who won the 2018 Nobel Prize in economics, [uses Jupyter Notebooks to write research papers](https://paulromer.net/jupyter-mathematica-and-the-future-of-the-research-paper/).

### Installing Pillow using Jupyter Notebook

You could install Pillow like you installed Jupyter Notebook: using `pip` on the command line. But since you’re working in a notebook right now, why not use its shell command capabilities instead?

You can run any command that works in your system’s command line in Jupyter Notebook by adding the `!` character before it. Let’s use this feature to install Pillow from within the notebook.

If you’re on Windows, enter this into a new cell and run it:

```bash
! python -m pip install --upgrade Pillow
```

On macOS and Linux, enter this into a new cell and run it:

```bash
! python3 -m pip install --upgrade Pillow
```