# 1주차 과제 계획서

> ## 1.Manifest 항목 조사 -> 매니패스트의 용도 및 4대 컴포넌트, 적용한 예시
> ## 2.Palette 항목 조사 -> 각가의 태그들의 역할 태그에서 대표적으로 어떤 속성들을 사용할수 있는지
> ## 3.Linear / Relative / Frame / Table / Grid / Constraint 조사 
> ## 4.레이아웃 활용하여 화면 구축 -> 레이아웃들의 특징들

---



# 1. Manifest란 무엇인가
   > 모든 앱 프로젝트는 프로젝트 소스세트의 루트에 AndroidManifest.xml 파일이 있어야함. 
   > AndroidManifest.xml 는 안드로이드 앱의 메인 환경 파일이며 개발부터 실행 까지 
   > 매니페스트의 역할은 안드로이드 빌드 도구 운영체제 및 Google Play 앱에 관한 필수 정보를 설명한다.
    
   
   
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
                    <action android:name="android.intent.action.MAIN" />          // 액션 태그로  카테고리 태그존재 => 첫화면 결정
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
   
   ### 2.앱 구성 요소 (App Components)
   > 앱에서 생성하는 각각의 앱 구성 요소에 대해 매니페스트 파일에서 해당하는 XML 요소를 선언해야 합니다.
   > 컴포넌트는 애플리케이션의 구성 요소입니다. 컴포넌트는 안드로이드 앱뿐만 아니라 여러 애플리케이션을 개발할때 사용하는 개념입니다.
   > ### 안드로이드 4대 컴포넌트 
   > 매니페스트 파일에서 XML 요소를 선언하지 않고 이 구성 요소를 하위 클래스로 지정하면 시스템에서 이를 시작할 수 없습니다.
   >
   > 1. <activity>: Activity
   > 2. <service>: Service
   > 3. <receiver>: Broadcast Receiver
   > 4. <provider>: Content Provider
   >
   > 이것들의 공통적인 특징들은
   > 각 컴포넌트들은 하나의 독립적인 형태로 존재하고, 고유의 기능을 수행, 인텐트를 통해 서로 상호작용합니다.
   > ### 1.액티비티(Activity)
   > 화면을 구성하는 컴포넌트 입니다. 앱의 화면을 안드로이드폰에 출력하려면 액티비티를 만들어야 하며, 앱이 실행되면 액티비티에서 출력한 내용이 안드로이드 폰에 나옵니다.
   > 안드로이드 앱은 하나 이상의 액티비티를 포함하고 있으며, 액티비티는 생명주기관련 메서드를 재정의하여 원하는 기능을 구현할수 있습니다. 또한 반드시 앱에는 하나 이상의 액티비티가 존재해야합니다.
   > ### 2.서비스(Service)
   > 백그라운드 작업을 하는 컴포넌트 입니다. 화면출력 기능이 없으므로 서비스가 실행 되더라도 화면에는 출력되지 않습니다. 서비스 컴포넌트는 화면과 상관없이 백그라운드에서 
   > 장시간 실행해야 할 업무를 담당합니다.
   > 네트워크와 연동이 가능하며 별도의 UI를 가지고 있지 않으며 백그라운드에서 힐행, 앱이 종료되어도 백그라운드에서 계속 동작합니다.
   > ### 3.브로드캐스트 리시버(Broadcast Receiver)
   > 시스템 이벤트가 발생 할 때 실행되게하는 컴포넌트입니다. 여기서 이벤트는 화면에서 발생하는 사용자 이벤트가 아니라 시스템에서 발생하는 특정 상황을 의미합니다.
   > 거의 대부분 UI를 가지고 않고, 특정한 상황을 제외하고는 브로드캐스트는 시스템에서 시작합니다.
   > ex) 부팅완료,배터리 방전같은 상황
   > ### 4. 콘텐츠 프로바이더(Content Provider)
   > 앱의 데이터를 공유하는 컴포넌트 입니다. 안드로이드폰에는 많은 앱이 설치되어있으며 앱 간에 데이터를 공유할수 있습니다. 하나의 앱이 자신의 데이터를 다른 앱에 공유하려면 콘텐츠 프로바이더를 만들어야하고
   > 다른 앱은 그 콘텐츠 프로바이더를 이용해 데이터에 접근합니다.
   > 외부 앱이 현재 실행중인 앱에 있는 DB에 접근하지 못하게 할수 있으며 원하는 데이터만 공유할수있게 할수있고, SQLite DB/ Web/파일 입력 등을 통해서 데이터를 관리합니다.
   > ex) 카톡앱에서 프로필 변경할때 갤러리 앱의 사진 데이터를 콘텐츠 프로바이더를 이용해 주고 받습니다.
   
   ## 인텐트 필터
   > activity,service,broadcast recevier는 인텐트로 활성화 되며 인텐트는 실행할 작업을 설명하는 Intent 객체로 정의되는 메시지입니다. 
   > 인텐트 유형
   > 1. 명시적 인텐트: 인텐트를 충족하는 애플리케이션이 무엇인지 지정 ex) 사용자 작업에 응답하여 새로운 액티비티를 시작하거나 백그라운드에서 파일을 다운로드하기 위해 서비스를 시작하는것
   > 2. 암시적 인텐트: 특정 구성요소의 이름을 대지 않지만, 수행할 일반적인 작업을 선언하여 다른 앱의 구성 요소가 이를 처리할수 있도록함 ex) 지도 위치 표시 요청
   
   
  
  ## 나머지 항목들
  
   > < action > 인텐트 필터에 작업을 추가합니다.
   
   > < activity > 애플리케이션의 시각적 사용자 인터페이스 요소를 구현하는 액티비티를 선언합니다. 

   > < activity-alias > activity의 별칭으로, targetActivity 속성에서 이름이 지정됩니다.
   
   > < application > 애플리케이션 선언입니다. 이 요소는 애플리케이션의 각 구성요소를 선언하고 모든 구성요소에 영향을 줄 수 있는 속성을 가진 하위 요소를 포함합니다.
   
   > < category>  인텐트 필터에 카테고리 이름을 추가합니다.
   
   > < compatible-screens > 애플리케이션이 호환되는 각 화면 구성을 지정합니다.
   
   > < data > 데이터 사양을 인텐트 필터에 추가합니다.
   
   > < grant-uri-permission > 상위 콘텐츠 제공업체에게 액세스 권한이 있는 앱 데이터의 하위 집합을 지정합니다.
   
   > < instrumentation >  애플리케이션과 시스템의 상호작용을 모니터링할 수 있는 Instrumentation 클래스를 선언합니다.
   
   > < intent-filter > 활동, 서비스, broadcast receiver가 응답할 수 있는 인텐트의 유형을 지정합니다. 
   
   > < meta-data > 상위 구성요소에 제공될 수 있는 추가 임의 데이터 항목의 이름-값 쌍입니다. 
   
   > < path-permission > 콘텐츠 제공자 내의 특정 데이터 하위 집합과 관련하여 경로와 필수 권한을 정의합니다. 
   
   > < permission > 이 애플리케이션이나 다른 애플리케이션의 특정 구성요소 또는 기능에 대한 액세스를 제한하는 데 사용될 수 있는 보안 권한을 선언합니다.
   
   > < permission-group >  관련 권한의 논리적인 그룹 이름을 선언합니다
   
   > < permission-tree > 권한 트리의 기본 이름을 선언합니다.
   
   > < provider > 콘텐츠 제공자 구성요소를 선언합니다. 
   
   > < supports-gl-texture >  앱에서 지원하는 단일 GL 텍스처 압축 형식을 선언합니다.
   
   > < supports-screens > 애플리케이션에서 지원하는 화면 크기를 지정하고 사용하는 화면이 애플리케이션에서 지원하는 화면보다 큰 경우 화면 호환성 모드를 사용 설정할 수 있게 합니다.
   
   > < uses-configuration > 애플리케이션에 필요한 하드웨어 및 소프트웨어 기능을 나타냅니다. 
   
   > < uses-feature > 애플리케이션이 사용하는 단일 하드웨어 또는 소프트웨어 기능을 선언합니다.
   
   > < uses-library > 애플리케이션이 연결되어야 하는 공유 라이브러리를 지정합니다.
   
   > < uses-permission > 앱이 올바르게 작동하기 위해 사용자가 반드시 부여해야 하는 시스템 권한입니다. 
   
   > < uses-permission-sdk-23 > 앱이 특정 권한을 원한다는 것을 지정합니다.(단, 오직 Android 6.0(API 레벨 23) 이상을 실행하는 기기에서 설치되는 경우에만 해당됩니다.)
   
   > < uses-sdk > 하나 이상의 Android 플랫폼 버전과의 애플리케이션 호환성을 API 레벨 정수로 표시할 수 있습니다.
 
