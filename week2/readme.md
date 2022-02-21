# 2주차 과제일지

- [x]  **실습영상**
- [x]  **생명주기 특징과 어떻게 활용할지 조사**
- [x]  **각각의 생명주기를 활용하여 앱 구현**
- [x]  **챌린지 미션**

## 1. 생명주기 특징 조사

# **안드로이드 생명주기**

## **생명주기란?**

> 사용자가 앱을 탐색하고, 앱에서 나가고, 앱으로 다시 돌아가면, 앱의 Activity 인스턴스는 수명 주기 안에서 서로 다른 상태를 통해 전환됩니다.Activity 클래스는 활동이 상태 변화(시스템이 활동을 생성, 중단 또는 다시 시작하거나, 활동이 있는 프로세스를 종료하는 등)를 알아차릴 수 있는 여러 콜백을 제공합니다.생명주기 콜백을 잘 구현하면 다음고 같은 문제를 예방할수 있음.
> 
> 1. 사용자가 앱을 사용하는 도중에 전화가 걸려오거나 다른 앱으로 전환할 때 비정상 종료되는 문제
> 2. 사용자가 앱을 활발하게 사용하지 않는 경우 귀중한 시스템 리소스가 소비되는 문제
> 3. 사용자가 앱에서 나갔다가 나중에 돌아왔을 때 사용자의 진행 상태가 저장되지 않는 문제
> 4. 화면이 가로 방향과 세로 방향 간에 회전할 경우, 비정상 종료되거나 사용자의 진행 상태가 저장되지 않는 문제
>     
>     ![https://user-images.githubusercontent.com/90558247/153814849-90524ba7-6943-483e-a88a-209ad5071bed.png](https://user-images.githubusercontent.com/90558247/153814849-90524ba7-6943-483e-a88a-209ad5071bed.png)
>     

## **생명주기 메소드**

> onCreate()
> 
> 
> 프로그램 Activity가 생성할 때 실행되는 것으로, 필수적으로 필요한 콜백입니다. Activity가 생성되면 동작합니다. 안드로이드 전체 생명 주기에서 단 한 번만 실행이 됩니다
> 
> ### **OnStart()**
> 
> onCreate(), onRestart() 이후에 Activity가 시작되면 이 콜백을 호출합니다. 프로그램의 ForeGround와 상호작용을 할 수 있습니다. 사용자에게 보이기 직전에 실행되는 콜백입니다.
> 
> ### **OnResume()**
> 
> Activity가 재개된 상태에 들어가면 ForeGround에 표시가 되고 onResume() 콜백을 호출합니다. 어떤 이벤트가 발생하여 앱에서 포커스가 떠날 때까지 이 상태에 머무릅니다. 포커스가 떠나는 상태라면 예를 들어 전화가 오거나, 사용자가 다른 활동으로 이동하는 등 상태에서 Resume() 콜백을 호출해줍니다. 포커스가 떠난 후 다시 돌아오면 onResume() 콜백을 다시 호출합니다
> 
> ### **OnPause()**
> 
> Activity가 어떤 이벤트가 발생하여 앱에서 포커스가 떠날 때 콜백을 호출합니다 onResume()과 onPause()는 한 묶음
> 
> ### **OnStop()**
> 
> Activity가 더 이상 사용자에게 표시가 되지 않으면 중단상태로 들어갑니다. 그때 onStop() 콜백을 호출합니다 예를 들어서 새로 시작된 앱이 화면 전체를 차지하는 경우에 onStop() 콜백을 호출합니다. onStop()은 주로 리소스를 해제하거나 조정해야 할 때 주로 사용됩니다 onStop() 상태로 들어갔다가 활동이 다시 시작되면 onRestart() 콜백을 호출해줍니다
> 
> ### **OnDestroy()**
> 
> Activity가 소멸할 때 불러오는 콜백입니다. onDestory()는 생명주기가 종료됩니다.
> 

출처: [https://crazykim2.tistory.com/634](https://crazykim2.tistory.com/634) [잡다한 프로그래밍]

> 액티비티 생성
> 
> 
> ![https://user-images.githubusercontent.com/90558247/153816081-7c3d3b10-3922-4eca-8075-ec6ae8356bd1.png](https://user-images.githubusercontent.com/90558247/153816081-7c3d3b10-3922-4eca-8075-ec6ae8356bd1.png)
> 
> 1. onCreate() → 생성된 화면 구성요소를 메모리에 로드
> 2. onStart(), onResume() → 화면의 구성요소를 나타내고 사용자와 상호작용 시작(Resumed: 실행 중)
> 
> ## **액티비티 화면에서 제거**
> 
> 1. onPause(), onStop() → 뒤로 가기, finish()를 실행할 때 동시에 실행
> 2. onDestory() → 최종적으로 액티비티가 메모리에서 제거
> 
> ## **액티비티를 종료하지 않고 다른 액티비티 실행**
> 
> 1. onPause(), onStop() → 현재 액티비티를 종료하지 않고 새로운 액티비티가 만들어질 때(Stopped)
> 2. onStart(), onResume() → 두 메서드가 연속적으로 실행되고 Resumed 상태로 변경
> 
> ## **액티비티를 종료하지 않거나, 모두 가려지지 않을 때 다른 액티비티 실행**
> 
> 1. onPause() → 완전히 사라진 것은 아니므로 Paused 상태로 변경
> 2. onResume() → 정지가 아니니 onStart를 거치지 않고 바로 onResume로 Resumed

출처: [https://bbaktaeho-95.tistory.com/62](https://bbaktaeho-95.tistory.com/62) [Bbaktaeho]

# 2. Fragment 생명주기

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4af5fa82-8153-476e-81ec-557777f4f1d6/Untitled.png)

## Fragment 에서 구현해야하는 최소한의 생명주기

- **onCreate()**

프래그먼트를 생성할 때 호출합니다. 프래그먼트가 일시정지 혹은 중단 후 재개되었을 때 유지하고 있어야 하는 것을 여기서 초기화 해야합니다.

- **onCreateView()**

프래그먼트가 자신의 인터페이스를 처음 그리기 위해 호출합니다. View를 반환해야 합니다. 이 메서드는 프래그먼트의 레이아웃 루트이기 때문에 UI를 제공하지 않는 경우에는 null을 반환하면 됩니다.

- **onPause()**

사용자가 프래그먼트를 떠나면 첫번 째로 이 메서드를 호출합니다. 사용자가 돌아오지 않을 수도 있으므로 여기에 현재 사용자 세션을 넘어 지속되어야 하는 변경사항을 저장합니다.

## **액티비티와 프래그먼트의 수명 주기에서 가장 중요한 차이점은 백스택에 저장되는 방법**

액티비티는 정지되면 시스템에서 관리하는 액티비티의 백 스택에 들어갑니다. 하지만 프래그먼트는 이를 제거하는 트랜잭션에서 addToBackStack()
을 호출하여 인스턴스를 저장하라고 명시적으로 요청할 경우에만 액티비티에서 관리하는 백 스택으로 들어갑니다.

출처 [https://ddangeun.tistory.com/50](https://ddangeun.tistory.com/50)

## 3. 구현

# 첫번째 화면

## 1. 프로필 사진 누르면 비밀번호 입력하는 액티비티로 이동

![화면1.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/daba19cb-eb9b-4d41-9ebd-ee8ef0c2b25b/화면1.jpg)

## 2. 암시적 인텐트 사용

 상단의 Facebook 이미지 버튼을 누를시 Facebook 홈페이지로 이동

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/824122a7-cb39-4894-a15a-41b7702ff26e/Untitled.png)

```kotlin
facebook.setOnClickListener()
        {
            var uri = Uri.parse("http://facebook.com")
            var intent = Intent(Intent.ACTION_VIEW,uri)
            startActivity(intent)
        }
```

# 두번째 화면

![화면3.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/24e97277-3d86-49e0-91b1-01d854853ba8/화면3.jpg)

- **onCreate()**    Sharedreferenes를 통해 비밀번호텍스트에 저장된 값이 있다면 불러오고 그렇지 않으면 저장합니다.
- **onDestroy()**  앱이 종료되면 저장된 값을 삭제시킵니다.

# 세번째 화면

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/144bb694-336f-4688-8f7b-e0e80ac3bebf/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7151e3f0-0a02-496c-9d21-fab956a11edd/Untitled.png)

- **onRestart()**  홈으로 나갔다가 다시돌아오거나 다른 액티비티로 갔다가 뒤로 가기 버튼으로 돌아오게 되는 경우인 onRestart()에서 광고 배너가 변경되게 했습니다.

# 네번째 화면

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8e4ef69a-9c09-4dab-8c4a-1fd6c02c838f/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c8b47058-5e62-46c2-a165-2775bf038686/Untitled.png)

- **onPause()**   대화창에서 액티비티가 포커스를 잃게 되면 edittext에 쓰던 텍스트를 onPuase() 단계에서 지워버립니다.

---

# **어려웠던점**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/da1e293b-530d-4206-9c04-9bedf99d7fd4/Untitled.png)

- bottom navigation 를 쓰는 부분에서 fragment1 에서 광고 배너가 바뀌는 부분(?) 을 표현할때 생명주기의 어떤부분에 구현을할지 어려움을 느껴 bottom navagation을 사용하지못함
- Fragment → Activity , Activity → Fragment 의 화면 전환 방법?
