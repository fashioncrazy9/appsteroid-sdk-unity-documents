#PushNotification

## How to register a Push Notification certificate
First, download your Push Notification certificate generated on iOS Dev Center.
![pn01](Images/ss_fresvii_pn_01.png "PN01")
Register your certificate on KeyChain, which will be registered with the name listed below.
* For Development : Apple Development IOS Push Services: Your.Bundle.ID
* For Production : Apple Production IOS Push Services: Your.Bundle.ID

### How to create a p12 file
Open KeyChain, right click the certificate you’ve registered and select “Export”.
![pn02](Images/ss_fresvii_pn_02.png "PN02")
Enter the file name and make sure the file format is "Personal Information Exchange(.p12)” before you “Save” it.
![pn03](Images/ss_fresvii_pn_03.png "PN03")
Enter the password and create your p12 file.
![pn04](Images/ss_fresvii_pn_04.png "PN04")

### How to upload a p12 file
Login to the console [fresvii](https://fresvii.com/), go to Settings->Notification and upload your p12 file.
Enter the password you’ve previously setup when exporting the p12 file.
![pn05](Images/ss_fresvii_pn_05.png "PN05")
After a successful upload, you will see a screen like below.
![pn06](Images/ss_fresvii_pn_06.png "PN06")
