## Digital Bitbox QR app

![alt tag](img/ios/screen_start.png)

This smartphone app is a general purpose barcode scanner with a minimalist interface. It uses the wildabeast BarcodeScanner plugin. 

For the Digital Bitbox, it is also used to verify QR codes before signing a transaction. This avoids handcrafted man-in-the-middle attacks on compromised computers by verifying that you are signing the correct transaction. 

Just click the button to scan. Plain text is printed as is. JSON-formatted text is pretty-printed. AES-256-CBC encrypted text is decrypted with a user-supplied password, which is set after clicking on the options icon at the bottom of the screen.


## Installation

- [Google Play Store for Android](https://play.google.com/store/apps/details?id=com.digitalbitbox.qr)
- App Store for iOS at a later date


## Installation from source

Requires:
  1. [**Node.js** and **npm**](https://nodejs.org/) (tested with Node.js v4.2.2 and npm v2.14.7)
  2. **Cordova command line interface** installed using npm `sudo npm install -g cordova` (OSX and Linux).
  3. For Android devices: [**Android SDK**](https://developer.android.com/sdk/)
  4. For iOS devices: [**Xcode**](https://developer.apple.com/xcode/)

Command line build and install:

```
git clone --recursive https://github.com/digitalbitbox/QR_app.git
cordova create digitalbitboxQR com.digitalbitbox.qr "DigitalBitboxQR" --copy-from=./QR_app/
cd digitalbitboxQR
cordova platform add android 
cordova plugin add https://github.com/wildabeast/BarcodeScanner
cordova plugin add cordova-plugin-file
npm install bitcore
browserify www/js/main.js -o www/js/app.js
cordova build android
```

To install on an Android phone, connect it to your computer and type  `cordova run android`. [Developer permissions](https://developer.android.com/tools/device.html) are required. 

To install on an iPhone, replace `android` with `ios` and open the file `platforms/ios/Digital Bitbox QR.xcodeproj` in Xcode. An iOS Developer Program membership, or a jailbroke phone, is required.

## Using the app

Scan a plaintext QR code:

![alt tag](img/website_logo_qrcode_small.png)

![alt tag](img/ios/screen_scan_url.png)


Scan an AES-encrypted Digital Bitbox verification QR code:

![alt tag](img/echo_qrcode.png)

![alt tag](img/ios/screen_scan_sign_lock.png)


Set the password for decrypting the Digital Bitbox verification QR code:

![alt tag](img/ios/screen_options.png)
![alt tag](img/ios/screen_pwdialog_keyboard.png)






