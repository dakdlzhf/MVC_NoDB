# :star:MVC 패턴 DB 연동없이 흐름파악해보기

### **index.jsp 에서 더하기,빼기 입력을 받고, Controller를이용하여 요청을 받고 분석하여 Model 을통해 처리한후 View  출력**

* Model , View , Controller 패턴을 이용한다
* db 접근이 없는 상황
* FrontController 패턴을이용하여  FrontController 는 모든 요청을 받을수있게 매핑해놓는다
* BackController  은 FrontController 의 요청분석 이끝나면 요청에 알맞는 Handler 를 실행한다.
* BackController 에서 Model 영역의 Service 처리를 한다.
