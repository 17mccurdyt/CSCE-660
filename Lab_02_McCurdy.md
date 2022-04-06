# Lab 2: Hardware Setup
## Objective:  	
* Prepare your environment to support completing the CSCE660 Labs
* Gain root level access to the phone and connect to it over Android Debug Bridge (ADB) shell
* Connect frida client to frida server on the phone over ADB

## References: 	
1. https://www.xda-developers.com/how-to-install-magisk/  
1. https://magisk.me/  
1. https://developers.google.com/android/images
1. https://github.com/M0Rf30/android-udev-rules.git  
1. https://frida.re/  
1. https://ubuntu.com/  
1. https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html
1. https://developer.android.com/studio/install  
1. https://github.com/skylot/jadx  
1. https://github.com/Genymobile/scrcpy
1. https://docs.microsoft.com/en-us/windows/wsl/connect-usb  
1. https://docs.microsoft.com/en-us/windows/wsl/install

## Instructions: 
* Type the answers to the questions using either latex or markdown.  If you get help from other sources, cite your sources at the end in works cited / bibliography (IEEE style).  
* Compress all supporting documentation used to generate the pdf (.md, .tex files, images, etc.) into a file named "lab_02_lastname.zip".  Include a text file with the commands and any additional steps you used to generate the .pdf.  Submit the compressed file through the MS Teams Assignment.  

## Tasks
*NOTE: You may configure WSL with the Ubuntu 20.04 kernel.  This will negate the need to install vmware workstation.  This means you may follow either the VMWare Tasks or the WSL2 Tasks, not both. You may also just do this from a host with ubuntu 20.04 as the primary operating system.

###	Workstation Tasks 
1. Fully updated Windows.  Recommend moving to Windows 11.

#### VMWare Tasks

1. Install VMWare Workstation
Configure Ubuntu 20.0.4 in vmware workstation.  
    * pre-allocate 40GB HDD space
    * 8GB RAM
    * Check Virtualize Intel VT-x/EPT or AMD-V/RVI to support android emulator
    * Ensure support for USB 3.1  
    * *NOTE: Check .vmx file for usb.restrictions.defaultAllow = "TRUE"...ensure it is set to True or else you cannot access USB devices from the guest VM*  
1. Install Android Studio 
    * install SDK-tools through the SDK Manager
1. Update the USB driver to _Android Bootloader Interface_
    * Device Manager -> right click on Pixel 4 -> General -> Update Driver -> Browse my computer for driver software -> Next  

#### WSL2 Tasks
1. Follow direcitons to install WSL2 w/ Ubuntu 20.04 distro as kernel: https://docs.microsoft.com/en-us/windows/wsl/install
1. Install Android Studio 
    * install SDK-tools through the SDK Manager
1. Update the USB driver to _Android Bootloader Interface_
    * Device Manager -> right click on Pixel 4 -> General -> Update Driver -> Browse my computer for driver software -> Next  
1. Update and upgrade ubuntu 
1. Follow directions to pass through USB to the WSL2 kernel:  
https://docs.microsoft.com/en-us/windows/wsl/connect-usb

### "Virtual" Machine Tasks
1. Update and upgrade ubuntu 
1. Install open-jdk (i.e., default-jdk)
    ```console
    $ sudo apt install default-jdk -y 
    ```
1. Install conda on Linux.  
    ```console
    $ curl -O https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh
    $ bash Anaconda3-2019.03-Linux-x86_64.sh
    $ conda update conda
    ```
1. Create a python3 environment in conda
1. Install Frida via conda
    ```console
    (base) user@ubuntu:~$ conda activate android_app_analysis
    (android_app_analysis) user@ubuntu:~$ conda activate android_app_analysis
    (android_app_analysis) user@ubuntu:~$ pip install Frida
    (android_app_analysis) user@ubuntu:~$ pip install Frida-tools
    ```
1. Create a python3 environment in conda
1. Build and install Jadx from source
1. Install Android Studio with Android development tools 
1. Configure Ubuntu PATH to use the Android build-tools (NDK), platform-tools (adb, fastboot).   Suggest editng the ~\\.bashrc file to something like this:
    ```console
    export ANDROID_NDK_ROOT=~/Android/Sdk/ndk/21.0.6113669/ 
    export PATH=$PATH:$ANDROID_NDK_ROOT 
    export ANDROID_SDK_ROOT=/home/user/Android/Sdk 
    export PATH=$PATH:$ANDROID_SDK_ROOT 
    export ANDROID_PLATFORM_TOOLS_ROOT=/home/user/Android/Sdk/platform-tools 
    export PATH=$PATH:$ANDROID_PLATFORM_TOOLS_ROOT 
    export ANDROID_BUILD_TOOLS=/home/user/Android/Sdk/build-tools/29.0.2 
    export PATH=$PATH:$ANDROID_BUILD_TOOLS 
    $ source ~/.bashrc
    ```

1. Install scrcpy

1. Update *udev* rules 
    ```console
    $ git clone https://github.com/M0Rf30/android-udev-rules.git  
    $ cd android-udev-rules  
    $ sudo chmod a+r /etc/udev/rules.d/51-android.rules
    $ sudo cp android-udev.conf /usr/lib/sysusers.d/
    $ sudo systemd-sysusers
    $ sudo gpasswd -a $(whoami) adbusers
    $ sudo service udev restart
    $ sudo service udev restart
    ```

