# Day 5 => Android Security Testing Notes Continue

------





```
Today's decide what to learn =>

Check what vulnerabilities are there for Android
Check Testing Methods
Check Tools Available

```



> **Mobile apps are basically classified into 3 categories:**

- **Web Apps:** These are like the normal web applications that are accessed from a mobile phone built in HTML.
- **Native Apps:** These are apps native to the device built using the OS features and can run only on that particular OS.
- **Hybrid apps:** These look like native but they behave like web apps making the best use of both web and native features.



------



### **Testing Analysis Types =>**



* **Static Analysis**
* **Dynamic Analysis**
* **Common application network analysis** 
  * Secure Application have certificate **pinning**
  * It is hard to analyse  the traffic using Proxy Tool
  * So, In the **Network Analysis** main Aim is 
    * Focus on bypass the certificate pinning
    * Tool can be use => HTTPCanary
* **Local Storage Testing**







![mwrinfosecurity.com | MWR InfoSecurity 15 Static Analysis .apk .dex .jar unzip dex2jar jd-gui .apk .smali apktool .java  ](https://image.slidesharecdn.com/pen-testingandroidapplications-160424063713/95/humla-workshop-on-android-security-testing-null-singapore-15-1024.jpg?cb=1461480778)









![mwrinfosecurity.com | MWR InfoSecurity 17 Dynamic Analysis Debug android application using Android Studio. .apk .dex .jar ...](https://image.slidesharecdn.com/pen-testingandroidapplications-160424063713/95/humla-workshop-on-android-security-testing-null-singapore-17-1024.jpg?cb=1461480778)











### So how the steps goes on ?



### **Static Analysis =>**



* Get .apk file
* Reverse Engineer it
* Decompile/Dis-assemble it
  * Dis-assemble => tool => Dedexer => it will give assembly like output + Baksmali => based on dedexer and gives code more easy to understand
  * Decompile => 
    * Dex2Jar => dalvik code turns to Java Byte Code [jar file]
    * Use jd-gui => to view Java Source codes





### **Dynamic Analysis =>**



* Load Emulator  => Android Studio, Genymotion
* Setup an Interception Proxy [ Burpsuite]
* Figure out SSL Issues
* Follow Generic Logic test cases we follow in Web Application





### **Local Storage Inspection =>**



* Check for Sensitive data getting stored on Client side
* XML Files, DB files are most commonly  found culprits
* Inspect memory for Information  Sensitive Information => **memdump**
* Inspect generated Logs  for Sensitive Information => **logcat**
* Uninstall and Check if things remain in Application Folder











### **SQLITE3** =>



![SQLITE3-some useful commands  Sqlite3 <dbfilename>   Loads the db   .tables   Shows the tables   .headers on|off   T...](https://image.slidesharecdn.com/androidforensicsandsecuritytesting-140308120518-phpapp02/95/android-forensics-and-security-testing-40-638.jpg?cb=1394280593)











### So, **there is is 3 Angles to Perform a successful  Security Testing**



1. Client Side Checks
2. Dynamic / Runtime /Local Storage / DB /  SD Checks
3. Static Code Analysis [a.k.a Reverse Engineering]











------





### **List of Vulnerabilities =>**



Static:
1. Reverse Engineering Leads to Source Code & Application Piracy
2. Insecure Application Certificate Signing
3. Application exported is set to true
4. Insecure Permission Requested



Dynamic:
1. SQL Injection
2. Cross-Site Scripting
3. OTP Brute Force & Strength
4. OTP Flooding
5. Lack of Authentication
6. Request Flooding
7. Insecure Deserialization
8. Insecure Data Storage
9. OTP Expiry.
10. Buffer Overflow.
11. Insecure Coding Practices.
12. Improper Error Handling.
13. Improper Schema Validation.
14. Password Complexity not maintained.
15. Password History not maintained.
16. Session Timeout Not Implemented.
17. Audit Trails Not Implemented.
18. Brute Force possible.
19. Server Banner Disclosure.
20. Application Works on Rooted Device.



------



### **Attacking Android Application => **



* Exploiting Activities
* Exploiting Insecure Content Providers
* Attacking Insecure Services
* Abusing Broadcast Receivers



------





### **What to Look for while Static Analysis?** 



* Look for API Information, DB Connection Strings, Internal/external IP Disclosure and Ports , Passwords, Emails etc
* TIP => A pair of  /* and  */  holds lot of information 





1. **M1: ** *Impmroper Platform Usage =>*  Android Intents, Permissions
2. **M4:** *Insecure Authorization =>* Identifying Session Keys, Session Management Logic
3. **M5:** *Insufficient Cryptography =>* Covering cryptographic keys (like MD5,SHA Keys) and encryption logic
4. **M7:** *Client Code Quality =>* like Buffer Overflows, format string vulnerabilities and various other code-level mistakes
5. **M8:** *Code Tampering =>* Covers Binary patching, local resource modification, method hooking and dynamic memory modification
6. **M9:** *Reverse Engineering =>* analysis of binaries, algorithms and other assets
7. **M10:** *Extraneous Functionality =>* Hidden backdoor functionalities,  commented code (accidently by developer)









### **What needs to look while Code Analysis =>**



* Android Intents
* Permissions => Permission File => /data/system/packages.xml
* Identifying Session keys
* Finding Session mgmt Logic
* Checking for Cryptographic Keys, salt tokens, Hash Values
* Finding Encryption Mechanism
* Buffer Overflow
* Format String Vulnerabilities
* Local resource and dynamic modification
* Binary patching
* Method hooking
* Analysis of libraries
* Analysis of algorithms
* Hidden backdoor Functionalities





### **Keen an eye on for any Flaws:=> **



* Activities
* Services
* Intents
* Broadcast Receivers
* Content Providers



------



### **Reverse Engineering =>**



![Reverse Engineering Arsenals  ](https://image.slidesharecdn.com/androidsecuritytesting1-180912072947/95/android-security-testing-7-1024.jpg?cb=1536737451)





------



### **TOOLS TIME => **



* Drozer => Assessment Tool => Interprocess Communication
  * Find Vulnerabilities in Application or Devices
  * Provide Exploits and Useful Payloads for Known Vulnerabilities
* m0bLiz3r tool => Static Analysis Tool => Functionality like => 
  * information disclosure automation from the source code of the .apk file
  * https://github.com/SudhanshuC/Android-Testing
* Android SDK
* Genymotion
* ADB
* Burpsuite
* APKTools
* Smali/baksmali
* Appuse/Android Tamer
* MobSF
* QARK [Quick Android Review Kit]



------





### **How to Fetch APK ?**



* From target's website
* From play store
  * Online Link for download apk file =>
    * https://apkpure.com
    * http://apps.evozi.com





### **Conversion of APK to Source Code =>**



* Manual way => 
  * dex2jar and apktool
* Online Way =>
  * https://www.javadecompilers.com/apk







------



