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
On Windows, we will handle the `Anaconda` and `NEURON` installations separately. First, we will install Anaconda following [their recommended instructions](https://docs.anaconda.com/anaconda/install/windows/). Then, we will install NEURON through its own `.exe`. Finally, we will create a `dev` Anaconda environment and install `NetPyNE` within `dev`.

### Installing Anaconda and Running Anaconda
Again, these instructions and images should be the same as found on Anaconda's own installation guide. <br>
1. Download the Windows [Anaconda installer](https://www.anaconda.com) `.exe`<br>
2. Run the installer .exe<br>
3. For the purposes of running `NEURON` and `NetPyNE`, there is no reason to change the initial recommended settings. These include:<br>
    1. Installation for Just Me<br>
    2. Default Path<br>
    3. Create Start Menu Shortcuts, Register Anaconda3 as My Default Python<br>
4. Try running the various Anaconda tools. The `Anaconda Powershell Prompt` will act as our `terminal` on Windows.<br>
![](https://raw.githubusercontent.com/jchen6727/portal/main/images/conda_n.png)

### Installing NEURON
1. Download the Windows [NEURON installer](https://neuron.yale.edu/neuron/download) `.exe`<br>
2. Run the installer .exe<br>
    1. Running the installer will prompt a Windows Defender warning as it is not trusted. You will have to navigate through this warning.<br>
    2. You may wish to change the installation path. For the purposes of running `NEURON` and `NetPyNE` with `Anaconda`, you should select *all* components for install, but at *the minimum* should include:<br>
        1. NEURON X.X.X AMD64<br>
        2. Associate .hoc and .nrnzip<br>
        3. Set DOS environment<br>
3. Test the installation of NEURON by starting the `Anaconda Powershell Prompt` and then running `neuron` and `nrnivmodl` (there won't be anything to compile, but should get the same error warning). Try importing neuron in `ipython`.<br>
![](https://raw.githubusercontent.com/jchen6727/portal/main/images/anaconda_windows.png)

### Setting up a dev Anaconda environment, installing NetPyNE within dev
1. Start the `Anaconda Powershell Prompt`
2. Create a custom Anaconda `dev` environment and `activate` it<br>
    `(base) PS > conda create --name dev --clone base`<br>
    `(base) PS > conda activate dev`<br>
3. Install `NetPyNE` from the Anaconda environment using pip<br>
    `(dev) PS > pip install netpyne`<br>
4. Try importing neuron and netpyne in `ipython` to see if the installation worked:<br>
    `(dev) > ipython -i`<br>
    `>>> from neuron import h`<br>
    `>>> from netpyne import specs`<br>
![](https://raw.githubusercontent.com/jchen6727/portal/main/images/conda_nn.png)

### NOTE: NEURON and Anaconda
In our setup, NEURON and Anaconda are handled separately (instead of handling NEURON as a Python package within an Anaconda environment). We have access to NEURON within the Anaconda prompt through paths configured through the NEURON installer (why Set DOS Environment should be checked)
[](https://raw.githubusercontent.com/jchen6727/portal/main/images/windows_path.png)
