# blinkpay_mobile_app_demo

A Flutter project showcasing how to use WebView for e-commerce functionality with the BlinkPay payment gateway.

## Getting Started

The main file is `lib/main.dart`. The app is built using Flutter SDK.

### Dependencies
```bash
flutter doctor
flutter pub outdated
flutter pub upgrade
flutter pub upgrade --major-versions
flutter pub get
```

### Deep linking
Edit `android/app/src/main/AndroidManifest.xml` to include uses-permission and the following intent-filter for deep linking.
```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android">
    <uses-permission android:name="android.permission.INTERNET" />
    <application
            android:label="blinkpay_mobile_app_demo"
            android:name="${applicationName}"
            android:icon="@mipmap/ic_launcher">
        <activity
                android:name=".MainActivity"
                android:exported="true"
                android:launchMode="singleTop"
                android:taskAffinity=""
                android:theme="@style/LaunchTheme"
                android:configChanges="orientation|keyboardHidden|keyboard|screenSize|smallestScreenSize|locale|layoutDirection|fontScale|screenLayout|density|uiMode"
                android:hardwareAccelerated="true"
                android:windowSoftInputMode="adjustResize">
            <!-- Specifies an Android theme to apply to this Activity as soon as
                 the Android process has started. This theme is visible to the user
                 while the Flutter UI initializes. After that, this theme continues
                 to determine the Window background behind the Flutter UI. -->
            <meta-data
                    android:name="io.flutter.embedding.android.NormalTheme"
                    android:resource="@style/NormalTheme"
            />
            <intent-filter>
                <action android:name="android.intent.action.MAIN"/>
                <category android:name="android.intent.category.LAUNCHER"/>
            </intent-filter>

            <!-- Deep Link Configuration -->
            <intent-filter>
                <action android:name="android.intent.action.VIEW"/>
                <category android:name="android.intent.category.DEFAULT"/>
                <category android:name="android.intent.category.BROWSABLE"/>
                <data android:scheme="blinkpay" android:host="test-app" android:pathPrefix="/return"/>
            </intent-filter>
        </activity>
        <!-- Don't delete the meta-data below.
             This is used by the Flutter tool to generate GeneratedPluginRegistrant.java -->
        <meta-data
                android:name="flutterEmbedding"
                android:value="2" />
    </application>
    <!-- Required to query activities that can process text, see:
         https://developer.android.com/training/package-visibility and
         https://developer.android.com/reference/android/content/Intent#ACTION_PROCESS_TEXT.

         In particular, this is used by the Flutter engine in io.flutter.plugin.text.ProcessTextPlugin. -->
    <queries>
        <intent>
            <action android:name="android.intent.action.PROCESS_TEXT"/>
            <data android:mimeType="text/plain"/>
        </intent>
    </queries>
</manifest>
```

### Building the app
```bash
flutter build apk
```