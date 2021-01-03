# Day 7 - Android Security Testing Continue Notes

------





```
Today's Agenda =>

Good resouces
Setup Lab 
BurpsuiteIntegration
ADB
Integrate Android Tamer to Genymotion
Vulnerable Lab resources which i will practice soon
```



### #1. **Setup Lab & Burpsuite Integration**





- [x] Virtualbox
- [x] Genymotion
- [x] Android Tamer 
- [x] apktool
- [x] dex2jar
- [x] mobsf
- [x] ADB
- [x] BurpSuite Proxy









```
ADB => Android Debug Bridge

* client-server program to enable the user to communicate with the emulator or the Connected Android Device
* Many commands it have and it gives access to a Unix LInux Shell that we can use to run a variety of commands on a decive
```



### ADB Commands =>



```
adb devices - List all the connected Android devices serial numbers

adb install <filename>.apk - Install the specified package

adb uninstall <uri> - uninstall the application with the specified identifier

adb shell ls - List all files in the root folder on the device

adb shell "ls sys" - List all files in the sys folder on the device

adb shell "ls -d */" - List only folders on the device in root

adb shell "ls -al <folder>"  - List all the info of the folder on the device in root

adb shell "pm list packages" - List all packages installed on the device

adb logcat - Start catching the system log file. This process will wait until it is killed (control C)
```





### Integrate Android Tamer to Genymotion



* Change Device Configuration Setting of genymotion 
  * Network Mode 
    * from NAT to Bridge
    * Choose Internet Card
* In Virtualbox
  * also change Network mode of Android Tamer from
    * NAT to Bridge
* Check IP Address of Genymotion Android device and note down it
* And check if it working or not in Android Tamer using `ping` command
* Now we can use ADB command in Android Tamer
* Connect to Android Device using ADB =>
  * adb connect <ip>





### Integrate Burpsuite from Android Tamer to Genymotion Device



* Open Burpsuite in Android Tamer
* Proxy => Bind Port to whatever => Specific Address => Genymotion Device's IP
* In Genymotion Device =>
  * WiFi Setting => Advance Option => Proxy => Manual =>  ip and port
  * On browser => http://burp => Download CA Certificate => change extension of cacert.der to cacert.cer
    * Go To Setting => Install from SD Card => choose file => give any name => set PIN or Pattern lock password







```
NOTE =>

I solve TLS error using last resource =>


https://blog.ropnop.com/configuring-burp-suite-with-android-nougat/
```





### Vulnerable Labs for Practice =>



```
allsafe                 
Damn-Vulnerable-Bank  
KotlinGoat  
SecurityShepherd  
VulnerableAndroidAppOracle  
VyAPI
Android-InsecureBankv2 
InjuredAndroid       
pivaa       
Vuldroid         
vulnerable-application    
WaTF-Bank
```











### RESOURCES =>





* [how-to-use-burpsuite-with-android-mobile](https://desk.zoho.com/portal/vegabirdtech/en/kb/articles/how-to-use-burp-suite-with-android-mobile)
* https://medium.com/bugbountywriteup/android-pentesting-lab-4a6fe1a1d2e0
* https://github.com/randorisec/MobileHackingCheatSheet
* https://support.genymotion.com/hc/en-us/articles/360012333077-How-to-use-Burp-suite-with-Genymotion-Desktop-
* https://blog.nvisium.com/android-assessments-with-genymotion-burp
* https://blog.ropnop.com/configuring-burp-suite-with-android-nougat/







