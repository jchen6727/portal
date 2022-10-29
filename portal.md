# Welcome to my Homepage!

> Programming Guides for Computational Neuroscience, Journaling, etc.
#%% md
## Stuff I'm Working On

1. An end-to-end tutorial for getting a "neurosim" environment (Linux VM + NEURON + Anaconda) running [here](https://jchen6727.github.io/tut0/)
2. A tutorial for converting older code into NEURON+Python+NetPyNE [here](https://jchen6727.github.io/tut1/)
3. My single cell characterization and optimization scripts are still a [WIP](https://jchen6727.github.io)

## My Journaling

1. I follow myself on Twitter [here](https://twitter.com/dontwgetshme) and my favorite Twitter users are [here](https://twitter.com/i/lists/1559340183169949697)
[![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/dontwgetshme.svg?style=social&label=Follow%20%40dontwgetshme)](https://twitter.com/dontwgetshme)<br>
2. My longer journal entries still a [WIP](https://jchen6727.github.io)

# tut0

> Creating a NEURON+NetPyNE project with Jupyter & Google Colab on GitHub
#%% md
## Nota Bene
The suggestions contained herein will be at least X days out of date, depending on when the last push was. Maybe this will cause headaches or scary things.
However, at the time of the last push, at least one person thought that the steps below were improved enough from prior documented knowledge that they thought it worthwile to update the repo.

This work is licensed under the Creative Commons Attribution 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.

## Links
Anaconda<br>
[https://www.anaconda.com](https://www.anaconda.com)<br>
GitHub<br>
[https://github.com](https://github.com)<br>
Jupyter<br>
[https://jupyter.org](https://jupyter.org)<br>
nbdev<br>
[https://nbdev.fast.ai](https://nbdev.fast.ai)<br>
NetPyNE<br>
[http://www.netpyne.org](http://www.netpyne.org)<br>
NEURON<br>
[https://neuron.yale.edu/neuron/](https://neuron.yale.edu/neuron/)<br>
Windows Subsystem Linux<br>
[https://docs.microsoft.com/en-us/windows/wsl/](https://docs.microsoft.com/en-us/windows/wsl/)<br>

## Steps

### How to set up your Virtual Machine
1. Start Windows PowerShell as an administrator
2. Use Windows PowerShell to install Linux<br>
    `wsl --install`<br>
3. Reboot your system
4. Start Ubuntu on Windows<br>
Thats it! You now have access to your Linux VM through Ubuntu on Windows, go celebrate!<br>

### NOTE: Running Linux VM as an administrator, or use sudo within your VM
Sometimes you may run into permission errors due to permission rights within your Linux VM.<br>
Ssing `sudo` before the command to resolve the issue, if that does not work<br>
Try starting Ubuntu as an administrator and executing the command, it may resolve the issue<br>

### NOTE: Accessing your Windows/Linux files
Within your Linux VM, you can access your Windows files under the directory `/mnt`<br>
Within your Windows machine, you can access your Linux files under the directory `\\wsl$`<br>

### Setting up your Python environment - Anaconda installation, 
1. Get the Linux Anaconda Installer here: https://www.anaconda.com/
2. Open your file explorer
3. In the file explorer search bar navigate to:<br>
    `\\wsl$\Ubuntu\tmp`<br>
4. Move your Linux Anaconda Installer to your Ubuntu\tmp directory
5. Start Ubuntu on Windows
6. In your Linux VM perform the following steps:
7. Navigate to your tmp directory using:<br>
    `cd /tmp`<br>
8. bash Anaconda3-xxxx.xx-Linux-x86_64.sh<br>
    you can autocomplete the line by using the Tab button<br>
9. Restart your Linux VM shell with:<br>
    `source ~/.bashrc`<br>
10. Install NEURON and NetPyNE with Python's built-in installer:<br>
    `pip install neuron` <br>
    `pip install netpyne`<br>
11. Run Python
12. Execute the following lines of code:
    `from neuron import h`<br>
    `from netpyne import specs`<br>
Thats it! You now are running NetPyNE and NEURON on your Linux VM<br>

### Compiling a custom cell using nrnivmodl
### The nbdev sequence
1. After cloning your repository initialise it as an nbdev repo<br>
    `nbdev_new`<br>
2. Install the nbdev hooks<br>
    `nbdev_install_hooks`<br>
3. View your site in your web-browser<br>
    `nbdev_preview`<br>
4. 00_core.ipynb
5. index.ipynb
6. Before pushing your repository prepare your site:<br>
    `nbdev_prepare`<br>
7. your site will be on<br>
    `https://{user}.github.io/{repo}`

### Installing pandocs on your Linux VM
You can install pandocs with the following commands:<br>
1. navigate to an appropriate repository to store your pandocs installer:<br>
`cd /home/<user>`<br>
2. get the linux installer
`wget https://github.com/jgm/pandoc/releases/download/<ver>/pandoc-<ver>-<architecture>.deb`<br>
3. use the installer (requires administrator rights)
`sudo dpkg -i pandoc-<ver>-<architecture>.deb`<br>
4. remove the linux installer
`rm pandoc-<ver>-<architecture>.deb`<br>





