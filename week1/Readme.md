<span style="color: green"> Some green text </span>
<font color="green"> Some green text </font>

<span style="color:red">매니패스트 태그 시작 .</span> 
# 1. Manifest란 무엇인가
> 모든 앱 프로젝트는 프로젝트 소스세트의 루트에 AndroidManifest.xml 파일이 있어야함. <span style="color:red">매니패스트 태그 시작 .</span> 

```Kotlin
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"  <span style="color:yellow">매니패스트 태그 시작 .</span> 
    package="com.example.rc_test">
    
    <application
        android:allowBackup="true" 
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.RC_test">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```
