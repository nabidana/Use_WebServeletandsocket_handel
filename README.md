# Use_WebServeletandsocket_handel

"loginfail_file_jsp", "logining_file_jsp", "loginok_file_jsp", "logout_file_jsp"
위 파일들은 기본적인 내부 DB에 접속하여 HelloWorld수준의 로그인 방식을 간략하게 구현한 파일들.

"main_login.jsp"
>로그인을 하기위해 사용되는 로그인 창.

"main_java_file.java"
>멀티 로그인 연동을 위해 사용했던 파일.

>들어오는 패킷의 파라미터에서 userid와 userpassword를 추출하여 내부DB와 비교한 뒤, 해당 user가 DB에도 있으면,

>Response패킷에 OKAY를 담아서 보내고, 아닐경우, FAIL을 보낸다.

>메인서버에서는 Response 패킷의 OKAY부분을 이용하여 멀티로그인 성공 여부를 메인서버에서 알리게 됨.
