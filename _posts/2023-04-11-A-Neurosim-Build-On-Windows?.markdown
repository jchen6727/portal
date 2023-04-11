---
layout: post
title:  "A Neurosim Build Using Windows?"
date:   2023-04-11 11:09:44 -0400
categories: Windows NEURON NetPyNE Python
---

The use case for installing NEURON and NetPyNE *directly* onto your Windows OS, as opposed to through WSL is *extremely limited*. These instructions are therefore *not recommended* as a first option

For the purpose of NetPyNE development. I am writing end-to-end development walkthroughs, including this NEURON + NetPyNE Windows installation use case (not preferred)

## Links
*Preferred installation method for Windows (through WSL)*<br>
(via) [https://jchen6727.github.io/portal/](https://jchen6727.github.io/portal/wsl/neuron/netpyne/python/2022/10/31/A-Neurosim-Build-Using-Windows-Subsystem-Linux!.html)<br>
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

## Steps
On Windows, we will handle the `Anaconda` and `NEURON` installations separately. First, we will install Anaconda following [their recommended instructions](https://docs.anaconda.com/anaconda/install/windows/).

### Installing Anaconda and Running Anaconda
Again, these instructions and images should be the same as found on Anaconda's own installation guide. <br>
1. Download the Windows [Anaconda installer](https://www.anaconda.com) `.exe`
2. Run the installer .exe
3. For the purposes of running `NEURON` and `NetPyNE`, there is no reason to change the initial recommended settings. These include:
    1. Installation for Just Me
    2. Default Path
    3. Create Start Menu Shortcuts, Register Anaconda3 as My Default Python

### Installing NEURON
1. Download the Windows [NEURON installer](https://neuron.yale.edu/neuron/download) `.exe`
2. Run the installer .exe
    1. Running the installer will prompt a Windows Defender warning as it is not trusted. You will have to navigate through this warning.
    2. You may wish to change the installation path. For the purposes of running `NEURON` and `NetPyNE` with `Anaconda`, you should select *all* components for install, but at *the minimum* should include:
        1. NEURON X.X.X AMD64
        2. Associate .hoc and .nrnzip
        3. Set DOS environment
3. The installer will set (if set DOS environment is checked) the appropriate paths to run the NEURON toolkit. This includes  
