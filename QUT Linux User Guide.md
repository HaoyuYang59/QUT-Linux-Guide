# QUT Ubuntu User Guide
As an MPhil student and a Linux (currently Ubuntu 20.04) user from Queensland University of Technology (QUT), I found Linux hardly officially supported here, if any. So here I share my personal experience of accessing various daily QUT resources from Linux operating systems.

This guide is written and tested to work on **Ubuntu 20.04** as of May 2022 at Garden Points campus, and might be subject to future changes.

This guide was tested with a **student account**, things might vary if you're using a staff account.


## Table of Contents



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
    `sudo bash ./anyconnect-linux64-*.*.*-core-vpn-webdeploy-k9.sh  # initialize the install script with root privilege`   

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
The Remote Data Storage System ([RDSS](https://qutvirtual4.qut.edu.au/group/research-students/conducting-research/managing-research-data/store-digital-research-data/research-data-storage-service)) serves as a secure and fast repository to store and **backup** your research data. 

1. Set up Samba Clent  
    `# Ubuntu`  
    `sudo apt-get update`  
    `sudo apt-get install samba smbclient`  

2. Connect to the Remote File Server 
    a) Open the file manager.  
    b) Click "Other Locations" at the left bar (in Ubuntu 20.04) and might look different in other versions ("Connect to server", for example).  
    c) Input "**smb://rstore.qut.edu.au/**" and then click "connect", you should now be connect to the RDSS.  
    d) There should be three folders: Acquisitions, Projects, Archives. To know where you data locates, please read the "Where do I store my data?" part at [this page](https://qutvirtual4.qut.edu.au/group/research-students/conducting-research/managing-research-data/store-digital-research-data/research-data-storage-service).  


## Access QUT Printing Services


## Access Work Computer Remotely







 
