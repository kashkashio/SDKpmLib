# SDKpmLib
KPMBro SDK Android Library

### Integration Guide:
* On App AndroidManifest file make sure to give permission
```
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```
* Download or clone to get the AAR (Android Archive) in this repository.

* On Android Studio project create a directory named libs under your app main directory (should be project/app/src/main/libs)

* Copy the AAR into your project in the libs directory of your app module we created before.

* On project level build.gradle file make sure to add this under allprojects -> repositories

```
flatDir {
    dirs 'src/main/libs'
}
```
E.g
```
allprojects {
    repositories {
        google()
        jcenter()
        flatDir {
            dirs 'src/main/libs'
        }
    }
}
```
* In  your module build.gradle file make sure you point to the right directory so the AAR can be loaded.

```
dependencies {
    implementation files('src/main/libs/sdkpm.aar')
}
```
* In your Main Activity add this import:
 ```
 import com.kpmbro.sdkpm.SDKpm;
 ```
* To initiate the sdk - In your Main Activity onCreate function add this code:
 ```
 SDKpm.start(this, "NEED TO PUT HERE GAID", "ADVCODE");
 ```
the init requires 3 parameters:
1. (Context) context - The app context - on activity onCreate will be "this".
2. (String) GoogleAdvertiserID - the IDFA of the user which can be retrieved by using google services library.
3. (String) advCode - Your Advertiser ID number on platform.

*If the strings will be empty the sdk will throw exception but wont crash tough the sdk wont work.
an error message is being thrown.*

**How to get IDFA can be found [here](https://stackoverflow.com/questions/25846108/how-to-get-advertising-id-in-android-programmatically)**

