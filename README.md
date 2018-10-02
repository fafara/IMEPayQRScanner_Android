# IMEPayQRScanner_Android
IME Pay QR Code Scanner SDK for Android



"IME Pay QR Scanner SDK" is designed to be used by the Third Party Apps, to scan the QR Code issued By IME Pay to its Merchants.



# Main Objective

  - Scan QR Code of IME Pay Merchants
  - Return the Merchant Code to the App implementing the SDK after Scanning
  - Easy Integration with  few lines of code


 
  


# How to implement IME PAY QR SDK in Android 

 ### 1. Add following permission in manifest
  	<uses-permission android:name="android.permission.CAMERA" />   


### 2. Register this Activity in your App Manifest 
```sh
 <activity android:name="lib.swifttechnology.merchantscanner.BarcodeCaptureActivity"     
   android:configChanges="orientation" android:screenOrientation="portrait"     
   android:theme="@style/Theme.AppCompat.Light.NoActionBar" 
   android:windowSoftInputMode="adjustPan|stateHidden" /> 
 ```

 
 ### 3. Initialize the IMESCannerHandler class and call openScannerActivity method with request code
 ```sh
 IMEScannerHandler scannerHandler; 
 scannerHandler = new IMEScannerHandler(MainActivity.this);
 scannerHandler.openScannerActivity(100);
 ```

 
 ### 4. Override the onActivityResult and check for your request code. On ResultOk, you can get the MerchantCode from intent with key name “BarCode”
 ```sh
@Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        if (requestCode == 100 && resultCode == RESULT_OK) {
            if (data != null) {
                String merchantCode = data.getStringExtra("BarCode");
} else {
                //  FAILED
            }
        } else {
            super.onActivityResult(requestCode, resultCode, data);
        }
    }
```
Note:  
-	For Invalid QR, SDK returns -1 as Merchant Code. App should ignore this value. 
-	Make sure NDK is enabled and properly integrated in the App 
