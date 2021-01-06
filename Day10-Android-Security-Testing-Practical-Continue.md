# Day 10- Practical Android Security Testing

---

### #Level 7. Export

![](https://i.imgur.com/kmJ0jdU.png)

![](https://i.imgur.com/dDB3hIN.png)


> So, there is a hidden service i need to find
> Let's check hint now

![](https://i.imgur.com/pwbIudv.png)

 Hint => what is an exported activity?

 ```Lets google it```
 Got some good results =>

 1. https://cwe.mitre.org/data/definitions/926.html
 2. https://stackoverflow.com/questions/63633709/android-vulnerability-exported-activity-true


![](https://i.imgur.com/ArwkD7e.png)

From google i came to know =
> Improper export of android application components

> So, its all about base on activities

unprotected activity(that means that any other app can have access to it) that when it launches have access to the local storage files

> Activity in Android is where all activities interact with users, because all application screens must be “attached” on an Activity.


> AndroidManifest.xml is very important file and there we need to check **activity** and **android: exported** . 

>If this property has a value of **true** , that activity may be triggered by other applications.

```
<activity android:exported="true" android:name="com.revo.evabs.ExportedActivity"/>
```
> Google => adb command to start activity
> ```am start -n yourpackagename/.activityname```

> OR

```
adb shell am start -n com.example.demo/com.example.test.MainActivity
```

Let's try this

```adb shell am start -n com.revo.evabs/.ExportedActivity```

![](https://i.imgur.com/SmRVy4K.png)

Fantastic

> Flag => EVABS{exp0rted_activites_ar3_harmful}

![](https://i.imgur.com/aQl4zQl.png)




```
What I Learn ?

In AndroidManifest.xml file look up for => export activities andif it true then start this activity using adb command and see if any sensitive info is there  or not
```



------



### #Level 8. Decode





![](https://i.imgur.com/Yy7eO43.png)

![](https://i.imgur.com/UeYiHyN.png)

> Ok, Again google => Reversing apk to java
> https://stackoverflow.com/questions/12732882/reverse-engineering-from-an-apk-file-to-a-project


![](https://i.imgur.com/mh25UaV.png)

Now lets use tool **jd-gui**

![](https://i.imgur.com/vb44yCG.png)

![](https://i.imgur.com/dPYBQDP.png)

> Let's decode it

Let's use => **https://gchq.github.io/CyberChef/**

![](https://i.imgur.com/WXCU45D.png)


```
RVZBQlN7bmV2M3Jfc3QwcmU=
X3MzbnMhdGl2M19kYXRh
XzFuXzdoM19zMHVyY2VjMGRl
```

```
Flag => EVABS{nev3r_st0re_s3ns!tiv3_data_1n_7h3_s0urcec0de
```

![](https://i.imgur.com/4H66yQw.png)



```
What I learn?

Reverse engineering the apk file using apk + d2j-dex2jar + jd-gui and then check hardcoded strings to see if any sensitive info is there or not
```



---



# Level 9. Smali Injection
![](https://i.imgur.com/GMFG8nm.png)

![](https://i.imgur.com/PTNVXb8.png)

![](https://i.imgur.com/qS3lpZU.png)

Let's check the jar file on jd-gui

![](https://i.imgur.com/iq5ynL2.png)

Check this code carefully

![](https://i.imgur.com/l61dujg.png)

> So, i see there is variable **SIGNAL** and by default its value is **LAB_OFF**

> If this variable **SIGNAL** become **LAB_ON** then we can see it will print **FLAG**

Once i click on **TURN ON** , I got **Access Denied**

![](https://i.imgur.com/KWrHEF1.png)

Let's google => how to repackaging apk file

```
https://itzone.com.vn/en/article/learn-the-format-of-ctf-reverse-android-decompile-and-patch-the-apk-file/

https://reverseengineering.stackexchange.com/questions/8044/repackaging-apk-file-using-baksmali-and-smali

https://techsable.com/how-to-unpack-and-repack-apk-file-on-android/

http://webpages.eng.wayne.edu/~fy8421/16sp-csc5991/labs/lab5-instruction.pdf
```

So, there is many resouces i got but
https://itzone.com.vn/en/article/learn-the-format-of-ctf-reverse-android-decompile-and-patch-the-apk-file/

This one i find very useful

Now, lets do this step by step

> Step 1 => First decompile the apk file using **apktool** command 

![](https://i.imgur.com/XB637of.png)

> Step 2 => Open the smali file **SmaliInject.smali**


![](https://i.imgur.com/02IiCV9.png)

> Step 3 => Change **LAB_OFF** to **LAB_ON**

![](https://i.imgur.com/V1xWDjS.png)

> Step 4 => Rebuild this apk file into NEW APK File

![](https://i.imgur.com/RO0pL2N.png)

> Step 5 => SIGN APK

![](https://i.imgur.com/NviLQrP.png)

passphrase used = **aakash**

![](https://i.imgur.com/rH3O4TI.png)


Command used =>

```
keytool -genkeypair -v -keystore key.keystore -alias publishingdoc -keyalg RSA -keysize 2048 -validity 10000

jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore ./key.keystore EVABSv4-new.apk publishingdoc

```

![](https://i.imgur.com/KqwdCX2.png)

> We, can see Jar Signed, good for attacker


Now, delete old apk file from genymotion device and install new apk file on device

![](https://i.imgur.com/MAwlLK5.png)

Now run the application on device and click on TURN ON on challenge 9

![](https://i.imgur.com/0Mw26zO.png)

> Flag => EVABS{smali_inj_is_l3thals}





```
What I learn from this challenge ?


We can edit the code and rebuild the new application and still use the normal functions because the Dev has no mechanism to check the code integrity.
```





---



# Level 10. Interception

![](https://i.imgur.com/NJ8cS5y.png)

Hint =>

![](https://i.imgur.com/098UcKn.png)


> So, for his we need to intercept the request using burpsuite proxy

I found **https://blog.ropnop.com/configuring-burp-suite-with-android-nougat/**  

> Above link is very important to setup burpsuite and SSL issues


![](https://i.imgur.com/emeh7Jd.png)

> Flag => EVABS{Always_p!n_SSL_C3rtificate}





```
What I learn ?

This is a risk of android app insecurity due to Dev not implementing SSL Pinning. If an application uses SSL Pinning carefully, the server will not respond to requests we send through Burp.
```

