# HTTP/1.1

> 매번 TCP 연결을 하는 것이 아니라 한 번 TCP 초기화를 한 이후에 keep-alive라는 옵션으로 여러 개의 파일을 송수신

> HTTP/1.0에서도 keep-alive가 있었지만 표준화가 되어 있지 않았고 HTTP/1.1부터 표준화가 되어 기본 옵션으로 설정되었다.
> 한 번 TCP 3-웨이 핸드셰이크가 발생하면 그다음부터 발생하지 않는다.

![HTTP1.0과HTTP1.1의비교.png](./image/HTTP1.0과HTTP1.1의비교.png)

**단점**

- 문서 안에 포함된 다수의 리소스(이미지, css 파일, script 파일)를 처리하려면 요청할 리소스 개수에 비례해서 대기 시간이 길어짐.
- HOL Blocking (Head Of Line Blocking)
  - 네트워크에서 같은 큐에 있는 패킷이 그 첫 번째 패킷에 의해 지연될 때 발생하는 성능 저하 현상
    ![HOL_Blocking.png](./image/HOL_Blocking.png)
  - 그림처럼 image.jpg와 styles.css, data.xml을 다운로드받을 때 보통은 순차적으로 잘 받아지지만 image.jpg가 느리게 받아진다면 그 뒤에 있는 것들이 대기하게 되며 다운로드가 지연되는 상태가 됨
- 무거운 헤더 구조
  - HTTP/1.1의 헤더에는 쿠키 등 많은 메타데이터가 들어 있고 압축이 되지 않아 무거움
