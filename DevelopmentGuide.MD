# DEVELOPMENT GUIDE #

## Basic Usage ##
STUPIDPIXHAWK is for helping stupid people to use pixhawk as a platform for whatever usage. Simplily try to follow this guide. If you are having trouble understanding or implementing our document, it probably means that your intellengence is below average and do not hesitage to call us at +86 wsbwsbwsbbwsb or email me at wsbking@wsb.com.



# STEP 1: Set up the environment ##

We recommend debian-based linux system. 

*   **SSR**  
    Set up electron-SSR and configure your proxy setting, make sure your http proxy is set at port 12333.

*    **System Network Setting**  
    1. Go to Setting-Network-Network Proxy
    2. select Manual
    3.  HTTP Proxy: http://127.0.0.1, Port: 12333
        HTTPS Proxy: https://127.0.0.1, Port: 12333
        Socks Host: 127.0.0.1, Port: 1080

*    **Firefox**  
    1. Go to Preference-General-Network Setting
    2. Select Use system proxy settings

## 1. Install Git:


```sh
$ sudo apt-get update
$ sudo apt-get install git
```  
Verify the installation by typing the following command and it will grant you the git version.  
```sh
$ git --version
```
Now you have successfully installed git.  
  
(optional) Then it is probably a good idea to install git GUI client if you are not familar with command-line.
*   **Install GitKraken**
    1. Go to https://www.gitkraken.com/download, and choose Linux(.deb) to download.
    2. Open download folder and double click.
    3. Install.

## 2. Clone the Repository
Now that you have install git. We need to "download" our source code.  
*   **Apply proxy for git to fasten the clone speed.**  
    1. Open terminal.
    2. type in:  
    ```sh
    $ git --config http.proxy http://127.0.0.1:12333
    % git --config https.proxy https://127.0.0.1:12333
    ```  
    The clone speech should be over 1MB/s. Check this step if it is taking more than it should to clone the repository.  

Enter desired destition (We will use the Document folder as an example), and clone by using the following command:
```sh
$ git clone https://github.com/supericx/ardupilot
```  
Upon completion, check if there is a folder named "arudupilot" in your destination.

## 3. (Optional) Change the Submodule update link
If you clone the original source code from ardupilot, you need to edit the .gitmodule file to incrase the speed of cloning submodules that ardupilot depends on.  

If you are using github.com/supericx/ardupilot, then skip this step.  

1. Go to ardupilot folder and edit .gitmodules with whatever editor. 
2. Change all the "git://github.com" to "http://github.com"

Example:  
    
* original code:
```
[submodule "modules/uavcan"]
	path = modules/uavcan
	url = git://github.com/ArduPilot/uavcan.git
```

* edited code:
```
[submodule "modules/uavcan"]
	path = modules/uavcan
	url = http://github.com/ArduPilot/uavcan.git
```

## 4. Update Submodules  
the ardupilot depends on serveal other modoles to work, so during this step you will download all the required submodules and they will be located in the ardupilot/module folder

1. Run the following command line:
```sh
git submodule update --init --recursive
```
2. If the speed is too slow or it is not connecting to the server, please see the "Change the submodule update link", and make sure everything is done correctly.

## 5. D