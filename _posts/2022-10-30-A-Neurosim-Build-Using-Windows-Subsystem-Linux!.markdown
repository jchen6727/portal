---
layout: post
title:  "A Neurosim Build Using Windows Subsystem Linux!"
date:   2022-10-30 21:05:44 -0400
categories: WSL NEURON NetPyNE Python
---
Windows Subsystem Linux is a powerful tool that allows developers on Windows to run a GNU/Linux environment directly on Windows, unmodified, without requiring the overhead of traditional VM or dualboot setup. 
If you are a traditional Windows User who is interested in learning GNU/Linux, WSL can serves as a very easy first step--letting you keep the creature comforts of working with Microsoft development tools while also giving you the ability to work with the a highly versatile and popular (i.e. documented) OS used in development.

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

### How to set up your Virtual Machine
1. Start Windows PowerShell as an administrator
2. Use Windows PowerShell to install Linux with `wsl --install`
![](https://github.com/jchen6727/portal/blob/main/images/wsl_install.png)
3. Reboot your system
4. The Ubuntu subsystem will now be accessible as an app in windows.
![](https://github.com/jchen6727/portal/blob/main/images/ubuntu.png)![](https://github.com/jchen6727/portal/blob/main/images/ubuntu_startup.png)
Thats it! You now have access to your subsystem Linux, create your profile username and password through the terminal.<br>

### NOTE: Accessing your Windows/Linux files
Within your linux subsystem, you can access your Windows files under the directory `/mnt`. You can change to this directory with command `cd /mnt` from the Ubuntu  <br>
Within your Windows machine, you can access your Linux files under the directory `\\wsl$`. By opening File Explorer, you can view all files in your linux subsystem by replacing the entry in the left navigation bar with `\\wsl$`<br>
![](https://github.com/jchen6727/portal/blob/main/images/file_access.png)

### Setting up your Python environment - Anaconda installation, 
1. Get the Linux Anaconda Installer here: https://www.anaconda.com/
2. Open your file explorer
3. In the file explorer search bar navigate to:<br>
    `\\wsl$\Ubuntu\tmp`<br>
4. Move your Linux Anaconda Installer to your Ubuntu\tmp directory
5. Start Ubuntu on Windows
6. In your Linux subsystem perform the following steps:
7. Navigate to your tmp directory using:<br>
    `$ cd /tmp`<br>
8. run the shell script with the following command:<br>
    `$ bash Anaconda3-xxxx.xx-Linux-x86_64.sh`<br>
    you can autocomplete the line by using the Tab button<br>
    type `yes` when prompted by the installer<br>
9. Restart your Linux subsystem shell with:<br>
    `$ source ~/.bashrc`<br>
10. Create a custom Anaconda `dev` environment and move to this environment<br>
    `$ conda create --name dev --clone base`<br>
    `$ conda active dev`<br>
11. Set up your shell so that it automatically moves to the `dev` environment on startub<br>
    `$ echo "echo "conda activate dev" >> ~/.bashrc`<br>
12. Install NEURON and NetPyNE from the Linux subsytem shell with Python's built-in installer `pip`:<br>
13. Create a custom anaconda environment using 
    `$ pip install neuron` <br>
    `$ pip install netpyne`<br>
14. Run Python
15. Execute the following lines of code to see if the imports are correct:<br>
![](https://github.com/jchen6727/portal/blob/main/images/python_imports.png)
    `>>> from neuron import h`<br>
    `>>> from netpyne import specs`<br>
Thats it! You now are running NetPyNE and NEURON on your subsystem Linux<br>

### NOTE: Anaconda environments
Anaconda environments help encapsulate Python programming environments--this is useful if you want to work on projects with different packages / libraries.<br>
In this case, we are cloning the `base` environment into a `dev` environment. <br>
When something breaks in this environment, we can simply remove the encapsulated environment and recreate it with `conda` commands. <br>
Whereas if we accidentally corrupted the `base` environment, we may have to fix everything within Anaconda. <br>