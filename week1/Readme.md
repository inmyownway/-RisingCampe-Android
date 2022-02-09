
# 1. Manifest란 무엇인가
   > 모든 앱 프로젝트는 프로젝트 소스세트의 루트에 AndroidManifest.xml 파일이 있어야함. 
    
   ## AndroidManifest.xml
   
   ### 매니페스트 파일은 다음고 같은 내용을 선언해야함.
   > 1. 앱의 패키지 이름
   > 2. 앱의 구성요소
   > 3. 앱이 시스템 또느 다른 앱의 보호된 부분에 액세스하기 위해 필요하 권한
   > 4. 앱에 필요한 하드웨어 및 소프트웨어 기능
   
   ```Kotlin
   <?xml version="1.0" encoding="utf-8"?>
   <manifest xmlns:android="http://schemas.android.com/apk/res/android"  // 매니페스트 태그 시작
       package="com.example.rc_test">                                    // package 속성: 앱 패키지 정의



        <application                                                      // 앱 태그 시작
            android:allowBackup="true"                                    
            android:icon="@mipmap/ic_launcher"                            // 앱의 주요 설정 정보를 담고있음
            android:label="@string/app_name"
            android:roundIcon="@mipmap/ic_launcher_round"
            android:supportsRtl="true"                                    // 백어 기능 사용 여부, 아이코 표시되는 앱 이름, 쓰기 방향, 테마 등
            android:theme="@style/Theme.RC_test">




            <activity android:name=".MainActivity"                        // 액티비티 태그 내부 인텐트 필터 태그 존재
                android:exported="true">
                <intent-filter>
                    <action android:name="android.intent.action.MAIN" />          // 액션 태그오 카테고리 태그존재 => 첫화면 결정
                    <category android:name="android.intent.category.LAUNCHER" />
                </intent-filter>
            </activity>
        </application>
    </manifest> 
   ```
   
 
    