---

# 2. Palette 항목
> ## Text
   TextView 화면에 텍스트를 표시하는 기능  
   Plain Text 표준 텍스트 키보드를 표시하는 textview  
   Password 표준 텍스트 키보드를 표시하고 개인 정보 보호를 위해 입력 한 텍스트를 숨김  
   Password(Numeric) 숫자 키보드를 표시하고 개인 정보 보호를 위해 입력 한 텍스트를 숨김  
   E-mail 스페이스 바 왼쪽에 "@" 문자를 추가하여 표준 텍스트 키보드를 표시  
      Phone 사용자가 전화번호 형식의 텍스트(xxx-xxxx)를 입력하기 쉽게 숫자 키보드가 올라오고 '-'가 위치  
      Postal Address 사용자가 우편번호 형식의 텍스트를 입력하기 쉽게 키보드 맨 윗줄에 길게 탭했을 때 숫자가 입력됨  
      Multiline Text 새 줄을 추가하기 위해 Enter 키를 추가하여 표준 텍스트 키보드를 표시  
      Time 사용자가 시간 형식의 텍스트(예) 12:20)를 입력하기 쉽게 ":" 문자를 추가하여 숫자 키보드를 표시  
      Date 사용자가 날짜 형식의 텍스트(예) 2020/09/23)를 입력하기 쉽게 "/"문자를 추가하여 숫자 키보드를 표시  
      Number 기본 숫자 키보드를 표시합니다.  '-', ',' '.' 등의 부호가 입력되지 않음  
      Number(Signed) 기본 숫자 키보드를 표시 , 시작시 + 또는-문자를 허용(양수,음수) 숫자를 입력하는 도중에는 '-'를 입력할 수 없고, 이 외에 ','와 '.'를 쓸 수 없음  
      Number(Decimal)   기본 숫자 키보드를 표시, 소수점('.')을 허용합니다. '-'와 ','는 사용할 수 없음  
      AutoCompleteTextView 사용자가 입력하는 동안 자동 완성 제안을 표시하는 편집 가능한 텍스트보기. 제안 목록이 드롭 다운 메뉴에 표시되어 사용자가 편집 상자의 내용을 바꿀 항목을 선택  
      MutilAutoCompleteTextView  확장 가능한 편집 가능한 텍스트보기로, AutoCompleteTextView사용자가 전체 내용 대신 입력하는 텍스트의 하위 문자열에 대한 완성 제안을 표시   
      CheckedTextView 체크박스를 제공하는 확장 TextViewMainActivity에서 setOnClickListner을 통해 체크 박스의 체크와 해제 속성을 부여 할 수 있음  
      TextlnputLayout   텍스트를 입력하는 곳이 Layout의 속성을 가짐  Layout의 속성을 설정하듯이 속성을 설정할 수 있음 
 
