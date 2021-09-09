# Jupyter Notebooks

## Getting started with Jupyter Notebooks

1. On the menu bar, click `Interactive Apps` and select the Jupyter app for your class. For example, if your class is CS109a, select `Jupyter Notebook - CS109a`. You can also select your app from the dashboard page.<br/>
![Select-jupyter-app screenshot](images/jupyter/select-jupyter-app.png?raw=true)

2. On the following page, in `Allocated Time`, enter the approximate number of hours for which you would like to run your server. For example, for a 4 hour session, enter `04:00:00`. Afterwards, click `Launch`.<br/>
![Launch-jupyter-server screenshot](images/jupyter/launch-jupyter-server.png?raw=true)

3. On the page that follows, click `Connect to Jupyter`. A new browser tab containing the Jupyter notebooks interface will open.<br/>
![Connect-to-jupyter screenshot](images/jupyter/connect-to-jupyter.png?raw=true)

4. Select the jupyter kernel you want. For example, to start a notebook with the Python 3 jupyter kernel, click `New` then `Python 3`.<br/>
![Select-python-3-kernel screenshot](images/jupyter/select-python-3-kernel.png?raw=true)

## How to install python packages

It is probable that the package you need is already pre-installed and that you can import it in your notebooks with `import packagename`. If that is not the case, below are the steps to install a python package.

1. From the jupyter notebooks interface, click `New` then `Terminal`. A terminal will open in a new browser tab.<br/>
![Open-a-terminal screenshot](images/jupyter/open-a-terminal.png?raw=true)

2. In the Terminal, run `pip install --user packagename`, replacing `packagename` with the python package you intend to install. E.g:<br/>
![Install-python-package screenshot](images/jupyter/install-python-package.png?raw=true)