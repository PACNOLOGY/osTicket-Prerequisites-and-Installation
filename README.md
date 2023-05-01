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
<img src=https://i.imgur.com/ZF809zc.png>

Now that we have our VM up and running, we must access it through a remote desktop application.  I'm running linux so I had to download one, but that's irrelevant because we will be doing this process in the VM we created.  In this case, mine is named CCAZF-SERVER 
<img src=https://i.imgur.com/aHaHrX9.png>
  
  **** Prerequisites for installing OSTicket on any host machine ****
A lot of what we will be using for this process can be found here https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6
keep that tab open, we will be coming back to this. 
<img src=https://i.imgur.com/7aPixaC.png>
<img src=https://i.imgur.com/Hstt3Pc.png>

1}  First, we must enable IIS in Windows along with CGI.  To do this, we go to Start>Settings>Apps>Optional Features>More Windows Features>Internet Information Services>World Wide Web Services>Application Development Features>CGI.  BE SURE TO TICK THE BOXES BEFORE OPENING THE FOLDERS.  If your screen looks like mine you're on the right track.
<img src=https://i.imgur.com/jjSPuvZ.png>

2}  Now, let's go back and download "PHPManagerForIIS_V1.5.0.msi".  Go ahead and install it.  If it fails, that means you skipped my first step.  For shame, slow it down!
<img src=https://i.imgur.com/RPRqgqQ.png>

3}  Thirdly, we download and install "rewrite_amd64-en-US.msi"

4}  Fouth Step, we create our own directory.  "C:\PHP".
<img src=https://i.imgur.com/uqifqK3.png>
Then we go and download "php-7.3.8-nts-Win32-VC15-x86.zip" from our installation files tab.  You will have to manually tell edge to "keep" the file in order for it to actually download.  Extract it to our new "PHP" folder. 
<img src=https://i.imgur.com/IHsZ264.png>

5}  Now we will download and install "VC_redist.x86.exe"
<img src=https://i.imgur.com/u1SHb7I.png>

6}  Step 6, we install "mysql-5.5.62-win32.msi".  We will go ahead and launch the Configuration Wizard once this installation completes. [INSERT PHOTO]
We want to select "Standard Configuration".  Go ahead and make up a password.  Let's go with "Password1" [INSERT PHOTO]

7}  Search for "IIS" from the "Start" menu.  Right click>Run as administrator.  Double click "PHP Manager" once we get it going.  Click "Register new PHP version", as the program is telling us that's what we need.  Browse your way to "php-cgi"
<img src=https://i.imgur.com/t8q9tUf.png>

click [OK], and then it should look like this
<img src=https://i.imgur.com/ihyLe14.png>

Click on our server name from under the "Connections" list, and then on the right side of the window you can restart the server.  Do it. 
<img src=https://i.imgur.com/GjWM2F8.png>

8}  Now we can finally install osTicket.  Download the .zip file "osTicket-v1.15.8.zip" and extract it, then put the "upload" folder into c\inetpub\wwwroot.
<img src=https://i.imgur.com/hiBh8QT.png>

Rename "upload" to "osTicket".
<img src=https://i.imgur.com/2Yuu7bo.png>

Reload IIS again. On the left side of the window, navigate to Sites>Default Web Site>osTicket and click on the right side of the window where it says "Browse *:80 (http)"
<img src=https://i.imgur.com/auxINvY.png>

It should open us up to a "Thank You" tab.
<img src=https://i.imgur.com/SShr7Q5.png>

9}  We're going to fill in the "X"s.  Go back into IIS, and from where we left it, we can run the "PHP Manager".
<img src=https://i.imgur.com/7pD7m43.png>

We have to change some options under "Enable or disable an extension".  Click that.  Right click and "enable" the three following dlls:  "php_imap.dll", "php_intl.dll", and "php_opcache.dll".  Go ahead and refresh osTicket in your browser.  Youll see more checks now.  Browse your way to "C:\inetpub\wwwroot\osTicket\include" and rename ost-sampleconfig.php
<imgsrc=https://i.imgur.com/pQtxr9U.png>

to ost-config.php
<img src=https://i.imgur.com/qHkY1nH.png>

From there, Right click>properties>Security>[Advanced]  [Disable inhertance], Remove all inherited permissions from this object.  Then we [add]>"Select a Principal", and type "everyone" in the open type field, click [Check names], then [OK]  Check the "Full Control" box, then [OK],  then [Apply], then [OK]. then [OK] again.

10} Now we can finally hit [Continue] on the osTicket screen in our browser.  Fill the fields out to your needs, in my case I'm setting up a help desk so the email address is the only thing that has to be real, but you must not forget the info you put in. [INSERT PHOTO]

11} Now we will download and install "HeidiSQL" by opening the link from the "installation files" tab and follow along until we get a running .exe.  Go ahead and install the program as you would anything else.  Run it, click [New] as soon as you see it.  User "root", Password "Password1", then click [Open].  Now we go back to the osTicket window and fill in the same name and password on the screen we left it on.  Now in HeidiSQL we right click "Unnamed" and then "Create new>Database".  For Name I'm putting in osTicket, then [OK].

12} Now that we have a database made for osTicket we can enter it's name in the only empty field we left in the browser. [INSERT IMAGE].  Install it.  You'll be greeted with a "Congratulations" screen if all was done correctly.

13} For cleanup purposes we're going to navigate to C:\inetpub\wwwroot\osTicket and delete the "Setup" folder [IMAGE]  Now we go to C:\inetpub\wwwroot\osTicket\include and seek out the "ost-config.php". open up "properties" as we're going to change it's permissions back.  Go to "Security>advanced" again, "Audit", type "Everyone" Again, then set it to read and read & execute.  [Apply] and [OK].
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

