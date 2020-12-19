
## Table of Contents

 * [Introduction](#introduction)
 * [Installation](#installation)
 * [Configuration ](#configuration )
 * [Supported Environments](#supported-environments)
 * [Sample Code](#Sample-Code)
 * [License](#license)
 
 
## Introduction
    HMS ML Kit BCR Codelab code encapsulates APIs of the HUAWEI ML Kit SDK and BCR feature. 
    It provides recognise your Bank Card number and copy for enter the forms without losing time With ML Kit.
    The bank card recognition service can quickly recognize information such as the bank card number, covering mainstream bank cards such as China UnionPay, American Express, Mastercard, Visa, and JCB around the world.
    It is widely used in finance and payment scenarios requiring bank card binding to quickly extract bank card information, realizing quick input of bank card information.
    Please refer to this link for more information : https://developer.huawei.com/consumer/en/doc/development/HMSCore-Guides-V5/bank-card-recognition-0000001050038118-V5

    Before you use this codelab, it's assumed that you already have a HUAWEI developer account and have already created an app to implement the HMS ML Kit. 
    If you haven't, please refer to https://developer.huawei.com/consumer/en/doc/start/introduction-0000001053446472 
    and https://developer.huawei.com/consumer/en/doc/development/AppGallery-connect-Guides/agc-introduction.
    
## Installation
    Before using HMS ML Kit BCR Codelab code, check whether the Android Studio environment has been installed. 
    Download the HMS ML Kit BCR Codelab project by zip or clone in Github.
    Wait for the gradle build in your project.
    
## Supported Environments
	•	Android Studio 3.x or later version
	•	Java JDK 1.8 or later version
	•	EMUI 5.0 or later version
	•	HMS Core (APK) 5.0.1.300 or later version
	•	Android 4.4 or later

## Configuration 
    1. Register and sign in to HUAWEI Developers.
    2. Create a project and then create an app in the project, enter the project package name.
    3. Go to Project Settings > Manage APIs, find the ML Kit API, and enable it.
    4. Go to Project Settings > General information, click Set next to Data storage location under Project information, and select a data storage location in the displayed dialog box.
    5. Download the agconnect-services.json file and place it to the app's root directory of the project.
    6. Add the Maven repository address maven {url 'https://developer.huawei.com/repo/'} and plug-in class path 'com.huawei.agconnect:agcp:1.4.1.300' to the project-level build.gradle file.
    7. Add apply plugin: 'com.huawei.agconnect' to the last line of the app-level build.gradle file.
    8. Configure the dependency com.huawei.hms:ml-computer-card-bcr:2.0.3.301 in the app-level buildle.gradle file.
    9. Configure the dependency com.jakewharton:butterknife:10.2.3 in the app-level buildle.gradle file.
    10. Synchronize the project.
	
## Sample Code
    HMS ML Kit BCR Codelab code uses the Client structure in the project.The following describes methods in the Client structure.

    1) Create and initialize of MLBcrCapture.Callback.
    You can obtain the initialized MLBcrCapture.Callback instance 
    Code location com.hms.codelab.mlkit.bankcardrecognition/MainActivity.kt
    
    2) Create and initialize of MLBcrCaptureConfig.Factory
    You can obtain the initialized MLBcrCaptureConfig object 
    Code location com.hms.codelab.mlkit.bankcardrecognition/MainActivity.kt
    
    3) Create and initialize of MBcrCapture 
    You can obtain the initialized MLBcrCaptureFactory.getInstance().getBcrCapture(config) object 
    Code location com.hms.codelab.mlkit.bankcardrecognition/MainActivity.kt
    
    4) Invoke checkAndRequestPermissions function when click the R.id.ivCardImage, R.id.btnTakePhoto buttons
    You can request permissions
    Code location com.hms.codelab.mlkit.bankcardrecognition/MainActivity.kt
    
    5) Invoke startMLBcrCaptureCameraStream function if permissions were has got granted in onRequestPermissionsResult method
    You can start MLBcrCaptureCameraStream for recognition
    Code location com.hms.codelab.mlkit.bankcardrecognition/MainActivity.kt
    
    6) Invoke displaySuccessAnalyseResults function to show recognised card details
    You can obtain Analyse Result details details with MLBcrCaptureResult param in Callback onSuccess
    Code location com.hms.codelab.mlkit.bankcardrecognition/MainActivity.kt
    
    7) Invoke copyTextToClipboard function with view param when click the R.id.tvCardNumberAll or click other textViews thats are showing recognised card numbers partially
    You can obtain coppied card number
    Code location com.hms.codelab.mlkit.bankcardrecognition/MainActivity.kt

##  License
    HMS ML Kit BCR Codelab is licensed under the [Apache License, version 2.0](http://www.apache.org/licenses/LICENSE-2.0).