##	Phone Tasks
1. Return your phone to factory settings
2. Become a developer  
3. Enable USB debugging  
4. Root your phone using Magisk & Magisk Manager  
*Note this may require you to use fastboot.  I have yet to get fastboot to work from WSL2 and sometimes there are issues from the ubuntu vm.  Suggest flashing any firmware directly from the host workstation.  
5. Install Frida server on the phone (something like this)  
    ```console
    (android_app_analysis) user@ubuntu:~$ unxz frida-server-12.8.14-android-arm64.xz
    (android_app_analysis) user@ubuntu:~$ adb push frida-server-12.8.14-android-arm64 /data/local/tmp
    (android_app_analysis) user@ubuntu:~$ adb shell "chmod 755 /data/local/tmp/frida-server-12.8.14-android-arm64"
    ```
6. Check _don’t auto-update apps_ in Google play settings and verify Google Play is certified  
7. Uncheck _Automatic system updates_ under Developer options  
8. Set up your phone with a new profile (i.e., email account, Wi-Fi, etc.)  
9. Install a few apps on it (such as Discord)  
10. Set up a profile on Discord and send/receive some texts to a partner

##	HILICS Tasks 

You can use the HILICS kit in one of two different configurations: 1) local Ethernet connection, OR 2) WiFi/remote connection. Both will require simple modifications to the Raspberry Pi. 

* **If you run into trouble, check these docs:**

    * https://github.com/dillrich/22SP_CSCE660/tree/main/hilics_docs
    
    * https://github.com/sdunlap-afit/hilics/tree/master/docs


* **Display config:**

    1. Plug a USB keyboard into the Raspberry Pi (port is on the side of the touch-screen).

    1. Open a terminal and use `vim.tiny` or `nano` to modify `~/start.sh`
    
        `nano ~/start.sh`

    1. The following line dictates which interface the GUI is displayed on. 

        `export DISPLAY=:0` - Display 0 is the touch-screen. Use this display for local Ethernet access.

        `export DISPLAY=:2` - Display 2 is the NoVNC server. Use this for WiFi/remote access.
    
* **WiFi config - Only needed for WiFi access at home**

    1. Use `vim.tiny` or `nano` to modify the WiFi credentials in `wpa_supplicant.conf`.
    
        `nano /etc/wpa_supplicant/wpa_supplicant.conf`

    1. Comment out the `ssid` and `psk` lines and add replacement lines with your desired WiFi credentials. 
        
        **Note: before turning in your kit at the end of class, remember to delete your credentials and uncomment the original lines.**

    1. Connect an Ethernet cable **from the Rapsperry Pi to the MicroLogix 1100.** This is used to forward your network traffic from WiFi to the PLC's Ethernet interface.

    1. Reboot the Raspberry Pi.

    1. You will need to find the IP address of your Raspberry Pi. There are many ways to do this, but `ifconfig` is probably the easiest.

* **Rockwell Software Setup - You have two choices; choose one:**

    1. Download and use the ICS VM image from the CDN share:

        `\\10.1.2.7\Public\Dunlap\ACE_VM`

    1.  OR, Install the Rockwell software yourself. You need to create a Rockwell account, so I downloaded the two installers you need and put them on the CDN share. You can install these on any Windows machine or VM.
    
        `\\10.1.2.7\Public\Dunlap\ACE_Installer`


* **Network Setup:**

    Whatever computer/VM Rockwell's tools are installed on, it needs to be able to communicate with the PLC. 
    
    * If you're on WiFi, make sure you can `ping` the IP address of the Raspberry Pi.

    * If you're using Ethernet, the PLC's IP should be 192.168.107.3, so you will need to configure you network interface to use a static IP in the 192.168.107.* subnet. 
    
    * If you're in the VM, will also need to configure your VM interface to be able to ping your device IP.

    * Make sure you can ping your target device before moving on.

* **Remaining Setup**

    Read through and follow the instructions **in order** here:

    https://github.com/dillrich/22SP_CSCE660/tree/main/hilics_docs

    * **Note: The VNC connection section in 02_hilics_vnc.md is only for WiFi, but everyone should read the Simulation section.** 
    * **Note: These docs were written for ACE, so there may be differences from your setup.**
    * **Note: You don't need to turn in anything from these docs. If you follow all the instructions, you should be able to collect the screenshot required for turn-in - see HILICS Write-up below.**


## Write-up
1.	Demonstrate that you completed the tasks.
2.	What are the security benefits and risks associated with rooting the device?
3.	Do people still root their devices? If so, what are the reasons why they do this? What are other examples throughout digital history that show humans modifying their devices?
4.	What things can you do after rooting your phone that you could not otherwise do? Can you access any folders/files? Be specific. 
5.	Are there implications for Digital Rights Management? Any legal constraints with rooting an android phone?
6.	Did you break the law? Discuss.


## HILICS Write-up

Provide a screenshot of RSLogix connected to your PLC in Online mode (REMOTE RUN or REMOTE PROGRAM). It should look something like this:
