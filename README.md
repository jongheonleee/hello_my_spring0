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

```java

// 컨트롤러 처리 내용 자바 코드로 구현해보기 
public class MethodCall3 {
	public static void main(String[] args) throws Exception{
        // 1. 쿼리스트링으로 넘어오는 값 -> ?year=2021&month=10&day=1
		Map map = new HashMap();
		map.put("year", "2021");
		map.put("month", "10");
		map.put("day", "1");

        // 2. 리플렉션 API를 활용한 객체 생성 및 메서드 호출  
		Model model = null;
		Class clazz = Class.forName("com.fastcampus.ch2.YoilTellerMVC");
		Object obj  = clazz.newInstance();
		Method main = clazz.getDeclaredMethod("main", int.class, int.class, int.class, Model.class); // YoilTellerMVC.main(int year, int month, int day, Model model);
		
        Parameter[] paramArr = main.getParameters(); // main의 파라미터 정보를 가져옴
		Object[] argArr = new Object[main.getParameterCount()]; // main의 파라미터 개수만큼 배열 생성
		
		for(int i=0;i<paramArr.length;i++) {
			String paramName = paramArr[i].getName(); // 파라미터 이름
			Class  paramType = paramArr[i].getType(); // 파라미터 타입
			Object value = map.get(paramName); 

            // 파라미터 형태가 다음과 같음 {2021, 10, 1, {}}
            // 파라미터의 값을 맵에 저장해서 전달. 컨트롤러에서 사용하게끔 만듦 
			// paramType중에 Model이 있으면, 생성 & 저장 
			if(paramType==Model.class) {
				argArr[i] = model = new BindingAwareModelMap(); 
			} else if(value != null) {  // map에 paramName이 있으면,
				// value와 parameter의 타입을 비교해서, 다르면 변환해서 저장  
				argArr[i] = convertTo(value, paramType);				
			} 
		}
		
		// Controller의 main()을 호출 - YoilTellerMVC.main(int year, int month, int day, Model model)
		String viewName = (String)main.invoke(obj, argArr);
        
		// 텍스트 파일을 이용한 rendering
		render(model, viewName);			
	} 
	
    // 데이터 타입 변환 메서드 
	private static Object convertTo(Object value, Class type) {
		if(type==null || value==null || type.isInstance(value)) // 타입이 같으면 그대로 반환 
			return value;

		// 타입이 다르면, 변환해서 반환
		if(String.class.isInstance(value) && type==int.class) { // String -> int
			return Integer.valueOf((String)value);
		} else if(String.class.isInstance(value) && type==double.class) { // String -> double
			return Double.valueOf((String)value);
		}
			
		return value;
	}
	
    // 뷰 페이지 렌더링 메서드 
	private static void render(Model model, String viewName) throws IOException {
		String result = "";
		
		// 1. 뷰의 내용을 한줄씩 읽어서 하나의 문자열로 만든다.
		Scanner sc = new Scanner(new File("src/main/webapp/WEB-INF/views/"+viewName+".jsp"), "utf-8");
		
		while(sc.hasNextLine())
			result += sc.nextLine()+ System.lineSeparator();
		
		// 2. model을 map으로 변환 
		Map map = model.asMap();
		
		// 3.key를 하나씩 읽어서 template의 ${key}를 value바꾼다.
		Iterator it = map.keySet().iterator();
		
		while(it.hasNext()) {
			String key = (String)it.next();

			// 4. replace()로 key를 value 치환한다.
			result = result.replace("${"+key+"}", ""+map.get(key));
		}
		
		// 5.렌더링 결과를 출력한다.
		System.out.println(result);
	}
}

/* [실행결과] 
paramArr=[int year, int month, int day, org.springframework.ui.Model model]
argArr=[2021, 10, 1, {}]
viewName=yoil
[after] model={year=2021, month=10, day=1, yoil=금}
<%@ page contentType="text/html;charset=utf-8" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<%@ page session="false" %>
<html>
<head>
	<title>YoilTellerMVC</title>
</head>
<body>
<h1>2021년 10월 1일은 금요일입니다.</h1>
</body>
</html>
*/


```

