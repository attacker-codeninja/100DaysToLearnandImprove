# 			Day 3 => Continue Android Basics Security Testing Notes

------





```
Still I am sticking to Basics

Let's Memorize what I learned till now from 2 days and of today
```



> * Android is an open source Linux-based operating system for mobile devices
>   (smartphones and tablet computers)
>
> * Programming Language vary => Java, Kotlin, C/C++
>
> * Different Types of Mobile Applications
>
>   * Native Apps
>
>     * > Native applications that reside in the mobile operating system are pushed/installed through the respective app stores.
>       >
>       > These apps are typically built using development tools and languages 
>       >
>       > e.g. => (Xcode and Objective C, Swift for iOS apps, and Android Studio and Java for Android apps) 
>       >
>       >
>       > and are designed for a particular platform and can take advantage of all the device features, such as 
>       >
>       > ​	the usage of the camera, GPS, phone contact list, and so on.
>
>   * Mobile web Apps
>
>     * > non-native applications
>       >
>       > Most of them are 
>       >
>       > ​	HTML5, JavaScript, and CSS applications 
>       >
>       > with a web interface supporting the native application look and feel.
>       >
>       > Users first access them as they would access any
>       > 	other web page, and these are mobile-optimized web pages.
>
>   * Hybrid Apps
>
>     * > combination of
>       > 	web- based content and native components 
>       >
>       > accessing services on the mobile device, most notably, storing or using storage.
>       >
>       > 
>       >
>       > Or can say => client-server  architecture of mobile applications
>
> * Android is based on DVM [Dalvik Virtual Machine] like JVM [Java Virtual Machine ]
>
> * Architecture =>
>
>   * Applications => like alarm, browser, wechat etc
>   * Application Frameworks  => Like => Content Providers, Managers for Activity etc, View System
>   * Native Libraries => Like => SQLITE, Audio Manager, LIBC, Media Framework, OpenGL
>   * Android Runtime => Core Libraries, Dalvik VM
>   * HAL [Hardware Abstraction Layer] => AUDIO, Bluetooth, Camera, External Storage, Graphics, Media, Sensors, TV etc
>   * Linux Kernel => Drivers for Audio, Binder, Bluetooth,Camera,Display, Keypad, USB,WiFi etc
>
> * Android File is => zip file => with an extension of .apk 
>
>   * i.e. APK files are nothing but ZIP files that are based on the JAR file format.
>
> * We can decompile/disassemble *.apk* => using **apktool**
>
> * Structure of an APK File is =>
>
>   * META-INF/ => files related to signature scheme
>   * lib/ => folder containing native compiled code => ARM,MIPS, X86,X64
>   * assets/ => folder containing application specific files
>   * res/ => folder containing all  the resources of the app
>   * classes.dex or many .dex files => Dalvik bytecode of the app
>   * AndroidManifest.xml => most important file => Essential Information about the app like **Permission**, **Components** etc
>
> * Usefull Data Storage
>
>   * For User Applications
>
>     * ```
>       /data/app/<package-name>/
>       ```
>
>   * For Shared Preferences Files
>
>     * ```
>       /data/app/<package-name>/shared_prefs
>       ```
>
>   * For SQLite Databases
>
>     * ```
>       /data/app/<package-name>/databases/
>       ```
>
>   * For Internal Storage
>
>     * ```
>       /data/app/<package-name>/files/
>       ```
>
> * Android Application Components
>
>   * Activities
>     * We can view the Application on Screen as Display
>     * Single screen with a user interface (UI) and it will acts an entry point for the user’s to interact with app. 
>   * Services
>     * Application that run in background even user close it, and can Trigger Notification and also brodcast Intents
>   * Content Providers
>     * Used to Manage the Application Data and also can interact with  SQL Database
>     * Can share data between application
>   * Intents
>     * Bind applications to Start/Stop Activities and Services
>   * Broadcast Services
>     * This enable to listen the Intents
>     * allow a system to deliver events to the app like sending a low battery message to the app.
>     * It broadcasts to let other apps know that required data available in a device to use it.
>     * So, Broadcast Receivers use status bar notifications to let the user know that broadcast event occurs.
>
>   ```
>   .java file => Java Compiler Compiles .java file to => .class java bytecode
>   
>   .class file => Dalvik Compiler then Compiles using dex  compiler to => .dex file
>   ```
>
> * AndroidManifest.xml file
>
>   * very crucial file
>   * Having all information about apk packages
>   * We must check this file for any misconfiguration as a pentester perspective





### #1. Understand AndroidManifest.xml file more



![image-20201230174335704](/home/code/.config/Typora/typora-user-images/image-20201230174335704.png)



![image-20201230174407874](/home/code/.config/Typora/typora-user-images/image-20201230174407874.png)



![image-20201230174429368](/home/code/.config/Typora/typora-user-images/image-20201230174429368.png)











### #2. What happens when a Mobile Application  Launch



![image-20201230175651114](/home/code/.config/Typora/typora-user-images/image-20201230175651114.png)





There are called **Activity LifeScycle**





### #3. Services Types => Bound & UnBound



> ### UnBound =>
>
> 
>
> > An unbound service is an application component that starts the service and will
> > continue to run in the background even when the original component that initiated it is destroyed. 
>
> > *Example* =>
> >
> > on turning on Bluetooth, a service would be available and ready to discover other devices in the background.



> ### Bound =>
>
> 
>
> > A bound service can bind from one application activity or component to another
> > using *bindservice()*
>
> > This service would run as long as the activities or components
> > are bound to it
>
> > It is destroyed only when they are unbound.



![image-20201230180448329](/home/code/.config/Typora/typora-user-images/image-20201230180448329.png)







> The important methods in a service lifecycle are:
>
>
> •  onStartCommand(): This method is called when startService() is called
>
> 
>
> • onBind(): This method is used when another component wants to bind with
> the service calling bindService()
>
>
> • onCreate(): All the service initiation is done by calling this method; it is
> never called again
>
>
> • onDestroy(): This method is called or used to destroy the service in order to
> clean up the created threads, receivers, and so on





### #4. Broadcast Reciever



![image-20201230180640126](/home/code/.config/Typora/typora-user-images/image-20201230180640126.png)



That above is one of example of Broadcast Receiver







### #5.  Vulnerabilities related to Mobile



![img](https://www.nowsecure.com/wp-content/uploads/2016/10/OWASP-Mobile-Top-10.png)









![img](https://static.packt-cdn.com/products/9781785883378/graphics/B05055_01_08.jpg)







### #6. Analysis of Android Testing



* Static Analysis
* Dynamic Analysis
* Reverse Engineering
* Local File Analysis
* Network and Web Traffic
* Analysis for 
  * Intents
  * Content Providers
  * Activites
  * Services
  * Broadcast Services





