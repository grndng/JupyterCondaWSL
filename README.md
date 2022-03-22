# Installing Jupyter Lab on Windows Subsystem for Linux with Miniconda

## Why?
When working with specific Python packages, especially ones related to geoinformatics like fiona or GDAL, developers on Windows might encounter difficulties during installation. While the installation and bugfixing on Windows sometimes is cumbersome, installing said packages on Linux "just works" - at least from the perspective of the end user. [Windows Subsystem for Linux (WSL)](https://docs.microsoft.com/en-us/windows/wsl/about) allows developers to run a Linux environment on Windows. While most of the time WSL takes place in the [command line interface](https://en.wikipedia.org/wiki/Command-line_interface), there are possibilities to use Linux on Windows from within applications like [Visual Studio Code (VSCode), Git or Docker](https://docs.microsoft.com/en-us/windows/wsl/setup/environment).

If the question is "Why use Jupyter Notebooks or Jupyter Lab at all?", [Packt](https://hub.packtpub.com/10-reasons-data-scientists-love-jupyter-notebooks/
), amongst a lot of other sources, has ten good reasons why.

With this tutorial, we want to take creating a development environment a step further and use [Jupyter Lab](https://jupyter.org/) with [Miniconda](https://docs.conda.io/en/latest/miniconda.html) in WSL in addition to popular applications such as VSCode and Docker!


## Prerequisites
WSL has to be installed (the distribution of your Linux Subsystem should not matter apart from the command to install packages), the [official Documentation](https://docs.microsoft.com/en-us/windows/wsl/install) is very useful!


## Checking and installing Python
Usually Python is installed by default. However, you should check the version with `python --version` in your cli. In case you are on Python 2 (checking the version would return something like `Python 2.7.18`), you should upgrade to Python 3 on your specific distribution (`sudo apt install python3` for Ubuntu, `pacman -S python3` for Arch Linux).

## Installing Miniconda
Since we do not have a GUI at hand, we will not download the installer from the website but do everything from the cli. First we need to get the [shell script](https://www.howtogeek.com/67469/the-beginners-guide-to-shell-scripting-the-basics/) which we have to run in order to install Miniconda:

`sudo wget -c https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh`

Since we want to run it to install Miniconda with that script, we need to make the script "executable". If you type `ls -l` (which stands for "list", the flag "-l" listing the contents in a table format) into your cli, you will see that there are a bunch of letters which are the permissions of each file and directory. [Here](https://open.oregonstate.education/computationalbiology/chapter/permissions-and-executables/) you can learn more about "Permissions and Executables". We make the script executable with the following command:

`sudo chmod +x Miniconda3-latest-Linux-x86_64.sh`

Now we can run the Miniconda installation script with:

`./Miniconda3-latest-Linux-x86_64.sh`

Now you are being greeted with a bunch of text which is the license agreement. Feel free to read it, otherwise use *Enter* or *Space* to skip ahead until you reach the line where you have to agree to the agreement. You have to answer with *yes* to proceed. Afterwards press *Enter* to install Miniconda at the default location. You did it!

## Starting Miniconda and creating an environment (optional)
To start Miniconda, simply type:

`conda activate`

If `(base)` shows up at the beginning of your command line, you have successfully installed and activated Miniconda. The `(base)` tells us that we are in the global scope (or base) of environments.

To deactivate Miniconda (and go back to "normal"), simply type:

`conda deactivate`

which brings us to environments and how to create, activate and deactivate them. To create a new environment (which e.g. might be useful to use different versions of packages), type:

`conda create -n jupyterenv`

which would create a virutal conda environment with the name "jupyterenv". To activate our newly created environment, we would use:

`conda activate jupyterenv`

Now `(jupyterenv)` should show up at the beginning of your command line instead of `(base)`. You can change inbetween environments without without deactivating the current environment first.

With `conda info --envs` you can list the installed environments.

## Installing and using Jupyter Lab
Installing packages with `conda` is as easy as with `pip`: to install a package, in our case the package that will enable us to use Jupyter Lab, we have to type:

`conda install jupyterlab`

This will result in conda listing the packages needed to properly run Jupyter Lab. After we have confirmed the installation dialogue, we can try and start our Jupyter Lab by typing

`juypter lab`

which will result in a dialogue that is supposed to redirect us to a Jupyter application. Since this has never worked for me, we press the buttons `q` (=quit) followed by `y` (=yes) button to quit the dialogue: et voilá, there is our IP to access our Jupyter Lab interface from our webbrowser as we are used to!



## TL;DR
* `sudo apt install python3`
* `sudo wget -c https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh`
* `sudo chmod +x Miniconda3-latest-Linux-x86_64.sh`
* `./Miniconda3-latest-Linux-x86_64.sh`
* Press *Enter* or *Space* until you reach the bottom
* Type `yes`
* Press *Enter*
* Close and re-open the terminal window
* Type `conda activate`
* `(base)` should show at the beginning of the command line
* `conda create -n jupyterenv`
* `conda install jupyterlab`
* Confirm the dialogue
* `jupyter lab`
* `q` `y`
* You're done! :)
