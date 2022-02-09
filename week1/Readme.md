
# 1. Manifest란 무엇인가
   > 모든 앱 프로젝트는 프로젝트 소스세트의 루트에 AndroidManifest.xml 파일이 있어야함. 
    
   
   
   ### 매니페스트 파일은 다음고 같은 내용을 선언해야함.
   > 1. 앱의 패키지 이름과 애플리케이션 아이디
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
   
   ### 1. 패키지 이름과 애플리케이션 아이디
   > 매니페스트 파일의 루트 요소는 앱의 패키지 이름에 대한 특성이 필요합니다
   > 위의 코드에서 패키지 이름이 "com.example.rc_test" 인 manifest 파일이 생성되었습니다.
   > 앱을 최종 어플리케이셔 패키지(APK)로 빌드하는 동안 안드로이드 빌드 도구가 패키지 특성으로 사용하느 목적은 2가지 입니다
   > 1. 빌드 도구는 앱에서 생성된 R.java 클래스의 네임스페이스로 이 이름을 적용합니다 , 위의 매니페스트오 함께 R클래스가 com.example.rc_text.R 로 생성
   > 2. 매니페스트 파일내에서 선언된 상대경롱 적용됩니다. <activity android:name=".MainActivity">로 선언된 액티비티가 com.example.myapp.rc_test 인 것으로 확인
   
   > 이처럼 매니페스트의 package 특성에 있는 이름은 액티비티와 기타 앱 코드가 들어 있는 프로젝트의 기본 패키지 이름과 항상 일치해야 합니다. 
   > 그러나 APK가 컴파일 되고나면 package 특성도 앱의 전체적으로 고유한 애플리케이션 ID를 나타낸다는 점을 유의해야 합니다.
   > 빌드 도구가 패키지 이름에 기초하여 위에 작업들을 수행 후, 프로젝트의 프로젝트의 build.gradle 파일에 있는 applicationId 속성에 지정된 값으로 package 값을 대체합니다.
