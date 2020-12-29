# Day 2 => Continue Android Basics Security Testing Notes





![Image for post](https://miro.medium.com/max/615/1*NyYaI179cunx4XEgjhBWsQ.jpeg)



------



## 

```
First recap => what I learned till now from Day 1

* Android is Linux based OS 

* Android applications are written primarily in Java, Kotlin (transpiled to Java), and C++

* When distributed, they use the .apk extension which stands for Android PacKage

* An APK is really just a ZIP file containing all the assets and bytecode for an app.

* Android use DVM [Dalvik Virtul Machine]

* Important file to look in apk => AndroidManifest.xml => contain information about :
	
	* package
    * components
    * Security Features
    * Protect applications and more
    
* javac tool  compiles .java files to -> .class -> dex tool -> compile .class file to => .dex

* Android Architecture important part to know

	* Applications
	* Application Framework
	* Android RunTime
	* Platform Libraries
	* Linux Kernel
	* Also one more i got to know today => HAL => Hardware Abstraction Layer => provides high level API for hardware management.
	
* Android Security Features is very important => Every app has its own Unique ID

* Access Control is UID/GID based

* Android Permission crucial role and Sandbox  + Encryption too

* Android Application Comonents 

	* Activity => user screen
	* Service  => Application that works in Background
	
        * Intent   => Used to Start and Stop Activites & Services or Used to bind other components 	                       
        together so they can communicate efficiently
	
	* Content Provider => All About DATA
	* Broadcast Receiver => Handle Communication between Android OS & Applications
	

```





## #1. Android Application Structure :



A typical unzipped APK structure looks like this:



```
**myapp.apk**
├── AndroidManifest.xml
├── META-INF/
├── classes.dex
├── lib/
├── res/
└── resources.arsc
```





> > > Let’s briefly cover each of these:
> >
> > 
> >
> > > **AndroidManifest.xml** =>
> > >
> > >
> > > This is a compressed version of the **AndroidManifest.xml** file which contains all of the basic application information such as the **package name, package version, externally accessibly activities and services, minimum device version**, and more. 
> > >
> > > 
> > >
> > > The compressed version of this file is **not humanly readable**, but there are a couple of tools that are able to uncompress it, most notably being **apktool** 
> >
> > 
> >
> > > **META-INF/** =>
> > >
> > > The *META-INF/*   folder is essentially a manifest of *metadata* information including the **developer certificate** and **checksums** for all the files contained within an APK. 
> > > 
> > >
> > >
> > > If you were to try and make changes to an APK without removing and re-signing this folder, you would get an error when installing the modified version.
> >
> > 
> >
> > > **classes.dex** =>
> > >
> > > The classes.dex file (sometimes there are multiple) *contains* all the *compiled bytecode of an Android application*.
> > > 
> > >
> > > Later on, this is what we will decompile into Java source files.
> >
> > 
> >
> > > **resources.arsc** =>
> > >
> > > The *resources.arsc* file *contains* *metadata* about the *resources and the XML nodes of the compiled resource* files like **XML layout files, drawables, strings, and more**. 
> > > 
> > >
> > > It also contains information about their **attributes** (like width, position, etc) and the **resource IDs**, which are used globally by both Java and XML app files in the app. 
> > > 
> > >
> > > This file is compressed into a binary form that is read into memory during *runtime*. 
> > > 
> > >
> > >
> > > Apktool can also decompress these files and output them into a humanly-readable format for you to explore.
> >
> > 
> >
> > > **res/** =>
> > >
> > > The *“res”* folder *contains* **compressed binary XML versions of the resource XML** files that are paired with the *resources.arsc* file during runtime to read images, translations, etc. 
> > > 
> > >
> > >
> > > These XML files are in the same binary format as the AndroidManifest.xml file and can be easily decoded with apktool.
> >
> > 
> >
> > > **lib/** =>
> > >
> > > 
> > >
> > > Not all Android apps contain a lib/ folder, but any app with native C++ libraries will. 
> > > 
> > >
> > > Within this folder, you will find different folders per-architecture, each one containing *.so files* specifically compiled for that target architecture such as *“armeabi-v7a” and “x86”*. 
> > > 
> > >
> > >
> > > This is also why you cannot install an app on an x86 device without it providing x86-compiled libs (Google for “INSTALL_FAILED_NO_MATCHING_ABIS”).









## #2. Lets learn more about Android Architecture



![Image for post](https://miro.medium.com/max/1384/0*0tl5SreIWTWtflrs.png)







> > ### 1. **System Apps or Application Layer:** 
> >
> > Applications That we use daily like **Messages** 
> >
> > all the applications we install belong to this layer, such as WeChat, Plants vs. Zombies.
>
> 
>
> > ### 2. **JAVA API Framework:** 
> >
> > The APIs that programmers use for development in **java** and **Kotlin**.
>
> 
>
> > ### 3. **Android Run time:**
> >
> > Translates Dalvik (Android JVM) byte codes into **native instructions**.
>
> 
>
> > ### 4. **Native C/C++ Libraries:**
> >
> > These libraries mostly used in android implementation and does not have much work to do with application developers except NDK developers.
>
> 
>
> > ### 5. **HAL:**
> >
> > provides high level API for hardware management.
>
> 
>
> > ### 6. **Linux Kernel:**
> >
> > 
> >
> > Linux core, the Android system is modified based on the Linux system. 
> >
> > The bottom layer of Android is Linux, and most of them are some drivers for operating hardware, such as 
> >
> > ​	**Display Driver, Audio Drivers, and so on**.







```Understand now with example```



```
Example: Alarm clock application.

The function of the alarm clock application is actually to play music regularly. The alarm clock application calls MediaPlayer in the APPLICATION and FRAMEWORK layer, and MeidaPlayer accesses the Media and Framework in the LIBRARIES layer, and the Media and Framework uses C language to operate Andio Drivers to play music.
```









### #3. Let's learn more on AndroidManifest.xml =>



> We know this file describes essential information about our app to the Android build tools, the Android operating system, and Google Play



> It plays an important role for every android application. 
>
> 
>
> 
>
> In this file the android developer determines the *permissions* that the application will require, *actions* that the application can perform and general other *activities*.



**Among many other things, the manifest file is required to declare the following:**

- The app’s package name, which is used by Android build tools to determine the location of code entities when building your project.
- The components of the app, which include all activities, services, broadcast receivers, and content providers.
- The permissions that the app needs in order to access protected parts of the system or other apps.
- The hardware and software features the app requires, which affects which devices can install the app from Google Play.





> This file is crucial and thus we as a pentester must check this file for juicy info and any misconfiguration related this  like =>



> ### allowBackup Flag :
>
>
> The **android:allowBackup** attribute defines whether application data can be backed up and restored by a user who has enabled usb debugging.
>
>
> If *true*  => it allows an attacker to take the backup of the application data via adb even if the device is not rooted.
>
> 
>
> Therefore applications that handle and store sensitive information such as card details, passwords etc. should have this setting explicitly set to **false** because by default it is set to **true** to prevent such risks.



```
<application
android:allowBackup=”false”
</application>
```





> ### debuggable Flag: 
>
>
> The **android:debuggable** attribute defines whether the application can be debugged or not. 
>
>
> If *true* => then an attacker can access the application data by assuming the privileges of that application and can even run arbitrary code under that application permission
>
> 
>
>
> In the case of non-debuggable application, attacker would first need to root the device to extract any data.
>
> 
>
> Android applications that are not in the production state are expected to have this attribute set to **true** to assist the developers however before the actual release of the application this tag should be set to **false**.



```
<application
android:debuggable=”false”
</application>
```







> ### Permissions :
>
> 
>
> The **android:protectionLevel** attribute defines the procedure that the system should follow before grants the permission to the application that has requested it. 
>
> 
>
>
> The purpose of a *permission* is to protect the privacy of an Android user.
>
>
> Android apps must request permission to access sensitive user data (such as contacts and SMS), as well as certain system features (such as camera and internet)
>
> 
>
> Depending on the feature, the system might grant the permission automatically or might prompt the user to approve the request.
>
> 
>
> Permissions are divided into several protection levels. The protection level affects whether runtime permission requests are required.
> 
>
> The protection levels that affect third-party apps are:
> 
>
> - normal
> - dangerous
> - signature
> - signatureOrSystem
>
> ```
> <permission>
> android:protectionLevel=”signature”
> </permission>
> ```
>

> NOTE :
>
>
> From Android 7.0 the security architecture is improved a lot. So this setting doesn't mean any significant problem
>
> 
>
> So, concentrate on *custom permission were defined by the developer.*



> The value can be set to one of the following strings:
>
> 
>
> **“normal” :-** The default value. A lower-risk permission that gives requesting applications access to isolated application-level features, with minimal risk to other applications, the system, or the use
>
> 
>
> **“dangerous”:**- A higher-risk permission that would give a requesting application access to private user data or control over the device that can negatively impact the user. Because this type of permission introduces potential risk, the system may not automatically grant it to the requesting application. For example, any dangerous permissions requested by an application may be displayed to the user and require confirmation before proceeding
>
> 
>
> “**signature”:-** A permission that the system grants only if the requesting application is signed with the same certificate as the application that declared the permission. If the certificates match, the system automatically grants the permission without notifying the user or asking for the user’s explicit approval





> ### `<android:sharedUserId>`:
>
> 
>
> * The name of a Linux user ID that will be shared with other applications
> * By default, Android assigns each application its own unique user ID
> * if this attribute is set to the same value for two or more applications, they will all share the same ID — provided that they are also signed by the same certificate.
> * Application with the same user ID can access each other’s data and, if desired, run in the same process.



> ### `<uses-permission>`: 
>
>
> Requests a permission that the application must be granted in order for it to operate correctly. Permissions are granted by the user when the application is installed, not while it’s running.
>
> 
>
> SYNTAX:
>
> ```
> <uses-permission android:name="string" />
> ```
>
> **android:name**
> The name of the permission such as “android.permission.CAMERA” or “android.permission.READ_CONTACTS



> ## External Storage:
>
>
> Applications that have the permission to copy data to external storage should be reviewed to ensure that no sensitive information is stored.
>
> 
>
> ```
> <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
> ```
>
> 





> ## Application Components:
>
> 
>
> * Keep an eye on Application Components
> * Activities, Services, Content Providers and Broadcast Receivers can all be exported
> * all of them they should be reviewed  for => any sensitive action that could be exposed to malicious third parties.



> ## Intents:
>
> Intents can be used to launch an activity, to send it to any interested broadcast receiver components, and to communicate with a background service. Intents messages should be reviewed to ensure that they doesn’t contain any sensitive information that could be intercepted.
>
> ```
> <intent-filter>
> <action android:name="string" />
> <category android:name="string" />
> </intent-filter>
> ```



------





