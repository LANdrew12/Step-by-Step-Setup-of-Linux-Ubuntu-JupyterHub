# Step-by-Step-Linux-JupyterHub
This guide is meant to help new users deploy a JupyterHub server for the first time on a brand new computer. It will start from the installation of linux and go to setting up a safe and secure way to access a home based server with remote access. The machine that is being used is a custom built computer and the specs will be listed at the bottom of this guide.

# Setting up Linux for the First Time
Before getting started it is important to know the risks involved in installing Ubuntu on a machine with important data stored on it. It is very easy to delete everything on the computer during this process. It is recommended that everything is backed up prior to continuing. 

# Creating the Ubuntu bootable USB drive
You will need to use a USB storage drive with enough storage to hold the installation of Ubuntu. 
The version of linux that will be installed is Ubuntu 20.04.3 LTS. For information regarding what it is and which one to install consult the Ubuntu website here:
https://ubuntu.com/download/desktop

To create the USB boot media follow the steps shown in the other page on Ubuntu's website here: 
https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview

The instructions for creating the boot media were followed on the website. 

# Installation of Linux/Ubuntu
For our machine, some settings in the BIOS needed to be changed to allow for our system to be a dual boot Windows 11 and Ubuntu machine. The issue ended up being with 'fast boot' and 'secure boot' both were disabled to allow for our particular system to work properly in this configuration. Consult an expert to understand the risks involved with changing BIOS settings before changing these settings. 

Now, to start the insallation you must access the 'BIOS' or the 'boot menu' which can be accessed differently depending on the computer you are working with. For our machine, the 'F2' or 'Delete' button can be used to access the UEFI BIOS during start up. Within the BIOS navigate to the 'boot' tab located at the top of the screen and select the boot media which Ubuntu is installed on. This should be in position number 1 on the order of bootable devices. If the USB drive is not showing up it may first try a different USB or restarting the computer then consult an expert. Also be sure to save the new boot order settings that were just changed prior to exiting the UEFI BIOS to begin the Ubuntu installation. 

Following step 4 and 5 from the Ubuntu website to complete the Ubuntu installation.

With our installation the installation of third party software for graphics and wifi hardware and additional media formats was selected to help with compatibility issues. 

Finally using the updater application to update Linux after the installation of Ubuntu.

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


# Creating the Virtual Environment for JupyterHub

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

# Install Using Pip

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

# Install Packages to Sudo
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

Type:
```sudo python3 -m pip install jupyterlab-system-monitor```
and press 'enter'.

Type:
```sudo apt install nodejs npm```
and press 'enter' and then type ```y``` and press 'enter'.

Type:
```sudo npm install -g configuratble-http-proxy```
and press 'enter'.

# Create a Configuration File
To create a configuration file type:
```sudo jupyterhub --generate-config```
and press 'enter'.

Now that we have a configuration file the next step is opening it and editing it. 
To access it we will use 'gedit' but 'nano' is also a good way to edit the config file.

To edit the file type:
```sudo gedit jupyterhub_config.py```
and press 'enter' the type your computers password and press 'enter' (the password will not show up this is normal).

This should open a text file with a configuration settings that can be changed. 
Navigate to " c.Spawner.default_url = '' "
First delete the '#' symbol at the front of the code and change it to ```c.Spawner.default_url = '/lab'```

Navigate to " c.JupyterHub.spawner_class = 'localprocess' "
First delete the '#' symbol at the front of the code and change it to ```c.JupyterHub.spawner_class = 'systemdspawner.SystemdSpawner'```


Navigate to " c.Jupyterhub.shutdown_on_logout = False "
First delete the '#' symbol at the front of the code and change it to ```c.Jupyterhub.shutdown_on_logout = True```

# (Work In Progress) Creating self assigned ssl-certs
Type:
```sudo mkdir /opt/jupyterhub/ssl-certs```
and press 'enter' the type your computers password and press 'enter' (the password will not show up this is normal).

########
Cd /opt/jupyterhub/ssl-certs
sudo openssl req -x509 -nodes -days 3650 -newkey rsa:2048 -keyout /opt/jupyterhub/ssl-certs/jhub.key -out /opt/jupyterhub/ssl-certs/jhub.crt



# (Work In Progress) Change the default ssl_cert and ssl_key In the jupyterhub_config file
c.JupyterHub.ssl_cert = ‘/opt/jupyterhub/ssl-certs/jhub.crt’
c.JupyterHub.ssl_key = ‘/opt/jupyterhub/ssl-certs/jhub.key’

# Starting JupyterHub from the Terminal
Type:
```sudo jupyterhub```
and press 'enter' the type your computers password and press 'enter' (the password will not show up this is normal).

Open a 'Firefox" browser window and type in the url bar at the top:
```localhost:8000```
and press 'enter' 

The username and password will be the same as the account you are logged into. 

To close the JupyterHub select the terminal window it is running in and press and hold 'control' and 'c' at the same time.



#### list specs ####
