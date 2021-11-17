# Hi Class,   또 하나의 선생님  
*HiClass(하이클래스) :: 또 하나의 선생님*

언택트 교육의 집중도 및 참여도 저하 문제를 해결하고 유학생&다문화 가정의 수업 이해를 돕는 서비스입니다. 수업 시 학생의 집중도와 참여도 향상을 위한 여러 서비스와 번역, 자막 서비스를 제공하는 **화상 교육 플랫폼**입니다.  
![sysnop](https://user-images.githubusercontent.com/48875061/142240838-8596439e-b334-47e6-97b7-5c26481a42ac.png)  

## 📋 Core Service Logic  

![ourservice](https://user-images.githubusercontent.com/48875061/142241756-15c5fecd-e496-4b1b-bca1-3b34f08052d9.png)
- 실시간 다중 화상 공유 수업
- 선생님이 직접할 필요없이 자동화된 얼굴인식을 통한 출석체크
- 수업 방해 요인 SNS APP 차단
- 학생의 수업 집중도 & 참여도 체크를 위한 자리이탈 감지
- 실시간 수업 번역 및 자막
- 필기 노트 
- 수업 이해도 확인을 위한 마무리 Quiz & 복습 Quiz 
- 수업 태도 확인을 위한 집중도 및 참여도 그래프
- 실시간 채팅 
- 수업 별 공지사항
## ⌨ Service Flow  
![serviceflow](https://user-images.githubusercontent.com/48875061/142242110-7443ec09-e1db-4751-a4e9-ac9becfa606d.png)

## 💡 Service UI(example)  
홈페이지 화면            |  APP 홈 화면
:-------------------------:|:-------------------------:
![pencil](https://user-images.githubusercontent.com/48875061/142193568-bdda8084-8c90-4945-b9c5-a2aacc0fa179.PNG)  |  ![app](https://user-images.githubusercontent.com/48875061/142244903-5640b9de-6985-4b25-979d-e2b7d282eeb4.png)  

출석체크          |  집중도 통계자료
:-------------------------:|:-------------------------:
 ![culsuk](https://user-images.githubusercontent.com/48875061/142245689-ec5b72e0-017e-4a93-9b41-33caff5edd49.png) |  ![focus](https://user-images.githubusercontent.com/48875061/142245861-62466d72-7087-4c1d-84aa-ba8b2c28cb88.png)


공지사항           |  APP 자리이탈 감지
:-------------------------:|:-------------------------:
 ![gonggee](https://user-images.githubusercontent.com/48875061/142245073-9387dd34-3c1f-46f8-be45-cbcb513e266a.png)| ![seatleave](https://user-images.githubusercontent.com/48875061/142245335-5bc8d0da-c81b-4a64-aa71-d196331c2e5c.png)  

## 💻 Development Stack  

![develop](https://user-images.githubusercontent.com/48875061/142246292-9758d9a1-d975-4efc-9c10-b47dcce5bb5f.png)

## 🔧 Service Architecture  
## 📽️ Video Streaming
![undefined (3)](https://user-images.githubusercontent.com/48875061/142192307-818cfbed-69ea-4977-b628-ab9b01b5f8da.jpg)  
- Peer Connection  
`RTCPeerConnection` 인터페이스는 로컬 컴퓨터와 원격 피어 간의 WebRTC 연결을 담당하며 원격 피어에 연결하기 위한 메서드들을 제공하고, 연결을 유지하고 연결 상태를 모니터링하며 더 이상 연결이 필요하지 않을 경우 연결을 종료합니다.  
- ScreenShare  
`navigator.mediaDevices.getDisplayMedia()`를 통해 화면 콘텐츠를 가져오고
임시 피어를 생성하여 원격 피어 간 연결 유지합니다.  
## 📽️ VideoStreaming Features  
필기모드            |  PDF 변환
:-------------------------:|:-------------------------:
![pencil](https://user-images.githubusercontent.com/48875061/142193568-bdda8084-8c90-4945-b9c5-a2aacc0fa179.PNG)  |  ![image](https://user-images.githubusercontent.com/48875061/142193909-fe82fcc5-530b-4b47-a4e0-e0ab4b778da6.png)  
수업 중 필기를 할 경우를 대비해 헤더와 본문을 구분 짓고 다양한 기능을 제공하는 Markdown 언어를 이용하여 작성할 수 있습니다. PDF 변환을 통해 자신의 필기를 저장하는 기능을 제공합니다. javascripts의 eidtor를 담당하는 구성 요소 `codemirror`를 통해서 마크 다운형식으로 필기형식을 가능하게 구현했습니다.|nodejs 모듈인 `html-to-pdfmake`을 이용하여 해당 필기 내용을 pdf 형식을 전환하여 저장하는 기능을 구현했습니다.


실시간 음성인식            |  번역
:-------------------------:|:-------------------------:
![unnamed (1)](https://user-images.githubusercontent.com/48875061/142206008-0f420da5-9ea7-4544-a58f-85920ac1c2ed.png)  |  ![unnamed (2)](https://user-images.githubusercontent.com/48875061/142206015-220090c1-e963-4eda-b95e-0511198d713b.png)  
JavaScript 오픈소스 ( Web Speech API )를 사용하여 React의 실시간 시그널링 서버와 통신하는 Section.js에서 각 사용자의 오디오를 인식하여 적용시켜줍니다.|한국어 처리에 특화되어 있는 NaverCloudPlatform API 인 Papago Translation을 사용하여 STT로 만든 자막을 번역합니다. 이후 실시간 수업 번역 기능을 통해 다문화 가정 학생들의 비대면 수업 이해도를 높여줍니다.

### `Redux`  
![Chatting V2](https://user-images.githubusercontent.com/48875061/142204562-7343036e-acde-47b5-b513-e68503263663.jpg)

기존 연결된 IO를 통해 채팅 기능을 제공합니다. 또한 Redux를 통해 메시지 상태 관리를 분리하여 저장, 유지합니다.  
서버로부터 메세지를 전달받게 되면, Dispatch를 통해 스토어에 저장됩니다.  
UI Component에서 state가 필요하다 판단되면, 스토어로부터 저장된 state값을 불러옵니다.  

### 🐹API

---

1. WebRTC서버:: 실시간 영상 전송 서버 (socket)
2. WebRTC — Node Adapting Server

    기본 url :: [https://pedantic-einstein-75bdbe.netlify.app/](https://pedantic-einstein-75bdbe.netlify.app/)

    `IO` / 방 입장 시 socket connection 설정 위한 offer 마다의 토큰 제공

    `IO` / 방 퇴장 시 socket connection 해제

    `IO` / Join room id 중복검사 , 방(UserData) 입장

    `IO`/ offer 요청한 연결, 나를 제외한 전체 사용자에게 연결 요청

    `IO` / getoffer 요청 받은 연결, 나에게 들어온 연결 요청

    `IO` /message 실시간 채팅을 위한 연결

3. ManageServer

    기본 url :: [https://118.67.131.138:30000](https://118.67.131.138:30010/)

    `POST` /  → 사용자 아이디 중복 체크 및 비밀번호 재입력 확인 요청

    `POST` / login → 사용자 아이디 및 비밀번호 요청

    `GET` / logout → 로그아웃

    `POST` / makeroom → STUDY/EXAM 모드에 따라 방생성

    `POST` / makeroom/success → 방 생성 성공 후 방 정보 나열

    `POST` / enteroom/exam1 → EXAM 모드 앱 차단 여부 요청

    `POST` / enteroom/exam2 → EXAM 모드 얼굴 인식 확인 요청

    `POST` / enteroom/exam3 → EXAM 모드 WebRTC 입장 가능 여부 요청 

    `POST` / enteroom/study1 → STUDY 모드 앱 차단 여부 요청

    `POST` / enteroom/study2 → STUDY 모드 WebRTC 입장 가능 여부 요청

    `GET` / roomout/<int:time>/<str:mode> → mode가 STUDY 일때 해당 사용자의 Analytics에 time이 저장됨

    `POST` / roomout/<int:time>/<str:mode> → App 접근 차단을 해제 하였는지 요청 & mode가 STUDY 일때 저장돤 time, app, person 변수를 바탕으로 level, rate를 측정하고 Analytics 모델에 저장 

    `GET` / roomout/study → session에서 사용자 정보를 가져와 Analytics 모델의 가장 마지막 row를 DB에서 가져와서 집중도 그래프를 그림 

    `POST` / roomout/exam → 시험이 성공적으로 종료 됐는지 요청

    `GET` / list/room → Room DB에서 사용자 이름으로 만들어진 Room을           QuerySet으로 반환후 list 나타냄

    `GET` / list/analytics → Analytics DB에서 사용자 이름으로 만들어진 Analytics를 QuerySet으로 반환후 list 나타냄

    `POST`/ list/analytics/<int:pk> → Analytics List에서 선택한 QuerySet 객체의 

    Primary Key 값과 같은 row를 DB에서 가져와 집중도 그래프를 그려줌 
---

### 🙋‍♂️Role
 @김준영 
 - *VideoStreaming Layout 구축*
 - *WebSocket token을 활용한 peer connection*
 - *화면 공유 기능 구축*
 - *Chat 기능 구축*
 - *필기 기능 구축*
 - *백엔드 실시간 통신 구축*
 - *Redux를 활용한 상태 관리*

 @김혜원 
 - *실시간 음성인식 구축*
 - *번역 기능 구축*

### License
```
MIT License

Copyright (해몽유식) [2021-11-19] [JunYoung Kim,HyeWon Kim,HanSik Hwang, YouLim Kim]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