```java
// 디스패처 서블릿 자바로 구현해보기 
    // (0) 요청 받고 적절한 메서드에게 위임
    // (1) 요청 데이터 타입 변환 - http는 텍스트 기반 프로토콜이므로 String을 알맞게 타입 변환해야함
    // (2) 응답 페이지 위치 생성기 
    // (3) 뷰 페이지 렌더링

// 요청 url : http://localhost/ch2/myDispatcherServlet?year=2021&month=10&day=1
// @WebServlet = @Controller + @RequestMapping
@WebServlet("/myDispatcherServlet")  
public class MyDispatcherServlet extends HttpServlet {
    
    // HttpServletRequest는 요청 정보를 저장하고 있는 객체를 의미함
    // HttpServletResponse는 응답 정보를 저장하고 있는 객체를 의미함
	@Override
	public void service(HttpServletRequest request, HttpServletResponse response) throws IOException {
        // 1. 작업에 필요한 정보 및 객체 생성 
		Map    map = request.getParameterMap();
		Model  model = null;
		String viewName = "";
		
		try {
            // 2. 리플렉션 API를 활용한 객체 생성 및 메서드 호출
			Class clazz = Class.forName("com.fastcampus.ch2.YoilTellerMVC");
			Object obj = clazz.newInstance();
			
      		// 2-1. main 메서드의 정보 조회 
			Method main = clazz.getDeclaredMethod("main", int.class, int.class, int.class, Model.class);
			
            // 2-2. main메서드의 매개변수 목록(paramArr)을 읽어서 메서드 호출에 사용할 인자 목록(argArr)을 만든다.
			Parameter[] paramArr = main.getParameters();
			Object[] argArr = new Object[main.getParameterCount()];

            // 2-3. main메서드의 매개변수 목록을 순회하면서, 각 매개변수의 타입과 이름을 조회하고, map에서 값을 꺼내서 변환해서 저장한다.
			for(int i=0;i<paramArr.length;i++) {
				String paramName = paramArr[i].getName();
				Class  paramType = paramArr[i].getType();
				Object value = map.get(paramName);

				// paramType중에 Model이 있으면, 생성 & 저장 
				if(paramType==Model.class) {
					argArr[i] = model = new BindingAwareModelMap();
				} else if(paramType==HttpServletRequest.class) {
					argArr[i] = request;
				} else if(paramType==HttpServletResponse.class) {
					argArr[i] = response;					
				} else if(value != null) {  // map에 paramName이 있으면,
					// value와 parameter의 타입을 비교해서, 다르면 변환해서 저장 
					String strValue = ((String[])value)[0];	// getParameterMap()에서 꺼낸 value는 String배열이므로 변환 필요 
					argArr[i] = convertTo(strValue, paramType);				
				} 
			}
			
			// 3. Controller의 main()을 호출 - YoilTellerMVC.main(int year, int month, int day, Model model)
			viewName = (String)main.invoke(obj, argArr); 	
		} catch(Exception e) {
			e.printStackTrace();
		}
				
		// 4. 텍스트 파일을 이용한 rendering
		render(model, viewName, response);			
	} 
	
    // (1) 데이터 타입 변환 메서드
	private Object convertTo(Object value, Class type) {
		if(type==null || value==null || type.isInstance(value)) // 타입이 같으면 그대로 반환 
			return value;
		
		// 타입이 다르면, 변환해서 반환
		if(String.class.isInstance(value) && type==int.class) { // String -> int
			return Integer.valueOf((String)value);
		} else if(String.class.isInstance(value) && type==double.class) { // String -> double
			return Double.valueOf((String)value);
		}
			
		return value;
	}
	
    // (2) 뷰 페이지 리소스 위치 문자열로 만들어서 반환 
	private String getResolvedViewName(String viewName) {
		return getServletContext().getRealPath("/WEB-INF/views") +"/"+viewName+".jsp";
	}
	
    // (3) 뷰 페이지 렌더링 메서드 
	private void render(Model model, String viewName, HttpServletResponse response) throws IOException {
		String result = "";
		
		response.setContentType("text/html");
		response.setCharacterEncoding("utf-8");
		PrintWriter out = response.getWriter();
		
		// 1. 뷰의 내용을 한줄씩 읽어서 하나의 문자열로 만든다.
		Scanner sc = new Scanner(new File(getResolvedViewName(viewName)), "utf-8");
		
		while(sc.hasNextLine())
			result += sc.nextLine()+ System.lineSeparator();
		
		// 2. model을 map으로 변환 
		Map map = model.asMap();
		
		// 3.key를 하나씩 읽어서 template의 ${key}를 value바꾼다.
		Iterator it = map.keySet().iterator();
		
		while(it.hasNext()) {
			String key = (String)it.next();

			// 4. replace()로 key를 value 치환한다.
			result = result.replace("${"+key+"}", map.get(key)+"");
		}
		
		// 5.렌더링 결과를 출력한다.
		out.println(result);
	}
}

```


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