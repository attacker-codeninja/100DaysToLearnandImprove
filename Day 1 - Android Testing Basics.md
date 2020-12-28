# 							Day 1 - Android Testing Basics





![Android Basics   ](https://image.slidesharecdn.com/androidsecurity-131108001250-phpapp02/95/android-security-3-638.jpg?cb=1383869841)



------





### #1. Android Introduction



> ### Basics =>
>
> > Android is  based on **Linux Platform**
>
> > Android based on DVM => **Dalvik Virtual Machine** => Similar to JVM => Java Virtual Machine
> >
> > 		* Each app has its own DVM
>
> > Android is designed Primarily for Touch Screen mobile devices such  as Smart Phone,Tablet computers, Smart TV etc 
>
> > Android Use **SQLITE** database
>
> > Data Storage Location =>
> >
> > * /data/data/<package-name>
>
> > App Programming => done in java, kotlin (Native)
> > 		=> apk written in JAVA, with native libraries in C/C++
>
> > Hybrid could be written using frameworks like => ionic (HTML) or Xamarin
>
> > * Packages => **dex**, **data** and **resources** file into => zip file => uses .apk extension
> > * Each application is a different user
> > * Unique Linux user ID is assigned to each application.
> > * Each process has its own VM
> > * Least Privilege => each application has Access Only to the components that it requires to do the work
> > * Permissions Defined in the **Android Manifest** file
>
> 



> ### DVM => Dalvik Virtual Machine
>
> 
>
> > * Created by Dan Bornstein
> >
> > * It's Virtual System to run the android apps
> >
> > * Register based instead of Stack based
> >
> > * It runs the **dex** [Dalvik Executables] files
> >
> > * Similar to JVM => Java Virtual Machine
> >
> > * It optimizes the virtual machine for *memory*, *battery life* and *performance*.
> >
> >   
> >
> >   
> >
> > * The Dex compiler converts the class files into the .dex file that run on the Dalvik VM. 
> >
> > * Multiple class files are converted into one dex file.
>
> ![Dalvik Virtual Machine Flow](https://static.javatpoint.com/images/androidimages/flow.jpg)
>
> > *javac tool* => compiles => java source file => into => class file
>
> > *dx tool* => takes all the class files of application => generate a single **.dex** file
>
> > AAPT => Android Assets Packaging Tool



> ## AndroidManifest.xml
>
> >  Each Android Package contains a File => **AndroidManifest.xml**  => in the root of the archive => Very Important
>
> > Contains Information about
> >
> > * package
> > * componenets
> >   * activities
> >   * services
> >   * content providers
> >   * intent
> >   * broadcast services
> > * Responsible to protect the application by defining permissions
> > * Android Security Features
>
> > *The manifest file can perform the following operations:*
> >
> > 
> >
> > - Name the application's Java software package. The package name serves as a unique identifier for the application.
> > - Describe the various components of the application, including the **activities, services, broadcast receivers, and content providers** that make up the application. 
> >   - It also names the classes that implement each component and publishes its functions, such as the Intent messages they can handle. These declarations inform the Android system about the components and the conditions under which they can be started.
> > - Determine the **process** of hosting application components.
> > - Declare what **permissions** the app must have to access the protected parts of the API and interact with other apps. 
> >   - It also declares that the **permissions** required by other applications to interact with the application components list Instrumentation classes, which can provide analysis and other information when the application is running. These statements will only appear in the manifest when the app is under development and will be removed before the app is released.
> > - Declare the minimum Android API level required by the application
> > - List the libraries that the app must link to
>
> 
>
> 
>
> 
>
> ### List file structure
>
>
> general structure of the manifest file =>
>
> 
>
> ```
> <? xml version = " 1.0 " encoding = " utf-8 " ?>
> 
> < manifest >
> 
>     < uses-permission />
>     < permission />
>     < permission-tree />
>     < permission-group />
>     < instrumentation />
>     < uses-sdk />
>     < uses-configuration />  
>     < uses-feature />  
>     < supports-screens />  
>     < compatible-screens />  
>     < supports-gl-texture />  
> 
>     < application >
> 
>         < activity >
>             < intent-filter >
>                 < action />
>                 < category />
>                 < data />
>             </ intent-filter >
>             < meta-data />
>         </ activity >
> 
>         < activity-alias >
>             < intent-filter >... </ intent-filter >
>             < meta-data />
>         </ activity-alias >
> 
>         < service >
>             < intent-filter >... </ intent-filter >
>             < meta-data />
>         </ service >
> 
>         < receiver >
>             < intent-filter >... </ intent-filter >
>             < meta-data />
>         </ receiver >
> 
>         < provider >
>             < grant-uri-permission />
>             < meta-data />
>             < path-permission />
>         </ provider >
> 
>         < uses-library />
> 
>     </ application >
> 
> </ manifest >
> ```
>
> 
>
> > The following list contains all the elements that can appear in the manifest file, listed in alphabetical order:
>
> ```
> < action >
> < activity >
> < activity-alias >
> < application >
> < category >
> < data >
> < grant-uri-permission >
> < instrumentation >
> < intent-filter >
> < manifest >
> < meta-data >
> < permission >
> < permission-group >
> < permission-tree >
> < provider >
> < receiver >
> < service >
> < supports-screens >
> < uses-configuration >
> < uses-feature >
> < uses-library >
> < uses-permission >
> < uses-sdk >
> 
> ```
>
> 







### Threats

> > The most dangerous attacks on mobile applications are those that **disclose sensitive data** or help a **compromise of the device**. 
>
> > But, server-side vulnerabilities cause the greatest risk to mobile application deployments as a whole because they can expose **unrestricted access to back-end systems.**

> > Mobile application penetration testing is an attempt to evaluate the security of a mobile application trying to exploit vulnerabilities. 
> >
> > 
> >
> > It includes **decompiling**, **real-time analyzing** and **testing** mobile application **for security point of view**.



![img](https://udemy-images.s3.amazonaws.com/redactor/raw/2018-09-13_11-15-16-24388ac434e709fed4a45ced7a2ad005.png)













### #2. Android Architecture



![image-20201228104503289](/home/code/.config/Typora/typora-user-images/image-20201228104503289.png)



![image-20201226190619625](file:///home/code/.config/Typora/typora-user-images/image-20201226190619625.png?lastModify=1609156486)







```
4. Different Layers =>

1. Applications
2. Application Framework
3. Libraries
4. Android Runtime

Linux Kernel Sits at the Bottom => It give Better Performance for mobile environment
		=> It Interact with all hardware components => contains most of the hardware drivers
		=> Responsible for most of the Security Features that are present in Android

```













### #3. Android Security Features & The Fundamental Android Security Models





![image-20201228112800411](/home/code/.config/Typora/typora-user-images/image-20201228112800411.png)







* From above we can see that every application have its own UID and run in its own Instances





> * Kernel based application sand boxing
> * UID, GID based Access Control and SELinux
> * System Services running with low privileges
> * Secure IPC [Interprocess Communication]
> * Application/Code Signing
> * Android Permission
>   * i.e. Application defined and user-granted permissions
> * Application Sand boxing 
> * Google Bouncer
> * Unix Sandboxing
> * Each Application have its own user name and memory space
> * One app cannot access resources of other app
> * Android Permission enforcement



> ## Android Permission =>
>
> 
>
> * System Application specific
> * Fine grained
> * User chooses to give permission to Application [Android 6+]
> * Install time permission
> * Run Time Permission [Android 6+]
> * Android Permission protect
>   * Access to sensitive APIs
>   * Access to content providers
>   * Inter- and intra-application communication
>
> 
>
> ![image-20201226201441089](file:///home/code/.config/Typora/typora-user-images/image-20201226201441089.png?lastModify=1609158001)
>
> 
>
> 
>
> ![image-20201226201526229](file:///home/code/.config/Typora/typora-user-images/image-20201226201526229.png?lastModify=1609158009)
>
> 
>
> 
>
> 
>
> ![image-20201226183403274](file:///home/code/.config/Typora/typora-user-images/image-20201226183403274.png?lastModify=1609158016)
>
> 
>
> 
>
> ![What is an Android Application…?   ](https://image.slidesharecdn.com/androidsecurity-131108001250-phpapp02/95/android-security-11-1024.jpg?cb=1383869841)
> 



### **Let's dive into Security Features => **



> ## #1. Application Sandbox
>
> 
>
> > *The foundation of the Android application security model is that no two applications running on the same device should be able to access each other’s data without **authorization**.*
>
> > i.e  They should not affect the operation of other applications, either
>
> > Application Sandbox => having this concept of above
>
> > It Assign Unique User Identity to application [UUID]
> >
> > ​	It means => each application will be running under its own user and its own *virtual machine* (VM), Dalvik or ART
> >
> > > so each process executes independently from one another
>
> 
>
> > EXCEPTION =>
> >
> > An exception where two apps can be processed under the same user and share the same VM is when they use a *shareUserId* tag which is declared in *AndroidManifest.xml:*
> >
> > 
> >
> > ```
> > android:shareUserId="com.modulotech.example"
> > ```
>
> > > With this tag, two or more applications will be sharing the same UID, accessing the each other’s data, holding the same set of permissions, and if desired, running the same process. 
> > >
> > >
> > > However, the feature is deprecated in API 29 and higher because of non-deterministic behavior within the package manager.
>
> 
>
> 
>
> ### Binder
>
> > There are still cases where processes would like to communicate with each other. That is the moment when **Binder** plays its role.
>
> * **Binder** is the Android-specific *Inter Process Communication* (IPC), also an *Inter Components Communication*
> * All applications have access to the Binder and are able to communicate with it.
> * Parcels are sent from apps to the Binder and passed to Activity Manager to check whether the calling application has permissions to perform the request.





> ## #2. Application Signing
>
> 
> 
>
> > **Application Signing** helps to **identify** the **author** of an application and to **update** the **application** without any complex permission
>
> 
>
> > It also represents a degree of **trust** in other aspects of the security model.
>
> 
>
> > The signing of a package is done **cryptographically** using a **certificate** whose **key** is hold by application developers 
> >
> > > nowadays the key may also be stored on Play Store utilising [Play App Signing](https://developer.android.com/studio/publish/app-signing#app-signing-google-play)’s feature
>
> 
>
> > The signing of a package is **mandatory** even if the application running is in debug mode
>
> > The idea of the Android Application Signing model is to prevent an application from being maliciously manipulated. 
> >
> >
> > Once application codes are decompiled and then modified, the certificate will no longer be valid.
> >
>
> > Application signing is also the first step to place the application in its Application Sandbox.
>
> 
>
> > two or more applications that share the same UID through *shareUserId* tag must be signed by the **same** certificate.
>
> > *Note that you can sign two or more applications, which do not share the same UID, with the same certificate. However, they will be running under different users and VMs.*
>
> 
>
> When you try to install/update an application with a non-identical certificate, you will get an error:
>
> ```
> adb: failed to install release_app.apk: Failure [INSTALL_FAILED_UPDATE_INCOMPATIBLE: Package com.modulo.example signatures do not match previously installed version; ignoring!]
> ```
>
> 
>
> 
>
> > To sign an open/unsigned apk, you can use some built-in tools in JDK or SDK. 





> ## #3. Application Permission
>
> 
>
> > Android controls certain types of information and resources which are often seen as *sensitive* such as: 
> >
> > >  SMS message, contact, telephone, location, camera etc.
>
> 
>
> > granting access to these pieces of info to the right applications having the correct demand is one of the goals of 
> >
> > **Android Security Models.** 
> >
> > > That is why Application Permissions is created.
>
> > As Android OS is not able to detect whether an application is eligible to use a resource; 
> >
> >
> > what it does is to deactivate all the accesses and only grant permissions when apps request (for the minor permissions) or user accepts (for the major permissions).
> >
> > > In that way, Android ensures that only resources permitted are exposed to the applications permitted.
>
>
> Before installing an application from Play Store, you can preview the requested permissions for the app by clicking **“Permission detail”.**
>
>
> ![Request permissions of an application are previewed on Play Store](https://miro.medium.com/max/540/1*G5_bLAJKHKfcWo1k0pMMxw.png)
>
> 
>
> > permission preferences are stored by **Activity Package Manager** in different files such as: 
> >
> > > */data/system/packages.list,* 
> > >
> > > */data/system/packages.xml*,
> > >
> > >  */data/system/users/0/runtime-permissions.xml*
> >
> > These files are not accessible on non-rooted devices.
> >
> > * When an application requests these permissions, its UID will be added to a Linux group id (GID).
> > * The permission <-> GID mapping can be found at [*/system/etc/permissions/platform.xml*](http://androidxref.com/9.0.0_r3/xref/frameworks/base/data/etc/platform.xml#30)
>
> ### Protection Level =>
>
> 
>
> * Each permission is associated to a protection level. 
> * there are three levels of protection **that affect third-party applications**: 
>   * normal
>   * signature
>   * dangerous
> * there are in total six protection levels:  => class [PermissionInfo](https://android.googlesource.com/platform/frameworks/base/+/2ca2c87/core/java/android/content/pm/PermissionInfo.java) in Android source code
>   * PROTECTION_NORMAL (*normal*), 
>   * PROTECTION_DANGEROUS(*dangerous*), 
>   * PROTECTION_SIGNATURE(*signature*),
>   *  PROTECTION_SIGNATURE_OR_SYSTEM(*signatureOrSystem*), 
>   * PROTECTION_FLAG_SYSTEM(*system*), 
>   * PROTECTION_FLAG_DEVELOPMENT(*development*).
>
> 
>
> ![Image for post](https://miro.medium.com/max/2212/1*oyIwze7cgOIpNDYJdh4BWw.png)
>
> 
>
> 
>
> > The most important one is *dangerous* level because it often requests sensitive data, so the application must prompt user to grant permission at runtime
> >
> > The permissions associated to this level are also called Runtime Permissions.



> ### #4. Data encryption
>
> 
>
> > **Encryption** *is the process of encoding all user data on an Android device using **symmetric encryption keys**. Once a device is encrypted,* **all** **user-created** *data is automatically encrypted before committing it to disk and all reads automatically decrypt data before returning it to the calling process.*
>
> > The purpose of data encryption is to protect all user data (only the data in */data* partition is encrypted) when the OS suspects that the phone might be out of user’s control. 
>
> > More accurately, data encryption will be triggered when the phone is powered off and then decrypted when user reboots the device and unlocks screen with PIN/password/pattern
> >
> > 
> >
> > That is why Android users often see a small lagging when the device has been rebooted.
>
> 
>
> > Android has two methods for device encryption: 
> >
> > * *Full-disk encryption(FDE)* 
> >
> >   and 
> >
> > * *File-based encryption(FBE).*
>
> > ## **Full-disk encryption**
> >
> >
> > FDE =>  introduced in  => Android 4.4 => became stable from Android 5.0 onwards => use up to Android 9.0 
> >         =>  no longer allowed in Android 10 and higher.
> >
> > 
> >
> > FDE use =>  master key =>  which is randomly generated upon first boot, to encrypt the whole user’s data.
> >  
> >
> > This master key is also encrypted using user PIN/password/pattern. 
> > Thus, when user changes this PIN/password/pattern, only the master key is re-encrypted, not the whole data.
>
> 
>
> > ## **File-based encryption**
> >
> > FBE =>  supported from Android 7.0 and later =>  For Android 10 and higher, FBE is required.
> >
> > ​        => Provides an encryption using different keys on different files
> > ​        => theses files will be decrypted independently
> >
> > 
> >
> > >  It avoids a situation where someone somehow has a “universal” key and uses it to open all data.
>
> > How to know If our device supports FDE or FBE ? =>
> >
> > 
> >
> > > ```
> > > # run this command
> > > 
> > > adb shell getprop ro.crypto.type
> > > 
> > > It returns =>
> > > 
> > > “file” if your device uses File-based Encryption 
> > > 
> > > and 
> > > 
> > > “block” if it uses Full-disk Encryption.
> > > ```
>
> 







### #4. Android Starting Process



* > The whole boot-up process starts with the boot-loader, which in turn starts the init process—the first user-land process.  

* > So, any change in boot-loader, or if we loaded up another boot-loader instead of the one present by default, we could really change what is being loaded on the device. 

* > The boot-loader is usually vendor-specific, and every vendor has their own modified version of the boot-loader. 
  >
  > Regularly, this functionality is disabled by default by having a locked boot-loader, which enables only the trusted kernel defined by the vendor to run on the device.

* > In order to flash your own ROM to the Android device, the boot-loader requires to be unlocked. 
  >
  > The method of unlocking a boot-loader might differ from device to device. In some situations, it could also void the warranty of devices.  

  







### #5. Android Application Components



```
1. Activity => Visual Screen => which we seen when open Any Android Application 
			=> All are called Activities

2. Intent   => Used to Start and Stop Activites and Services

3. Service  => Invisible Worker => Works in Background => Run back and Updating our Data Sources and 				Activities Triggring Notifications and also broadcast intents => Also perform some 				   tasks when Application are not active

4. Content Provider => Used to Manage and Process the Application DATA
					=> Sharing the data of particular application


5. Broadcast Receiver => Handle communications between Android OS and Applications


```







> ### More Explanation
>
> 
>
> * Activities
>   * Represents a single screen  or Visual screens of an Application with which user Interact
>     * Example, when user launch an Application
>   * Application can have multiple activities
>   * Different app can start the activity of other application [if the other app allows it]
>   * Defined in the **Manifest** file
> * Services
>   * Don't provide Graphical interface
>   * Provide facility to perform task that are long running in the background and run even when user has opened another application
>   * Handle Background task associated with an application
>   * Services can run in background indefinitely even if the application is destroyed
>   * E.g => Music application playing songs in background
> * Content Provider => Data Handling
>   * Handles the data
>   * Used to share/store application data
>   * Application can use other applications data using Content Provider
> * Broadcast Receivers
>   * Non-graphical components
>   * Respond to broadcast messages from other application
>   * Broadcast Receivers could be used to respond to system events like
>     * system boot-up
>     * low battery
>     * SMS  etc
> * Intent
>   * Defined object used for messaging which is created and communicated to an intended application componenet
>
> 



![image-20201226201318520](file:///home/code/.config/Typora/typora-user-images/image-20201226201318520.png?lastModify=1609156783)





> ![MANIFEST FILE   ](https://image.slidesharecdn.com/androidsecurity-131108001250-phpapp02/95/android-security-18-1024.jpg?cb=1383869841)
>
> 
>
> 
>
> ![COMPONENT PERMISSION   Components can be made accessible to other applications (exported) or be made private Default is p...](https://image.slidesharecdn.com/androidsecurity-131108001250-phpapp02/95/android-security-19-1024.jpg?cb=1383869841)
>
> 
>
> ![REQUESTING PERMISSIONS   ](https://image.slidesharecdn.com/androidsecurity-131108001250-phpapp02/95/android-security-20-1024.jpg?cb=1383869841)









## <- Android Component => INTENT [Let's dive little a bit more in this] ->



> ![Mobile Application Security Testing (Static Code Analysis) of Android App](https://image.slidesharecdn.com/mobileapplicationsecuritytesting-170319134141/95/mobile-application-security-testing-static-code-analysis-of-android-app-31-1024.jpg?cb=1489931342)

> ![Mobile Application Security Testing (Static Code Analysis) of Android App](https://image.slidesharecdn.com/mobileapplicationsecuritytesting-170319134141/95/mobile-application-security-testing-static-code-analysis-of-android-app-32-1024.jpg?cb=1489931342)

> ![Mobile Application Security Testing (Static Code Analysis) of Android App](https://image.slidesharecdn.com/mobileapplicationsecuritytesting-170319134141/95/mobile-application-security-testing-static-code-analysis-of-android-app-33-1024.jpg?cb=1489931342)

> ![Mobile Application Security Testing (Static Code Analysis) of Android App](https://image.slidesharecdn.com/mobileapplicationsecuritytesting-170319134141/95/mobile-application-security-testing-static-code-analysis-of-android-app-34-1024.jpg?cb=1489931342)



> ![Mobile Application Security Testing (Static Code Analysis) of Android App](https://image.slidesharecdn.com/mobileapplicationsecuritytesting-170319134141/95/mobile-application-security-testing-static-code-analysis-of-android-app-36-1024.jpg?cb=1489931342)





### # The Most common areas where we find mobile application data resides





```
The Most common areas where we find mobile application data resides

* Private Application Folder
* SD Card/Emulated SD Card
* System Log Files
* Keychain
* RAM
* Source Code
* Web Cache/History


Each app has its own folder where data is stored in files

In Android there is Either External SD Card or Emulated SD Card

Error Log Files are stored in System Log Files
	Lot of Sensitive app data stored in the System Log Files
	
	
Keychain
	Popular place to Store User Credentials and Passwords fir iOS
	
RAM -> Where Data is temporarily Stored
	-> When sign out of an Application or if there session is timeout
		-> its expected that sensitive data should automatically be cleared  by the application
		
Source Code => Where values are hardcoded in the app itself and residing on the phone
			=> Sensitive passwords and other values hard coded
			=> Code Analysis comes here
			
Web Cache History => Another common area to look 
```

