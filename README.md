# PhoneGap Plugin BarcodeScanner
================================

## About

This is a fork of the original repo (https://github.com/rarestep/phonegap-plugin-barcodescanner). The main motivator for creating our own fork was due to the scan `beep` sound in android being very loud and buggy. When a barcode is scanned, the sound would ignore the volume setting, play at the max volume, and loop while the scanner "worked", sometimes up to 4 times. This fork remedies those problems as well as adds a more soothing, shorter beep.

## Making changes

So far, I've only had to make changes to the android portion, specifically the Zebra Crossing library. Run these commands to rebuild once you've made your edits to appropiate files.

```
> cd phonegap-plugin-barcodescanner/src/android/LibraryProject
> echo "sdk.dir=/path/to/android/sdk" > local.properties # Mine was /Users/jorgevaldivia/Library/Android/sdk
> ant release
> cp bin/classes.jar ../com.google.zxing.client.android.captureactivity.jar

# commit changes and push to github
```

Once those are complete you will have a new build that's ready to be added to an ionic project. You will most likely need to remove your plugin and platforms from your project and add them again.

```
# In an ionic project
> ionic platforms rm android
> ionic plugin rm phonegap-plugin-barcodescanner
> ionic plugin add https://github.com/rarestep/phonegap-plugin-barcodescanner.git
> ionic platforms add android
> ionic build android
> ionic run android
```

That's it! The app should be running on your device and the changes made to the barcode scanner will be evident.
