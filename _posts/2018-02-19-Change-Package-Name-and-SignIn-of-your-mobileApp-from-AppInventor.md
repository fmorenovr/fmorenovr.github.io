---
layout: post
title:  "Change your Package name and SingIn on google play your app created using App Inventor."
date:   2018-02-19 12:15:12 -0500
categories: Tools
---
## App Inventor

You should check from my app inventor tutorial [here][apptutorial].

## Change Package Name

* First, you should know that the package name of the app created with AppInventor is like `appinventor.ai_youremail.appname`.  

* So, If we want change our `appinventor.ai_felipe_moreno_v.rgobeApp` package name to `com.rolnomev.rgobe`, we must follow this steps.

   * Download **apkTool** from this repository [apktool][apkToolRepo] for linux or follow the respective steps for others Operating Systems [here][apkToolURL].

   * Once download (I downloaded [apktool_2.3.1.jar][apkToolVersion] version), you can use it.
   
* Then, Build your apk project from AppInventor. My apk is named rgobeApp.apk.

   * Then, I uncompress my apk file writing this:
   
         java -jar apktool_2.3.1.jar d rgobeApp.apk
   
     ![apkToolRun][apkToolRunBash]

     This command generates a file directory with name `rgobeApp` of our android project like:
     
     ![apkToolDir][apkToolDir]

   * Next, modify `AndroidManifest.xml` and other files in project, I used Gedit:
   
     ![androidmanifest][AndroidManifestChange]
     
     Also, you must change files in `/smali/appinventor/ai_felipe_moreno_v/rgobeApp/` (in this case).  
     Modify in these file the regular text from **Lappinventor/ai_felipe_moreno_v/rgobeApp/** to **Lcom/rolnomev/rgobe** in all files of that directory path.
     
[comment]: <> (   * Next, export AppInventor (.aia) file here: )
   
[comment]: <> (      ![AIaia][aiAiaFile] )
      
[comment]: <> (   * Next, go to [AppyBuilder](http://gold.appybuilder.com/) page and import your project: )

   * Next, create directories path as your new package name like: `/smali/com/rolnomev/rgobe`.

   * Next, copy files from `/smali/appinventor/ai_felipe_moreno_v/rgobeApp` to new dir `/smali/com/rolnomev/rgobe`.
   
   * Once your finish to replace all coincidences, yo should to rebuild the apk, writing this:
   
          java -jar apktool_2.3.1.jar b rgobeApp
     
     ![apkToolBuild][apkToolBuild]
     
   * Now, you can install your apk in your mobile phone and enjoy your app with new package name.
   
   
## Notes

* You can upload your apk in google play with your new package name, instead the package name that appinventor gives you by default.

* Maybe this method will be deprecated as time passes.


[apptutorial]:           /tools/Installing-App-Inventor
[apkToolRepo]:           https://bitbucket.org/iBotPeaches/apktool/downloads/
[apkToolURL]:            https://ibotpeaches.github.io/Apktool/install/
[apkToolVersion]:        /files/apktool_2.3.1.jar
[apkToolRunBash]:        /assets/tools/apkTool/runningApkTool.png
[apkToolDir]:            /assets/tools/apkTool/dirApkTool.png
[AndroidManifestChange]: /assets/tools/apkTool/changePackageName.png
[aiAiaFile]:             /assets/tools/appInventor/generateAiaFile.png
[apkToolBuild]:          /assets/tools/apkTool/buildingApkTool.png
