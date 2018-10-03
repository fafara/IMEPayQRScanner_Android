# IMEPayQRScanner For Android
IME Pay QR Code Scanner SDK for Android



"IME Pay QR Scanner SDK" is designed to be used by the Third Party Apps, to scan the QR Code issued By IME Pay to its Merchants.



# Main Objective

  - Scan QR Code of IME Pay's Merchants
  - Return the Merchant Code to the App implementing the SDK after Scanning
  - Easy Integration with  few lines of code


 ![Screenshot](doc-qr-code.jpg)

 
  


# How to implement IME PAY QR SDK in Android 

### 1.Add the following in your app's build.gradle file:
```sh
compile 'ib.swifttechnology.merchantscanner:IMEMerchantScanner:1.0.0'
```

 ### 2. Add following permission in manifest
 ```sh
  	<uses-permission android:name="android.permission.CAMERA" />   
   ```


### 3. Register this Activity in your App Manifest 
```sh
 <activity android:name="lib.swifttechnology.merchantscanner.BarcodeCaptureActivity"     
   android:configChanges="orientation" android:screenOrientation="portrait"     
   android:theme="@style/Theme.AppCompat.Light.NoActionBar" 
   android:windowSoftInputMode="adjustPan|stateHidden" /> 
 ```

 
 ### 4. Initialize the IMESCannerHandler class and call openScannerActivity method with request code
 ```sh
 IMEPayScannerHandler scannerHandler; 
 scannerHandler = new IMEPayScannerHandler(MainActivity.this);
 scannerHandler.openScannerActivity(100);
 ```

 
 ### 5. Override the onActivityResult and check for your request code. On ResultOk, you can get the MerchantCode from intent with key name “BarCode”
 ```sh
@Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        if (requestCode == 100 && resultCode == RESULT_OK) {
            if (data != null) {
                String merchantCode = data.getStringExtra(IMEPayScannerConstant.BARCODE);
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
