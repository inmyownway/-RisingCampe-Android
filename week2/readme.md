# 안드로이드 생명주기

## 생명주기란?
> 사용자가 앱을 탐색하고, 앱에서 나가고, 앱으로 다시 돌아가면, 앱의 Activity 인스턴스는 수명 주기 안에서 서로 다른 상태를 통해 전환됩니다.  
  Activity 클래스는 활동이 상태 변화(시스템이 활동을 생성, 중단 또는 다시 시작하거나, 활동이 있는 프로세스를 종료하는 등)를 알아차릴 수 있는 여러 콜백을 제공합니다.   
  생명주기 콜백을 잘 구현하면 다음고 같은 문제를 예방할수 있음. 
>  1. 사용자가 앱을 사용하는 도중에 전화가 걸려오거나 다른 앱으로 전환할 때 비정상 종료되는 문제  
>  2. 사용자가 앱을 활발하게 사용하지 않는 경우 귀중한 시스템 리소스가 소비되는 문제  
>  3. 사용자가 앱에서 나갔다가 나중에 돌아왔을 때 사용자의 진행 상태가 저장되지 않는 문제  
>  4. 화면이 가로 방향과 세로 방향 간에 회전할 경우, 비정상 종료되거나 사용자의 진행 상태가 저장되지 않는 문제
>  ![image](https://user-images.githubusercontent.com/90558247/153814849-90524ba7-6943-483e-a88a-209ad5071bed.png)

## 생명주기 메소드
> ### onCreate()
>  프로그램 Activity가 생성할 때 실행되는 것으로, 필수적으로 필요한 콜백입니다. Activity가 생성되면 동작합니다. 안드로이드 전체 생명 주기에서 단 한 번만 실행이 됩니다
> ### OnStart()
> onCreate(), onRestart() 이후에 Activity가 시작되면 이 콜백을 호출합니다. 프로그램의 ForeGround와 상호작용을 할 수 있습니다. 사용자에게 보이기 직전에 실행되는 콜백입니다.
> ### OnResume()
>  Activity가 재개된 상태에 들어가면 ForeGround에 표시가 되고 onResume() 콜백을 호출합니다. 어떤 이벤트가 발생하여 앱에서 포커스가 떠날 때까지 이 상태에 머무릅니다.
>  포커스가 떠나는 상태라면 예를 들어 전화가 오거나, 사용자가 다른 활동으로 이동하는 등 상태에서 Resume() 콜백을 호출해줍니다. 포커스가 떠난 후 다시 돌아오면 onResume() 콜백을 다시 호출합니다
> ### OnPause()
>  Activity가 어떤 이벤트가 발생하여 앱에서 포커스가 떠날 때 콜백을 호출합니다
>  onResume()과 onPause()는 한 묶음
>  ### OnStop()
>  Activity가 더 이상 사용자에게 표시가 되지 않으면 중단상태로 들어갑니다. 그때 onStop() 콜백을 호출합니다
>  예를 들어서 새로 시작된 앱이 화면 전체를 차지하는 경우에 onStop() 콜백을 호출합니다. onStop()은 주로 리소스를 해제하거나 조정해야 할 때 주로 사용됩니다
>  onStop() 상태로 들어갔다가 활동이 다시 시작되면 onRestart() 콜백을 호출해줍니다
>  ### OnDestroy()
>  Activity가 소멸할 때 불러오는 콜백입니다. onDestory()는 생명주기가 종료됩니다.






출처: https://crazykim2.tistory.com/634 [잡다한 프로그래밍]

> ## 액티비티 생성
> ![image](https://user-images.githubusercontent.com/90558247/153816081-7c3d3b10-3922-4eca-8075-ec6ae8356bd1.png)
> 1. onCreate() → 생성된 화면 구성요소를 메모리에 로드
> 2. onStart(), onResume() → 화면의 구성요소를 나타내고 사용자와 상호작용 시작(Resumed: 실행 중)
> ## 액티비티 화면에서 제거
> ![image](https://user-images.githubusercontent.com/90558247/153816206-c0b730aa-498b-45a7-89d4-e6ecada6dd3d.png)
> 1. onPause(), onStop() → 뒤로 가기, finish()를 실행할 때 동시에 실행
> 2. onDestory() → 최종적으로 액티비티가 메모리에서 제거
> ## 액티비티를 종료하지 않ㄱ 다른 액티비티 실행
> 1. onPause(), onStop() → 현재 액티비티를 종료하지 않고 새로운 액티비티가 만들어질 때(Stopped)
> 2. onStart(), onResume() → 두 메서드가 연속적으로 실행되고 Resumed 상태로 변경
> ## 액티비티를 종료하지 않거나, 모두 가려지지 않을 때 다른 액티비티 실행
> 1. onPause() → 완전히 사라진 것은 아니므로 Paused 상태로 변경
> 2. onResume() → 정지가 아니니 onStart를 거치지 않고 바로 onResume로 Resumed

출처: https://bbaktaeho-95.tistory.com/62 [Bbaktaeho]






