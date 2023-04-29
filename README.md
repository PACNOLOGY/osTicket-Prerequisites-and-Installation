# osTicket-Prerequisites-and-Installation
osTicket: Prerequisites and Installation
osTicket logo

osTicket - Prerequisites and Installation
We will be step-by-step going through the process of installing OSTicket, including neccesary prerequisites to allow for proper operation.
Environments and Technologies Used
Microsoft Azure (Virtual Machines/Compute)
Remote Desktop
Internet Information Services (IIS)
Operating Systems Used
Windows 10 (21H2)

------------------------List of Prerequisites------------------------

 **** Setting up a Virtual Machine (VM) in Microsoft Azure, and setting it to run Windows 10. ****
We will not be covering this as it's a simple process to execute.  However, what will be pointed out is that when creating the VM, we need it to have more than 1 vCPU.  For this tutorial, I have chosen East US for region and Standard_E2s_v3 - 2 vCPUs, and we must allow it to create a new Virtual Network (Vnet).

Now that we have our VM up and running, we must access it through a remote desktop application.  I'm running linux so I had to download one, but that's irrelevant because we will be doing this process in the VM we created.  In this case, mine is named CCAZF-SERVER [Insert photo of vm]
  
  **** Prerequisites for installing OSTicket on any host machine ****
A lot of what we will be using for this process can be found here https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6
keep that tab open, we will be coming back to this. [Insert photo of page]

1}  First, we must enable IIS in Windows along with CGI.  To do this, we go to Start>Settings>Apps>Optional Features>More Windows Features>Internet Information Services>World Wide Web Services>Application Development Features>CGI.  BE SURE TO TICK THE BOXES BEFORE OPENING THE FOLDERS.  If your screen looks like mine you're on the right track.

2}  Now, let's go back and download "PHPManagerForIIS_V1.5.0.msi".  Go ahead and install it.  If it fails, that means you skipped my first step.  For shame, slow it down!

3}  Thirdly, we download and install "rewrite_amd64-en-US.msi"

4}  Fouth Step, we create our own directory.  "C:\PHP".  Then we go and download "php-7.3.8-nts-Win32-VC15-x86.zip" from our installation files tab.  You will have to manually tell edge to "keep" the file in order for it to actually download.  Extract it to our new "PHP" folder. [INSERT PHOTOS]

5}  Now we will download and install "VC_redist.x86.exe" [INSERT PHOTO]

6}  Step 6, we install "mysql-5.5.62-win32.msi".  We will go ahead and launch the Configuration Wizard once this installation completes. [INSERT PHOTO]
We want to select "Standard Configuration".  Go ahead and make up a password.  Let's go with "Password1" [INSERT PHOTO]

7}  Search for "IIS" from the "Start" menu.  Right click>Run as administrator.  Double click "PHP Manager" once we get it going.  
Item 3
Item 4
Item 5
Installation Steps
Disk Sanitization Steps

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.


Disk Sanitization Steps

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.


Disk Sanitization Steps

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.

