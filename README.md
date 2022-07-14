# Tour Korea
### 항해99 - 1주차 프로젝트 
#### 2022.7.11 ~ 2022.7.14   
   
   
---   

## 프로젝트 소개
늘 해외여행만 다니는 우리, 국내에도 예쁜 관광지가 많다.
지금까지 다녔던 국내 예쁜 여행지들의 사진과 경험했던 것을 글로 공유하여 다른 유저들에게 자랑을 해보는 웹 플랫폼 입니다. 다른 유저의 사진과 글에 댓글을 달아 감정을 공유해보면 좋습니다.

   ---
## 프로젝트 시연영상
<strong>유튜브 링크 : </strong> https://youtu.be/FMlhL29LUaI

https://user-images.githubusercontent.com/82853790/178917343-2d611f0e-589d-4307-b493-9f6dc133164a.mp4



   ---
### API Table
![image](https://user-images.githubusercontent.com/82853790/178924622-fc722a85-0940-4c85-8680-bfab42e30597.png)




   ---
### Trouble Shooting
1. 삭제 기능 데이터 중복 제거 문제
-> 사전 프로젝트 강의의 bucketList처럼 데이터 개수에 1을 추가하여 index를 생성했으나 삭제 되면 index가 중복되는 문제가 발생됨.
→ 해결 : 데이터 추가할 때 난수를 생성하여 DB에 index로 저장(생성된 난수가 DB에 있을 시 새로운 난수 생성)

2. EC2 서버에서 app.py 실행 시, 로그인 기능 문제 발생
-> 기존 Local서버에서 로그인 기능이 동작되었으나, EC2서버에서 실행 시 token을 클라이언트 측으로 넘겨주지 못하는 문제가 발생됨.
→ 해결 : token 생성 코드에 .decode(‘utf-8’)을 붙여 스트링 값으로 바꿔서 해결(Local서버에서 실행 시, decode() 함수 제거해야 동작됨)

3. Jinja2에서 현재 URL 가져오기
-> URL 파라미터를 변수로 사용하여 DB를 분류해야 함.
→ 해결 : {%request.full_path.split("?")[1].split("=")[1] | int %}  사용하여 url를 추출 후 split함수 사용함. 
               DB의 int형과 비교를 위해 String 타입을 int 타입으로 형변환. ( | int )

4. 로그인 실패 시 멈추는 문제
-> 틀린 ID와 PW를 넣을 시,  500 (INTERNAL SERVER ERROR) 가 발생함.
     DB에 데이터가 없을 시 name 변수에 오류가 발생함.
               result = db.users.find_one({'id': username_receive, 'pw': password_hash})
               name = result['name']
→ 해결 :결과가 있을 시에만 name변수에 할당하게 설정( if result is not None:  코드 추가)

5 화면전환 시 그에 맞는 데이터 가져오기 
-> 메인 페이지에 사진을 눌렀을 때, commnetpage에 클릭한사진에 맞는 사진과 글 가져오는것과 댓글올렸을 때 유저이름과 댓글 올라가는 것에 대한 방법
======>해결 삭제하기 기능 때 추가했던 index를 사용해서 이미지에맞는 index와 파라미터에 index값설정을해 일치할 때 나오도록 구현함


  -----
## Tech Stack
 - Javascript 
 - Jquery
 - HTML
 - CSS
 - Github
 - Linux
 - AWS EC2
 - Python
 - Flask
 - Jinja2
 - MongoDB



