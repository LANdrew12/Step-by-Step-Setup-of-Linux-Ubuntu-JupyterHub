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
