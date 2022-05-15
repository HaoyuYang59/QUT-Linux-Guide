# QUT Ubuntu User Guide
As an MPhil student and a Linux (currently Ubuntu 20.04) user from Queensland University of Technology (QUT), I found Linux hardly officially supported here, if any. So here I share my personal experience of accessing various daily QUT resources from Linux operating systems.

This guide is written and tested to work on **Ubuntu 20.04** as of May 2022 at Garden Points campus with **HDR student account**, and might differ if you're holding a different account.


## Table of Contents
  * [(Prerequisite) Access QUT Network](#prerequisite-access-qut-network)  
    * [On Campus-Access QUT WiFi](#on-campus-access-qut-wifi)  
    * [Off Campus-Establish VPN Connection](#off-campus-establish-vpn-connection)  
  * [Set up QUT Email on External Mail Client](#set-up-qut-email-on-external-mail-client)
  * [Access QUT Remote Data Storage System (RDSS)](#access-qut-remote-data-storage-system-rdss)
  * [Access QUT Printing Services](#access-qut-printing-services)
  * [Access Work Computer Remotely](#access-work-computer-remotely)


## (Prerequisite) Access QUT Network
First step first, to access most QUT IT resources, you might need to first gain access to the QUT network, either on campus through QUT WiFi (or wired Ethernet) or off campus via Virtual Private Network (VPN).

### On Campus-Access QUT WiFi
As far as I know, this is the only thing where "official QUT instruction" is available and could be found [here](https://qutvirtual4.qut.edu.au/group/student/it-and-printing/wi-fi-and-internet-access/qut-wi-fi). Please note, most settings are **NOT default** so please check every entry carefully.

### Off Campus-Establish VPN Connection
1. Download VPN client-Cisco AnyConnect Secure Mobility Client  
    Go to [this site](https://sas.qut.edu.au/), login with your QUT username and password to start the download.

2. Install VPN Client  
    Note: you would need **root privilege** to perform the installation with the following command:  
    `cd $DOWNLOAD_POSITION  # change to download directory`  
    `sudo bash ./anyconnect-linux64-*.sh  # initialize the install script`   

3. Launch VPN Client on Linux and Establish VPN Connection  
    VPN server hostname: remote.qut.edu.au    
    Username: *your QUT username*    
    Password: *your QUT password*    


## Set up QUT Email on External Mail Client  
As recommended by [ThunderBird](https://support.mozilla.org/en-US/kb/difference-between-imap-and-pop3), here I introduce how to setup **IMAP** service to access and manage your email account from external mail client.   
Alternatively, you could also use the [Progressive Web App](https://support.microsoft.com/en-gb/office/use-the-web-version-of-outlook-like-a-desktop-app-b360bd9a-00dc-43a4-bdf8-71cdeeb78e83) (PWA) if you prefer the original Outlook appearance.

1. Set up Incoming Mail (IMAP) Server    
    Server name: outlook.office365.com  
    Username: *your qut username*@qut.edu.au  
    Port: 993  
    Encryption method: TLS  
    Authentication method: OAuth2  

2. Set up Outgoing Mail ([SMTP](https://support.microsoft.com/en-us/office/pop-imap-and-smtp-settings-for-outlook-com-d088b986-291d-42b8-9564-9c414e2aa040)) Server  
    Server name: smtp.office365.com  
    Port: 587  
    Encryption method: STARTTLS  
    Authentication method: OAuth2  

3. (optional) Subsribe to the Folders  
Sometimes, you might find some of your folders under "INBOX" missing. In this case, you may need to **subscribe** to the specific folders for them to show up.
  

## Access QUT Remote Data Storage System (RDSS)
The Remote Data Storage System ([RDSS](https://qutvirtual4.qut.edu.au/group/research-students/conducting-research/managing-research-data/store-digital-research-data/research-data-storage-service)) serves as a secure and fast repository to **backup** your research data. 

1. Set up SAMBA Clent  
    `sudo apt-get update`  
    `sudo apt-get install samba smbclient`  

2. Connect to the Remote File Server 
    a) Open the file manager.  
    b) Click "Other Locations" at the left bar (in Ubuntu 20.04) and might look different in other versions ("Connect to server", for example).  
    c) Input "**smb://rstore.qut.edu.au/**" and then click "connect".
    d) You should be asked for identification, if so, use "**QUTAD\your_QUT_username**" as the username.
    e) You would now be connected to the RDSS. There should be three folders: Acquisitions, Projects, Archives. To know where you data locates, please read the "Where do I store my data?" part at [this page](https://qutvirtual4.qut.edu.au/group/research-students/conducting-research/managing-research-data/store-digital-research-data/research-data-storage-service).  


## Access QUT Printing Services  
This guide works at least on printing from the *printers outside the HDR offices* using *HDR-student account*. And I know there are different printers (for students or staffs) and details might be a little different, you might need do some experiments yourself if so.

1. Identify the Server  
    There should be a label around the printer identifying the printer as "\\FACULTY-print\FACULTY-BUILDING-INDEX" （for example, in my case "\\sef-print\SEF-M2-1"）.
   
 2. (Optional) Install Driver  
    a) I would usually recommend installing the driver. You might try without doing so and come back if anything goes sideways.  
    b) Usually, you would be able to identify the manufacturer and model of the printer by looking carefully around the printer or the control panel (or maybe ask the admin). In my case, it's one "**ApeosPort-VI C4471**" from "FUJIFILM". If so, go to the manufacturer's website and try to find the driver for Linux or simply Google search. In my case, I found the driver [here](https://support-fb.fujifilm.com/processDriverForm.do?ctry_code=SG&lang_code=en&d_lang=en&corp_pid=AP6C4471&rts=null&model=ApeosPort-VI+C4471&type_id=2&oslist=Linux&lang_list=en). Please **DO NOT** use this driver if the model doesn't match.  

3. Add the Printer  
    a) Go to "Settings" - "Printers" - "Additional Printer Settings".  
    b) Click "+ Add" on the popup window, go to "Network Printer" - "Windows Printer via SAMBA".  
    c) Input the printer location. **NOTE: remember to use "/" in Linux instead of "\"**. For example, the printer is labelled as "\\sef-print\SEF-M2-1", so I put **"//sef-print/SEF-M2-1"**.  
    d) Input Authentication using "**QUTAD/your_QUT_username**" and then click "forward". **Note: from my experience, you would not be prompted nor allowed to print if you don't input authentication beforehand**  
    e) Choose driver and then decribe the printer.  


## Access Work Computer Remotely
Note: This guide is written using **[Remmina](https://remmina.org/)** 1.4.2 , installed by default on Ubuntu 20.04, as an example.  

1. Enable Remote Desktop on Work Computer following [this guide](https://qutvirtual4.qut.edu.au/group/staff/technology-and-facilities/technology-services/internet-and-network-access/working-remotely/remotely-connect-to-your-work-computer)  

2. Identify the **Full Computer Name** of your Work Computer, following [this guide](https://support.microsoft.com/en-us/office/do-you-need-help-locating-your-computer-name-00384381-8aa9-4398-b81b-475f09fed618). For example, my computer name looks something like "*SEF-PAxxxxxxxx*".  

3. Start Remmina, click ![image](https://user-images.githubusercontent.com/80093591/168461176-47f890ce-7936-4a78-a8da-5ceeb6efbdbd.png) at the left top corner to creater a New Connection Profile, with the following details:  
    Protocol: RDP-Remote Desktop Protocol  
    Server: *your_computer_name*.qut.edu.au  
    Username: *your_QUT_username*  
    Password: *your_QUT_password*  

4. Click "Save" to save your RDP profile, then double click to start the Remote Desktop session.  
    
