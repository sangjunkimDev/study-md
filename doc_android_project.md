## 기본 개념
- ### proguard
    - 빌드시 코드 난독화, 디컴파일시에도 안정성 확보
    - 기본적으로 Android Stdio에서 제공한다.

- ### lint
    - 컴파일시 에러 또는 필요없는 부분을 표시해줌
    - lint.xml 은 설정파일

- ### keystore
    - 앱을 안드로이드마켓에 올리는 경우 꼭 필요한 개발자 정보를 담은 파일
    - keystore는 cmd에서 명령어를 통해 만들고 Android Studio에서 해당 키스토어로 설정한다
    - 비밀번호를 까먹지 말아야한다. 만약 까먹을 경우 다시 만들어야 하는 수가 있다.
    - 유효기간은 25년 이상을 권장한다

- ### 비동기처리(CallBack)
    - 해당 쓰레드에서 실행되며, 절대로 쓰레드를 하나 더 만드는 것이 아니다.
    - 비동기 메서드는 스택에 쌓이자마자 백그라운드에 이동시킨다.  
      해당 메서드가 실행되고 나면 다시 백그라운드에서 가져온다.  
      그리고 다시 스택에 쌓고 처리한다.

- ### 쓰레드
    - 프로세스가 회사라면, 쓰레드는 회사원이다.
    - 안드로이드에서 쓰레드는 기본 메인(UI)쓰레드가 있다.
    - 쓰레드를 써야하는 상황은 화면처리와 동시에 작업이 되어야 한다거나  
      네트워크 통신을 하는 경우이다.
    - 서비스에서 네트워크 처리를 하는 경우는 거의 없다.
    - 안드로이드에서는 Thread를 직접생성하는 것보다 AsyncTask 사용을 권장하고 있다.
    - 안드로이드에서는 UI쓰레드에는 기본적으로 Handler가 있다.(추가할 필요가 없다)
    - UI관련 작업은 Main쓰레드에서만 진행한다. 다만 화면이동(액티비티 전환)은 다른 쓰레드에서도 가능하다.
    - 라이브러리로는 `Retrofit2` 이 있다.

- ### 네트워크 요청 처리
    - 앞서 말한것처럼 비동기처리 만 사용하는 경우 메인쓰레드에서 실행하는 것이기 때문에 런타임에러가 발생한다.
    - 그렇기 떄문에 쓰레드를 추가적으로 사용해야한다.
    - 하지만 네트워크 처리는 대부분 비동기처리로 이루어지게 된다.(서버와의 통신시간이 필요하기 때문에)
    - 그래서 쓰레드와 비동기처리를 같이 써야한다.
    - 위와 같은 처리를 쉽게 도와주는 라이브러리로는 `Retrofit2` 이 있다.

- ### Service
    - 앱이 백그라운드에서 무언가를 계속 감지하거나 수행해야 하는 업무가 있는 경우에 쓰인다.
    - IntentService는 비동기로 처리되는 서비스이며, 여러번 실행되었을 경우에는 Queue로 처리된다.

- ### StrictMode
    - 사고로 일어날 수 있는 일(잠재적 문제 요소)을 감지하고 문제를 알려주는 개발자 도구
    - 메인스레드에서 디스크 또는 네트워크 작업을 잡는데 사용된다.
    - 즉, ANR(Android not response) 발생을 방지하게 도와준다.(단, 내가 수정을 했을 경우만!)
    - Lint는 컴파일 단계 검사, StrictMode는 런타임 단계 검사, 둘 다 잠재적 요소 파악

- ### GCM (Google Cloud Message)
    - 개발자에게 서버에서 안드로이드 디바이스의 app으로 데이터를 전송하는 것을 도와주는 무료서비스이다.
    - 서버에서 새로운 데이터가 있을 경우 GCM서비스를 통하여 Message를 특정 device의 특정 app으로
    전송해준다.
    - Message는 최대 4kb의 경량 메세지이다.
    - GCM서비스는 Message를 큐잉하며 이를 단말에 전달해주는 처리를 담당한다.
    - GCM connection Servers는 http / xmpp 지원

- ### BroadcastReceiver

---
### 도움받은 링크 목록
- proguard
    - <http://bitly.kr/W345>

- lint
    - <http://bitly.kr/b13i>

- keystore
    - <http://dwfox.tistory.com/40>

- 비동기처리(CallBack)
    - <http://new93helloworld.tistory.com/137>
    - <http://bitly.kr/mwuS>
    - <http://mailmail.tistory.com/12>

- 쓰레드
    - <http://itmining.tistory.com/5>

- 네트워크 요청 처리 및 Retrofit2
    - <http://bitly.kr/csRJ>
    - <http://bitly.kr/2jg5>
    - <http://bitly.kr/mDJO>

- Service
    - <http://fullstatck.tistory.com/23>
    - <http://bitly.kr/K2ct>
    - <http://jo.centis1504.net/?p=968>

- StrictMode
    - <https://developer.android.com/reference/android/os/StrictMode>

- GCM
    - <http://humble.tistory.com/30>
    - <https://aroundck.tistory.com/789>
