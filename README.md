# Step-by-step-Linux-JupyterHub
This guide is meant to help new users deploy a JupyterHub server for the first time on a brand new machine. It will start from the installation of linux and go to setting up a safe and secure way to set up a home based server with remote access. The machine that is being used is a custom built computer and the specs will be listed at the bottom of this guide.

# Setting up Linux for the first time
Before getting started it is important to know the risks involved in a venture like this. Make sure all data is backed up on a separate device if it is important. 

# Creating the Ubuntu bootable USB drive
You will need to use a USB storage drive with enough storage to hold the installation of Ubuntu. 
The version of linux that will be installed is Ubuntu 20.04.3 LTS. For information regarding what it is and which one to install consult the Ubuntu website here:
https://ubuntu.com/download/desktop

To create the USB boot media follow the steps shown in the other page on Ubuntu's website here: 
https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview

The instructions for creating the boot media were followed on the website. 

# Installation of Ubuntu to the desired machine
For our machine, some settings in the BIOS were to be changed to allow for our system dual boot Windows 11 and Ubuntu. The issues we had were with fast boot and secure boot both were disabled to allow for our particular system to work properly in this configuration. Consult an expert to understand the risks involved with changing BIOS settings before changing settings. 

Now, to start the insallation you must access the BIOS or the boot menu which is accessed differently depending on the model. For our machine, the 'F2' or 'Delete' button can be used to access the UEFI BIOS and the 'Boot' tab can be found to select the newly created Ubuntu bootable USB drive. This should be in position number 1 on the order of bootable devices. If the USB drive is not showing up it may first try a different USB or restarting the computer then consult an expert. Also be sure to save the new boot order settings that were just changed prior to exiting the UEFI BIOS to begin the Ubuntu installation. 

Following step 4 and 5 from the Ubuntu website to complete the Ubuntu installation.

With our installation the installation of third party software for graphics and wifi hardware and additional media formats was selected to help with compatibility issues. 

Finally using the updater all software updates were installed.

#####################


# Setting up JupyterHub
# Installing Anaconda
First open terminal and type:
```cd ~```
and press 'enter'.

Then type:
```mkdir tmp```
and press 'enter'.

Then type:
```cd tmp```
and press 'enter'.

Now open firefox and go to anaconda: https://www.anaconda.com/products/individual

At the bottom of the page there is a clickable link that says: '64-Bit (x86) Installer (581 MB)' right click this link and click 'copy link address'

Back in the terminal type:
```wget https://repo.anaconda.com/archive/Anaconda3-2021.11-Linux-x86_64.sh```
(but instead of the URL here right click and click paste the URL you just copied with a space just after the wget. This will just ensure that the most up to date version of anaconda is installed.)
Press 'enter'

Next type:
```ls```
and press 'enter'.

The output should look something like:
'Anaconda3-2021.11-Linux-x86_64.sh'.

To finish the install of Anaconda type:
```bash Anaconda3-2021.11-Linux-x86_64.sh```
Except replace the 'Anaconda3-2021.11-Linux-x86_64.sh' with the output from the last code.

Now press 'enter' and keep pressing it until 'more' goes away at the bottom of the terminal and type 'yes' if you agree and finally 'yes' one more time. This will finish the installation of Anaconda. 

Now type:
```cd ~```
and press 'enter'.

Verify that conda is installed by typing:
```source .bashrc```
and pressing 'enter'.

This should say base on the left of the screen.

Then type:
```conda --version```
and press 'enter'. 

This should say 'conda' followed by the version you installed. 


# Creating the virtual environment for JupyterHub

To create the virtual environment to use JupyterHub type:
```conda create -n jhub python==3.8```
and press 'enter'.
type: 
```y```
and press 'enter'.

To enter the virtual environment type:
```conda activate jhub```
and press 'enter'. 

This should now have 'jhub' off to the left instead of 'base' from earlier.


# Install JupyterHub
Next, install JupyterHub by typing:
```conda install -c conda-forge jupyterhub```
and press 'enter'.

Type:
```y```
and press 'enter'.

And, type:
```conda install -c conda-forge jupyterlab```
and press 'enter'.

Type:
```y```
and press 'enter'.

# Installs using pip

Type:
```pip install Jupyterhub-systemdspawner```
and press 'enter'.

Type:
```pip install psutil```
and press 'enter'.

Now that the those are installed, create a place for the condifuration files by typing:
```sudo mkdir /opt/jupyterhub```
and press 'enter' the type your computers password and press 'enter' (the password will not show up this is normal).

Staying within the same environment type:
```sudo python3 -m pip install jupyterlab```
and press 'enter'.

Then type:
```sudo python3 -m pip install jupyterhub```
and press 'enter'.

Next type:
```sudo python3 -m pip install psutil```
and press 'enter'.

# Install packages to sudo
Type:
```sudo apt-get install python3```
and press 'enter'.

Type:
```sudo apt-get install python3-pip```
and press 'enter'.

Then type ```y``` and press 'enter'.

Type:
```sudo python3 -m pip install jupyterlab```
and press 'enter'.

Type:
```sudo python3 -m pip install jupyterhub```
and press 'enter'.

Type:
```sudo python3 -m pip install psutil```
and press 'enter'.

Type:
```sudo python3 -m pip install jupyterhub-systemdspawner```
and press 'enter'.



#####################
# Setting up JupyterHub
To install JupyterHub (JH), Python 3 must be installed first. 
# Installing Python 3
To install python first check if it is already installed by opening the terminal and type:
```python3 --version```
Followed by pressing 'enter'.
Then type:
```sudo apt update```
Followed by pressing 'enter'.

If it says which version you have that means the next python install steps can be skipped.

If there is no version then type:
```sudo apt install python3.8```
Then press 'enter' and type password in (password wont show up for linux terminal) and press 'enter' again. 

Now check the version of python installed by typing:
```python3 --version```
Followed by pressing 'enter'.



#########should this be done prior to installing python and then use anaconda to install python?############
# Installing Anaconda
Follow the guide here to install Anaconda:
https://phoenixnap.com/kb/how-to-install-anaconda-ubuntu-18-04-or-20-04

# Installing JupyterHub
To install JH follow the guide here:
https://jupyterhub.readthedocs.io/en/stable/quickstart.html






#### list specs and versions ####