---
# 3. Layout
   ## 1. Linear Layout
> 기본적인 레이아웃으로 왼쪽 위부터 아래 또는 오른쪽으로 차례로 배치  
> 이용할때 항상 orientation 속성에서 "horizontal" 또는 "vertical"으로 레이아웃을 추가해 나갈지 결정해줘야한다.  
>  내부 값들을 정할 때 layout_gravity는 뷰를 정렬하는 데 사용되고 gravity는 뷰 안에 들어가 있는 내용물을 정렬할때 사용한다.  
>  weight는 내부 객체들의 크기를 비율로 정해줌  
>  weightSum 은 전체 비율을 정하는 속성, weight는 항상 남은 크기에서 비율로 크기를 나눠서 여백이 없지만 weightsum은 여백을 남길수 잇음
   ## 2. Relative Layout
> 레이아웃 내부에 포함된 위젯들을 상대적인 위치로 배치
   ![r1](https://user-images.githubusercontent.com/90558247/153354447-df479154-88a0-47cf-806c-622bea3b6c4a.jpg)
   ![r2](https://user-images.githubusercontent.com/90558247/153354502-7e348b59-c745-46ae-9c82-ef8bcf81089b.jpg)
   ## 3. Frame Layout
>  하나의 자식 view 위젯만 표시  
   여러 view 위젯을 자식으로 추가하면 겹쳐진 형태로 표시되며, 가장 최근에 추가된 view 위젯이 가장 위에 표시됌  
   이러한 특징을 이용해 Visibility 로 뷰의 가시성을 설정할 수 있음.  
   visible : 뷰의 영역 유지, 뷰를 보여줌 (일반적인상태)  
   invisible : 뷰의 영역을 유지하고, 뷰를 숨김(ex,이미지뷰의 영역은 남기고 이미지를 숨김)  
   gone: 뷰의 영역 자체를 숨겨 보이지않음  
   ![fream](https://user-images.githubusercontent.com/90558247/153550755-253f20a3-e579-4252-a388-ce4371a02101.jpg)

   ## 4. Table Layout
>  자식 view 위젯을 테이블(행과 열로구성)로 나누어 표시. 
   stretchColumns: 여유공간이 생기지 않음, 속성 안에는 크기를 늘리고싶은 뷰의 인덱스를 작성 ex) android:stretchColumns="0,2" ( o과 2의 뷰의 크기 늘림)  
   layout_span: 해당 column이 지정한 값 만큼의 공간 차지 ex) layout_span="3"이면 1만큼의 자리를 가진 뷰가 3만큼 자리를 가짐  
   layout_column: 인덱스 번호를 입력하면 해당 column이 지정된 인덱스 위치로 이동 ex) 두번째에 배치되어있는 인덱스가 1인 뷰를 column="3" 하면 두칸 옆으로 이동  
   ![table](https://user-images.githubusercontent.com/90558247/153552309-ce39a246-60c1-4320-a707-c8a79a3b427a.jpg)

   ## 5. Grid Layout
>  ridLayout은 2차원 격자무늬 형태의 레이아웃으로 행과 열의 집합형태로 구성된 레이아웃입니다. TableLayout의 단점을 보완한 레이아웃으로 LinearLayout 또는 FrameLayout과 같은 다른 레이아웃의 장점을 포함
   
# 4. Layout 활용하여 화면 구축하기 
   
   
   



