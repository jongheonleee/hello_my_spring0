# Hello My First Spring 🙋🏻‍♂️

## 📌 02. Spring MVC

#### 🧑🏻‍🏫 주요 내용 작성 

<img src="/images/아직.jpeg" width="800" height="500"/>

<br>

#### 👉 원격 프로그램의 실행

```java

@Controller // (1) 프로그램 등록 
public class HelloController {
    
    @RequestMapping("/hello") // (2) 요청 url 매핑
    public String hello(Model model) {
        model.addAttribute("greeting", "안녕하세요");
        return "hello";
    }
}
```


> - <img src="/images/아직.jpeg" width="400" height="400"/>
> - 원격으로 프로그램을 실행하려면 다음과 같이 2가지 작업을 해야함
>   - (1) 프로그램 등록
>   - (2) 요청 url 매핑 
> - 이 과정에서 알수 있는 것은 Tomcat이 내부에서 빈을 생성하고 등록함(스프링 컨테이너)
> - Reflect API를 활용해서 빈을 생성함
>   - Reflect API는 자바에서 지원하는 클래스 정보를 활용하는 기능을 의미함
>   - 모든 객체는 설계도 객체가 있음(Class가 존재함)
>   - 설계도 객체에는 클래스 관련 메타 정보가 저장되어 있음

<br>

#### 👉 HttpServletRequest와 HttpServletResponse

> - <img src="/images/아직.jpeg" width="400" height="400"/>
> - HttpServletRequest란? 요청 정보를 저장하고 있는 객체를 의미함
>   - url 자체는 문자열. 해당 요청 문자열을 저장하고 활용할 수 있게 해주는 객체
>   - 한마디로 url 요청 문자열을 저장하고 있는 객체를 의미함
>   
> - HttpServletResponse란? 응답 정보를 저장하고 있는 객체를 의미함
>   - 브라우저에 정보를 보여줄 때 활용함
>   - 해당 객체를 이용해서 자바코드로 HTML ... 을 만들어서 브라우저에서 보여줄 수 있음

<br>

#### 👉 서버가 제공하는 리소스

> - 리소스는 크게 2가지로 나뉨
>   - (1) 동적 리소스 : 계속해서 변화는 리소스
>     - 스트리밍, 프로그램, ...
>   
>  - (2) 정적 리소스 : 변하지 않고 고정되어 있는 리소스
>    - 이미지, 파일, HTML, CSS, JS, ...

<br>

#### 👉 클라이언트와 서버

> - <img src="/images/클라이언트와서버.jpeg" width="400" height="400"/>
> - 클라이언트란? 서버로 요청을 보내서 서비스를 사용하는 쪽. 서버란? 서비스를 제공하는 쪽
> - 서버는 여러 종류로 구성됨
>   - Email Server
>   - Web Server
>   - File Server
> 
> - Web Server란? 브라우저를 통해 사용할 수 있는 모든 종류의 서비스를 제공하는 서버
> - 하나의 서버에 여러 종류의 서버가 같이 있는 경우, 포트 번호로 구분하여 통신함
> - <img src="/images/서버여러대포트번호.jpeg" width="400" height="400"/>
> - binding이란? 포트번호와 서버가 연결되는 것을 말함. listening은 서버는 binding된 포트번호로부터 클라이언트 요청을 기다림

<br>

#### 👉 WAS(Tomcat)

> - <img src="/images/WAS구조.jpeg" width="400" height="400"/>
> - WAS란? 
>   - Web Application Server의 약자로, 웹 어플리케이션을 서비스하는 서버를 의미함
>   - 클라이언트에게 웹과 관련된 프로그램을 제공하는 서버
> - 서블릿이란?
>   - 서블릿은 자바로 만들어진 웹 프로그램을 의미함. 즉, 작은 서버 프로그램을 의미함

<br>

#### 👉 Tomcat 서버 내부 구조

> - <img src="/images/Tomcat내부구조.jpeg" width="400" height="400"/>
> - 서블릿이란? 작은 서버 프로그램을 의미함. 예를들어, 컨트롤러, ... 이 있음
> - 요청처리 전과정은 밑에와 같음
>   - Thread -> Connector -> Engine -> filter -> DispatcherServlet -> Controller -> 매핑된 메서드 호출 


<br>

#### 👉 Tomcat의 설정 파일

> - Tomcat의 설정 파일은 크게 2가지로 나눌 수 있음
>   - (1) server.xml : Tomcat 서버 설정 파일 
>     - Tomcat 설치경로/conf/server.xml
>   
>   - (2) web.xml : 웹 어플리케이션 설정 파일
>     - (2-1) web app의 공통 부분 설정
>       - Tomcat 설치경로/conf/web.xml
>     
>     - (2-2) web app의 개별 부분 설정
>       - web app/WEB-INF/web.xml

<br>

#### 👉 HTTP 요청과 응답 

<br>

#### 👉 텍스트와 바이너리, MIME, Base64

<br>

#### 👉 관심사의 분리와 MVC 패턴

<br>

#### 👉 서블릿과 JSP

<br>

#### 👉 @RequestParam과 @ModelAttribute

<br>

#### 👉 @RequestMapping

<br>

#### 👉 회원가입 화면 작성하기 

<br>

#### 👉 @GetMapping과 @PostMapping

<br>

#### 👉 redirect와 forward

<br>

#### 👉 쿠키란?

<br>

#### 👉 세션이란?

<br>

#### 👉 예외처리

<br>

#### 👉 DispatcherServlet 파헤치기

<br>

#### 👉 데이터 변환과 검증 

<br>

#### 👉 IntelliJ 사용법 

<br>




## 📌 03. Spring DI와 AOP 

#### 🧑🏻‍🏫 주요 내용 작성

<img src="/images/아직.jpeg" width="800" height="500"/>

## 📌 04. MyBatis로 게시판 구현

#### 🧑🏻‍🏫 주요 내용 작성

<img src="/images/아직.jpeg" width="800" height="500"/>

## 📌 05. Spring MVC로 웹사이트 만들어보기 

#### 🧑🏻‍🏫 주요 내용 작성

<img src="/images/스프링오브젝트.jpeg" width="800" height="500"/>