# Convert Apple Certificate into a P12 file
***
### make sure you have latest certificate: [Apple WWDRCA](https://developer.apple.com/certificationauthority/AppleWWDRCA.cer)
***


## STEP 1: Create a “.certSigningRequest” (CSR) file
* Open Keychain Access on your Mac (found in Applications/Utilities)
* In the main Keychain Access window ( <b>make sure that you don’t have a private key already selected</b> ) 
<br>otherwise this process will not work correctly
<br>From the toolbar, open Keychain Access > Preferences
* In the pop up window that appears, click the Certificates tab
* 
![Image](./1-01.png)

* Set both: 
<br>&nbsp;&nbsp;&nbsp;&nbsp;<b>“Online Certificate Status Protocol” = “Off”</b>
<br>&nbsp;&nbsp;&nbsp;&nbsp;<b>“Certificate Revocation List” = “Off”</b>
<br>&nbsp;&nbsp;&nbsp;&nbsp;( <b>see screenshot above</b> )
<br>
<br>
<b>*** Close this window ***</b>

* In the Keychain Access toolbar
<br>&nbsp;&nbsp;&nbsp;&nbsp;Open Keychain Access > Certificate Assistant > Request a Certificate From a Certificate Authority

![Image](./1-02.png)

* Enter:
<br>&nbsp;&nbsp;&nbsp;&nbsp;<b>“User Email Address”</b>
<br>&nbsp;&nbsp;&nbsp;&nbsp;<b>“Common Name” ( name of the developer as it appears in your Apple Developer Account )</b>
<br>&nbsp;&nbsp;&nbsp;&nbsp;<b>“CA Email” ( Leave blank )</b>
<br>&nbsp;&nbsp;&nbsp;&nbsp;<b>“Saved to disk” ( selected )</b>
<br>&nbsp;&nbsp;&nbsp;&nbsp;<b>“Let me specify key pair information” ( checked )</b>
<br>
<br>&nbsp;&nbsp;&nbsp;&nbsp;Click Continue
<br>
<br>Choose a filename & destination on your hard drive ( e.g. “CommanName.certSigningRequest” ) 
<br>
<br>&nbsp;&nbsp;&nbsp;&nbsp;Click Save
<br>
<br>
* In the next window

![Image](./1-03.png)

<br>&nbsp;&nbsp;&nbsp;&nbsp;<b>“Key Size” = “2048 bits”</b>
<br>&nbsp;&nbsp;&nbsp;&nbsp;<b>“Algorithm” choose “RSA”</b>
<br>
<br>&nbsp;&nbsp;&nbsp;&nbsp;Click Continue


This will create and save your certSigningRequest file (CSR) to your hard drive. 
A public and private key will also be created in Keychain Access with the Common Name you entered earlier (e.g. John Smith)

![Image](./1-04.png)

## STEP 2: Create the “.cer” file in your iOS Developer Account
* Log on to https://developer.apple.com

![Image](./2-01.png)

* Click <b>“Certificates, Identifiers & Profiles”</b>

![Image](./2-02.png)

* Click <b>“Provisioning Profiles”</b> from the left-hand column

![Image](./2-03.png)

* In the <b>“Certificates”</b> section at the top of the left-hand panel
* Click <b>“Production”</b>
* Click the <b>“Add” (+)</b> button at the top-right of the main panel

![Image](./2-04.png)

In the main panel ( Select <b>“Development”</b> or <b>“Production”</b> Option needed )

![Image](./2-05.png)

* Click Continue

![Image](./2-06.png)

* Click <b>“Choose File”</b> & find the CSR file you’ve just made from your hard drive

![Image](./2-07.png)

* Click <b>“Generate”</b> and wait for the file to process 

![Image](./2-08.png)

* Click <b>“Download”</b> to get the file, and then click the Done button at the bottom once the download has finished

## STEP 3: Install the .cer and generate the .p12

* Find the .cer file you’ve just downloaded and double-click. 
<br>If the certificate hasn’t automatically been installed:
<br>you will see the following (otherwise, skip the next two steps)

![Image](./3-01.png)

* Make sure the drop-down is set to <b>“login”</b>
* Click <b>“Add”</b>

* Open up KeyChain Access again
* Find the two profiles you created in Step 1 (with the iOS Developer Common Name)

![Image](./3-02.png)

* You should now be able to expand the <b>“private key”</b> profile
<br>which should show the certificate you just added

![Image](./3-03.png)

* Select only these two items (not the public key), by holding SHIFT and clicking both items
* Right click and click <b>“Export 2 items…”</b> from the popup

![Image](./3-04.png)

* Make sure the file format is a <b>“.p12”</b> and choose a filename and destination on your hard drive
* Click <b>“Save”</b>

![Image](./3-05.png)

Finally, you’ll be prompted to set a password

