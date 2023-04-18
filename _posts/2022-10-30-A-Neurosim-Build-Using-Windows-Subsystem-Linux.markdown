---
layout: post
title:  "A Neurosim Build Using Windows Subsystem Linux"
date:   2022-10-30 21:05:44 -0400
categories: Windows WSL NEURON NetPyNE Python
---
Windows Subsystem Linux is a powerful tool that allows developers on Windows to run a GNU/Linux environment directly on Windows, unmodified, without requiring the overhead of traditional VM or dualboot setup.
If you are a traditional Windows User who is interested in learning GNU/Linux, WSL can serves as a very easy first step--letting you keep the creature comforts of Microsoft while also giving you the ability to develop in a highly versatile and popular OS.

For the purpose of NetPyNE development. I am writing end-to-end development walkthroughs, including this starting intro to running NetPyNE on Windows through WSL (preferred). 

## Links
Anaconda<br>
[https://www.anaconda.com](https://www.anaconda.com)<br>
GitHub<br>
[https://github.com](https://github.com)<br>
Jupyter<br>
[https://jupyter.org](https://jupyter.org)<br>
NetPyNE<br>
[http://www.netpyne.org](http://www.netpyne.org)<br>
NEURON<br>
[https://neuron.yale.edu/neuron/](https://neuron.yale.edu/neuron/)<br>
Windows Subsystem Linux<br>
[https://docs.microsoft.com/en-us/windows/wsl/](https://docs.microsoft.com/en-us/windows/wsl/)<br>

## Steps
First we will set up `WSL` through `Windows PowerShell`. By default, the `WSL` setup will install `Ubuntu` as a subsystem. Then, we will install `Anaconda` onto the Ubuntu subsystem, configure an Anaconda environment `dev`, and install `NEURON` and `NetPyNE` in that environment.

### How to set up your Virtual Machine
1. Run Windows PowerShell as administrator
![](https://raw.githubusercontent.com/jchen6727/portal/main/images/powershell_as_admin.png)
2. Use Windows PowerShell to install Linux with `wsl --install`
![](https://raw.githubusercontent.com/jchen6727/portal/main/images/wsl_install.png)
3. Reboot your system
4. The Ubuntu subsystem will now be accessible as an app in windows.
![](https://raw.githubusercontent.com/jchen6727/portal/main/images/ubuntu.png)![](https://raw.githubusercontent.com/jchen6727/portal/main/images/ubuntu_startup.png)
You now have access to your subsystem Linux, create your profile username and password through the terminal.<br>

### NOTE: Password
The password you entered will be used for any commands requiring `admin` access in Linux. You won't see any characters or placeholders when you type it.
### NOTE: Accessing your Windows/Linux files
Within your linux subsystem, you can access your Windows files under the directory `/mnt`. You can change to this directory with command `cd /mnt` from the Ubuntu  <br>
Within your Windows machine, you can access your Linux files under the directory `\\wsl$`. By opening File Explorer, you can view all files in your linux subsystem by replacing the entry in the left navigation bar with `\\wsl$`<br>
![](https://raw.githubusercontent.com/jchen6727/portal/main/images/file_access.png)

### Setting up your Python environment - Anaconda installation, 
1. Get the Linux Anaconda Installer (likely the x86_64) from the [Anaconda site](https://www.anaconda.com/products/distribution#Downloads)
2. On Windows, open the File Explorer
3. In the Windows File Explorer search bar navigate to your `Ubuntu\tmp` directory:<br>
    `\\wsl$\Ubuntu\tmp`<br>
4. Move your Linux Anaconda Installer (the file just downloaded with the extension `.sh`) to your Ubuntu\tmp directory<br>
5. On Windows, open Ubuntu to start your Linux subsystem.<br>
6. In your Linux subsystem perform the following steps:<br>
7. Navigate to your tmp directory using the `c`hange `d`irectory command:<br>
    `$ cd /tmp`<br>
8. run the `bash` shell script with the following command:<br>
    `$ bash Anaconda3-xxxx.xx-Linux-xxxxxx.sh`<br>
    where `-xxxx.xx-Linux-xxxxxx` is the specific release number and architecture specified by your download<br>
    the shell supports autocomplete, so you can autocomplete the line by typing `bash Anaconda3` then hitting the Tab key<br>
    type `yes` when prompted by the installer<br>
9. The Anaconda3 shell script will modify your startup `.bashrc`, `source` your `.bashrc` with the following command:<br>
    `$ source ~/.bashrc`<br>
10. Create a custom Anaconda `dev` environment and `activate` it<br>
    `(base) $ conda create --name dev --clone base`<br>
    `(base) $ conda activate dev`<br>
11. Optional: set up your shell by appending the activation command to your startup `.bashrc` so that it automatically moves to the `dev` environment on startup<br>
    `(dev) $ echo "conda activate dev" >> ~/.bashrc`<br>
12. Install NEURON and NetPyNE from the Linux subsytem shell with Python's built-in installer `pip`:<br>
    `(dev) $ pip install neuron` <br>
    `(dev) $ pip install netpyne`<br>
13. Try importing neuron and netpyne in `ipython` to see if the installation worked:<br>
    `(dev) $ ipython -i`
    `>>> from neuron import h`<br>
    `>>> from netpyne import specs`<br>
![](https://raw.githubusercontent.com/jchen6727/portal/main/images/python_imports.png)

You now are running NetPyNE and NEURON on your subsystem Linux<br>
### NOTE: Instruction Set Architecture
The multiple Linux installers available point to different shell scripts and repositories depending on your instruction set architecture.<br> 
unless you are using a supercomputer, a server mainframe, or an embedded system, it should be `x86_64`<br>
### NOTE: Anaconda environments
Anaconda environments help encapsulate Python programming environments--this is useful if you want to work on projects with different packages / libraries.<br>
In this case, we are cloning the `base` environment into a `dev` environment. <br>
When something breaks in this environment, we can simply remove the encapsulated environment and recreate it with `conda` commands. <br>
Whereas if we accidentally corrupted the `base` environment, we may have to fix everything within Anaconda. <br>
Make sure that you are in the correct Anaconda environment before running any Python package commands 
