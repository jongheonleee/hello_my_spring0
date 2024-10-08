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


> - <img src="/images/원격프로그램실행.jpeg" width="400" height="400"/>
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

> - <img src="/images/HttpServletRequest와HttpServletResponse.jpeg" width="400" height="400"/>
> - HttpServletRequest란? 요청 정보를 저장하고 있는 객체를 의미함
>   - url 자체는 문자열. 해당 요청 문자열을 저장하고 활용할 수 있게 해주는 객체
>   - 한마디로 url 요청 문자열을 저장하고 있는 객체를 의미함
>   
> - HttpServletResponse란? 응답 정보를 저장하고 있는 객체를 의미함
>   - 브라우저에 정보를 보여줄 때 활용함
>   - 해당 객체를 이용해서 자바코드로 HTML ... 을 만들어서 브라우저에서 보여줄 수 있음

<br>

#### 👉 서버가 제공하는 리소스

> - <img src="/images/리소스종류.jpeg" width="400" height="400"/>
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

> - <img src="/images/Tomcat구조.jpeg" width="400" height="400"/>
> - 서블릿이란? 작은 서버 프로그램을 의미함. 예를들어, 컨트롤러, ... 이 있음
> - 요청처리 전과정은 밑에와 같음
>   - Thread -> Connector -> Engine -> filter -> DispatcherServlet -> Controller -> 매핑된 메서드 호출 


<br>

#### 👉 Tomcat의 설정 파일

> - <img src="/images/Tomcat설정파일.jpeg" width="400" height="400"/>
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

> - 프로토콜이란? 아래와 같음
>   - 서로 간의 통신을 위한 약속, 규칙
>   - 주고 받을 데이터에 대한 형식을 정의함
>   - 프로토콜은 편지 우편 체계와 매우 유사함
>   
> - HTTP란? 
>   - Hyper Text Transfer Protocol의 약자로, 웹에서 데이터를 주고 받을 때 사용하는 프로토콜을 의미함
>   - 프로토콜의 일종으로 텍스트 기반의 프로토콜임
>   - 단순하고 읽기 쉬운 구조임
>   - 상태를 저장하지 않음(stateless)
>     - 클라이언트 정보를 서버에 저장하지 않음. 이 때문에 '쿠키, 세션, 쿼리스트링을 활용함'
>   - 확장 가능함
>     - HTTP 응답 메시지는 헤더와 바디로 구성됨
>     - 헤더에는 '헤더이름 : 값' 형식으로 구성
>       - 표준에 정해놓지 않음. 헤더를 추가할 수 있음. 이를 '커스텀 헤더'라고함
>     - 바디에는 '텍스트, 바이너리'과 같은 데이터로 구성됨


<br>

#### 👉 HTTP 요청과 메시지

> - <img src="/images/HTTP메시지.jpeg" width="400" height="400"/>
> - 크게 2가지 요청 메서드로 나뉨
>   - (1) GET : 데이터를 요청할 때 사용함
>   - (2) POST : 데이터를 전송할 때 사용함
> - GET은 리소스를 얻어오기 위함. 바디가 없음
> - 쿼리스트링으로 추가 데이터를 보낼 수 있음
> - GET은 Read(읽기)에 사용함
> 
> - POST는 리소스를 등록하거나 작성할 때 주로 사용함. 그래서 바디가 있음
> - 바디에 서버에서 전송할 데이터가 존재함
> - POST는 Write(글쓰기)에 사용함.
>   - 예를들어서, 글쓰기, 로그인, 회원가입, 파일첨부, ... 등이 해당함

<br>

#### 👉 GET과 POST의 비교

> - <img src="/images/GET과POST비교.png" width="400" height="400"/>


<br>

#### 👉 텍스트와 바이너리

> - <img src="/images/바이너리와텍스트비교.png" width="400" height="400"/>
> - 데이터는 크게 '문자'와 '숫자'로 구성
> - 바이너리 파일 : '문자' + '숫자'로 구성된 파일
> - 텍스트 파일 : '문자'로만 구성된 파일
> 
> - 숫자를 문자로 바꾼다는 것의 의미
> - <img src="/images/숫자를문자로변환.png" width="400" height="400"/>
> - 숫자를 문자로 변환하는 과정에서 메모리 크기가 변경될 수 있음
> - 텍스트 파일은 '읽기 쉬움' 하지만, 바이너리 파일은 '읽기 어려움'

<br>

#### 👉 MIME

> - MIME이란? Multipurpose Internet Mail Extensions
> - HTTP는 텍스트 기반의 프로톸콜
> - 하지만, HTTP로 바이너리 파일인 이미지, 동영상, ... 을 전송함
> - 이 과정에서 사용하는 것이 MIME
> - MIME이라는 것은 '전송할 데이터의 타입을 명시하는 것'을 의미함
>   - text, image, audio, video, application 등이 있음
>   - 이 하위에 서브 타입이 존재함
>   - text/html, text/css, ... 등 브라우저가 해당 정보를 참고해서 해석함
> - 즉, MIME은 content-type 헤더에 사용하여 데이터의 타입을 명시해줌으로써 브라우저가 적절히 해석할 수 있게 도와줌

<br>


#### 👉 Base64

> - <img src="/images/Base64.png" width="400" height="400"/>
> - <img src="/images/Base642.png" width="400" height="400"/>
> - 64 진법을 활용함, 데이터를 표현할 때 64개의 문자로 표현함
> - 64개 -> 2^6 -> 6비트로 구성된 데이터
> - 데이터를 6비트로 쪼갬
> - 바이너리 데이터를 텍스트 데이터로 변환하기 위해 사용함(숫자 -> 문자 변환)
> - 64진법 '0' ~ '9', 'A'~'Z', 'a'~'z', '+', '/'는 어떤 OS에서든 호환 가능함(한글 OS, 아랍 OS)
> - 위의 작업의 단점은 사이즈가 커짐
>   - 8bit + 8 bit -> 6bit + 6bit + 6bit + 6bit 



<br>

#### 👉 텍스트와 바이너리, MIME, Base64 정리

> - HTML은 텍스트 기반의 프로토콜이지만 현재는 해당 프로토콜로 바이너리 데이터들도 전송함
> - 이 과정에서 '숫자 -> 문자' 변환하는 작업이 필요함
> - 바이너리 데이터를 텍스트 기반의 HTTP 프로토콜로 전송하려면 2가지 방법이 있음
>   - (1) MIME 타입 쓰고 바이너리 그대로 넣음
>   - (2) Base64를 통해 바이너리를 텍스트로 변환해서 보냄 


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

> - <img src="/images/관심사의분리이론1.png" width="400" height="400"/>
> - <img src="/images/관심사의분리이론2.png" width="400" height="400"/>
> - <img src="/images/관심사의분리이론3.png" width="400" height="400"/>


<br>

#### 👉 서블릿과 JSP

> - 서블릿과 컨트롤러의 비교, 스프링은 서블릿이 발전된 형태 
> - <img src="/images/서블릿생명주기.png" width="400" height="400"/>
> - JSP란? 'Java Server Pages'의 약자로, 서블릿과 유사한 형태임
> - <% ~ %> 안에 자바 코드 작성함
> - 결국에는 자바 클래스와 유사한 형태임
> - <img src="/images/JSP호출과정.png" width="400" height="400"/>
> - 요청할 때 그때 서블릿을 생성하고 등록함, lazy-init
> - 스프링은 이 부분을 개선하고자 미리 등록해서 사용하게 만듦, early-init
> - <JSP와 서블릿으로 변환된 JSP의 비교>
> - <img src="/images/JSP와서블릿비교.png" width="400" height="400"/>
> - JSP의 기본 객체는 생성없이 사용할 수 있는 객체를 의미함
>   - service 메서드의 lv
>   - request, response, pageContext, ...

<br>

#### 👉 유효범위(scope)와 속성(attribute)


> - <img src="/images/전체스코프와속성그림.png" width="400" height="400"/>
> - <img src="/images/전체스코프와속성그림1.png" width="400" height="400"/>
> - <img src="/images/전체스코프와속성그림2.png" width="400" height="400"/>
> - <img src="/images/전체스코프와속성그림3.png" width="400" height="400"/>
> - <img src="/images/전체스코프와속성그림6.png" width="400" height="400"/>
> - <img src="/images/전체스코프와속성그림4.png" width="400" height="400"/>
> - <img src="/images/전체스코프와속성그림5.png" width="400" height="400"/>
> - HTTP 특징은 stateless임. 상태정보를 저장하지 않음
>   - 이에 따라, '저장소'가 필요함
>   
> - '저장소'는 범위에 따라서 4개로 구분함. 크게 2가지 특징이 있음
>   - (1) 접근범위
>   - (2) 생존기간
>   
> - '저장소'는 기본적으로 '맵'으로 구성되어 있음
>   - (1) pageContext
>     - lv를 저장하는 저장소
>     - 기본객체 request, response가 있음
>     - 특정 page 내에서만 접근 가능함(읽기, 쓰기). 다른 페이지에서 접근하지 못함
>     - 이때, 값을 사용할 때는 EL 태그나 <%= ~ %>를 사용함
> 
>   - (2) application
>     - web application 전체에서 접근 가능한 저장소
>     - 여러 페이지에서 접근 가능함. 쓰기할 때는 setAttribute()를 사용함. 읽기할 때는 getAttribute()를 사용함
>     - 전체 application에서 공유해서 사용하는 저장소이기 때문에 특정 상용자의 데이터를저장하는 것은 바람직하지 않음
>       - 이로 인해 session 등장
>   
>   - (3) session
>     - 특정 클라이언트에 대한 개별 저장소
>     - 클라이언트마다 개별적으로 할당되는 저장소이기 때문에 개별적인 데이터를 저장하기에 적합함. 예를들어, id, email 등이 있음
>     - 세션은 쿠키를 이용해서 이 세션 객체가 어떤 사람 것인지 연결해주는 역할을함
>     - 세션에는 id, email, ... 등이 있음
>     - 세션은 쿠키를 이용해서 이 세션 객체가 어떤 사람 것인지 연결해주는 역할을 함
>     - 세션에는 id, 장바구니, ... 을 담기에 좋음
>     - 무분별한 세션 사용은 좋지 않음. 사용자마다 1개 개별 저장소가 부여되기 때문에 사용자수가 많으면 많을수록 성능은 저하됨
>     - 서버 부담이 젤 큰 객체. 최소한의 데이터만 저장해야함
>   
>   - (4) request 
>     - 사용자마다 독립적이며 요청할 때 마다 생성되는 객체임
>     - 주로 요청 보내는 시점부터 작업이 완료될 때 까지 유효함, forward 처리가 그 예시임
>     - forward 처리하면 다른 jsp 페이지에서도 request 객체를 사용할 수 있음
>     - 가능하면 request 객체를 최대한 활용해보고 안되면 session 객체를 사용함


<br>

#### 👉 URL 패턴

> - @WebServlet으로 서블릿을 URL에 매핑할 때 사용
> - 패턴 종류에는 크게 4가지가 있음
>   - (1) exact mapping : 정확히 일치하는 경우
>   - (2) path mapping : 일부 경로가 일치하는 경우
>   - (3) extension mapping : 확장자가 일치하는 경우
>   - (4) default mapping : 모든 요청에 대한 매핑
> 
> - 스프링에서도 url pattern이 있음. @RequestMapping을 사용함
> - <img src="/images/URL패턴.png" width="400" height="400"/>
> - 스프링에서는 DispatcherServlet이 Children과 ServletMappingr을 위와 유사한 형태로 서블릿(컨트롤러)들을 가지고 있음
> - 즉, DispatcherServlet이 URL 매핑과 그에 대한 서블릿(컨트롤러)들을 보관하고 관리하고 있음
> - 모든 요청은 DispatcherServlet이 받게 되어 있음(Front-Controller). servlet-mapping 을 보면 url-pattern이 '/'로 되어 있음

<br>

#### 👉EL 태그 
> - EL 태그란? Expression Language의 약자로, JSP에서 사용하는 표현식 언어를 의미함
> - <%= ~ %> 을 ${ ~ } 형식으로 작성하게끔 바꿔줌. 이는 여러면에서 편리한 경우가 많음
> - EL 태그에서 특정 값을 사용할 때 scope를 탐색해서 해당 값을 조회함
> - <img src="/images/스코프체인탐색.png" width="400" height="400"/>
> - 자바에서는 "1" + 1 -> "11" 이지만, EL에서는 "1" + 1 -> 2로 계산함
> 
> - empty 는 크게 2가지 부분을 확인해줌
>   - (1) null 여부
>   - (2) 빈 컬렉션 배열
> - 위의 조건을 하나라도 충족하면 true를 반환함
> - EL은 lv를 사용못함. 저장소에 저장된 것을 사용함

<br>

#### 👉JSTL
> - JSTL이란? JSP Standard Tag Library의 약자로, JSP에서 사용하는 표준 태그 라이브러리를 의미함
> - <img src="/images/JSTL.png" width="400" height="400"/>
> - 접두사 <c 사용. 형식화에서는 <fmt 사용
> - 맨위에 설정 라인에 넣어줘야함


<br>

#### 👉Filter
> - 공통적인 요청 전처리와 응답 후처리에 사용함. 주로 로깅, 인코딩, 수행시간 측정 ... 에 사용함
> - <img src="/images/Filter적용그림.png" width="400" height="400"/>
> - 필터는 n개로 구성할 수 있음. AOP 기능과 유사함


<br>

#### 👉 @RequestParam과 @ModelAttribute

```java
// RequestParamTest
@Controller
public class RequestParamTest {
    @RequestMapping("/requestParam")
    public String main(HttpServletRequest request) {
        String year = request.getParameter("year");
//		http://localhost/ch2/requestParam         ---->> year=null
//		http://localhost/ch2/requestParam?year=   ---->> year=""
//		http://localhost/ch2/requestParam?year    ---->> year=""
        System.out.printf("[%s]year=[%s]%n", new Date(), year);
        return "yoil";
    }

    @RequestMapping("/requestParam2")
//	public String main2(@RequestParam(name="year", required=false) String year) {   // 아래와 동일 
    public String main2(String year) {
//		http://localhost/ch2/requestParam2         ---->> year=null
//		http://localhost/ch2/requestParam2?year    ---->> year=""
        System.out.printf("[%s]year=[%s]%n", new Date(), year);
        return "yoil";
    }

    @RequestMapping("/requestParam3")
//		public String main3(@RequestParam(name="year", required=true) String year) {   // 아래와 동일 
    public String main3(@RequestParam String year) {
//		http://localhost/ch2/requestParam3         ---->> year=null   400 Bad Request. required=true라서 
//		http://localhost/ch2/requestParam3?year    ---->> year=""
        System.out.printf("[%s]year=[%s]%n", new Date(), year);
        return "yoil";
    }

    @RequestMapping("/requestParam4")
    public String main4(@RequestParam(required=false) String year) {
//		http://localhost/ch2/requestParam4         ---->> year=null 
//		http://localhost/ch2/requestParam4?year    ---->> year=""   
        System.out.printf("[%s]year=[%s]%n", new Date(), year);
        return "yoil";
    }

    @RequestMapping("/requestParam5")
    public String main5(@RequestParam(required=false, defaultValue="1") String year) {
//		http://localhost/ch2/requestParam5         ---->> year=1   
//		http://localhost/ch2/requestParam5?year    ---->> year=1   
        System.out.printf("[%s]year=[%s]%n", new Date(), year);
        return "yoil";
    }

// =======================================================================

    @RequestMapping("/requestParam6")
    public String main6(int year) {
//		http://localhost/ch2/requestParam6        ---->> 500 java.lang.IllegalStateException: Optional int parameter 'year' is present but cannot be translated into a null value due to being declared as a primitive type. Consider declaring it as object wrapper for the corresponding primitive type.
//		http://localhost/ch2/requestParam6?year   ---->> 400 Bad Request, nested exception is java.lang.NumberFormatException: For input string: "" 
        System.out.printf("[%s]year=[%s]%n", new Date(), year);
        return "yoil";
    }

    @RequestMapping("/requestParam7")
    public String main7(@RequestParam int year) {
//		http://localhost/ch2/requestParam7        ---->> 400 Bad Request, Required int parameter 'year' is not present
//		http://localhost/ch2/requestParam7?year   ---->> 400 Bad Request, nested exception is java.lang.NumberFormatException: For input string: "" 
        System.out.printf("[%s]year=[%s]%n", new Date(), year);
        return "yoil";
    }

    @RequestMapping("/requestParam8")
    public String main8(@RequestParam(required=false) int year) {
        //	http://localhost/ch2/requestParam8        ---->> 500 java.lang.IllegalStateException: Optional int parameter 'year' is present but cannot be translated into a null value due to being declared as a primitive type. Consider declaring it as object wrapper for the corresponding primitive type.
        //	http://localhost/ch2/requestParam8?year   ---->> 400 Bad Request, nested exception is java.lang.NumberFormatException: For input string: "" 
        System.out.printf("[%s]year=[%s]%n", new Date(), year);
        return "yoil";
    }

    @RequestMapping("/requestParam9")
    public String main9(@RequestParam(required=true) int year) {
        //	http://localhost/ch2/requestParam9        ---->> 400 Bad Request, Required int parameter 'year' is not present
        //	http://localhost/ch2/requestParam9?year   ---->> 400 Bad Request, nested exception is java.lang.NumberFormatException: For input string: "" 
        System.out.printf("[%s]year=[%s]%n", new Date(), year);
        return "yoil";
    }

    @RequestMapping("/requestParam10")
    public String main10(@RequestParam(required=true, defaultValue="1") int year) {
        //	http://localhost/ch2/requestParam10        ---->> year=1   
        //	http://localhost/ch2/requestParam10?year   ---->> year=1   
        System.out.printf("[%s]year=[%s]%n", new Date(), year);
        return "yoil";
    }

    @RequestMapping("/requestParam11")
    public String main11(@RequestParam(required=false, defaultValue="1") int year) {
//		http://localhost/ch2/requestParam11        ---->> year=1   
//		http://localhost/ch2/requestParam11?year   ---->> year=1   
        System.out.printf("[%s]year=[%s]%n", new Date(), year);
        return "yoil";
    }
}

// SetterCall

public class SetterCall {
    public static void main(String[] args) throws Exception{
        Map<String, String> map = new HashMap<>();
        map.put("year", "2021");
        map.put("month", "10");
        map.put("day", "1");

        Class<?> type = Class.forName("com.fastcampus.ch2.MyDate");

        // MyDate인스턴스를 생성하고, map의 값으로 초기화한다. 
        Object obj = dataBind(map, type);
        System.out.println("obj="+obj); // obj=[year=2021, month=10, day=1]
    } // main

    private static Object dataBind(Map<String, String> map, Class<?> clazz) throws Exception {
        // 1. MyDate인스턴스 생성
//		Object obj = clazz.newInstance(); // deprecated method
        Object obj = clazz.getDeclaredConstructor().newInstance(new Object[0]);

        // 2. MyDate인스턴스의 setter를 호출해서, map의 값으로 MyDate를 초기화
        // 	 2-1. MyDate의 모든 iv를 돌면서 map에 있는지 찾는다.
        // 	 2-2. 찾으면, 찾은 값을 setter로 객체에 저장한다.
        Field[] ivArr = clazz.getDeclaredFields();

        for(int i=0;i<ivArr.length;i++) {
            String name = ivArr[i].getName();
            Class<?>  type = ivArr[i].getType();

            // map에 같은 이름의 key가 있으면 가져와서 setter호출 
            Object value = map.get(name); // 못찾으면 value의 값은 null
            Method method = null;

            try {   // map에 iv와 일치하는 키가 있을 때만, setter를 호출
                if(value==null) continue;

                method = clazz.getDeclaredMethod(getSetterName(name), type); // setter의 정보 얻기	
                System.out.println("method="+method);
                method.invoke(obj, convertTo(value, type)); // obj의 setter를 호출
            } catch(Exception e) {
                e.printStackTrace();
            }
        }

        System.out.println(Arrays.toString(ivArr));

        return obj;
    }

    private static Object convertTo(Object value, Class<?> type) {
        // value의 타입과 type의 타입이 같으면 그대로 반환
        if(value==null || type==null || type.isInstance(value))
            return value;

        // value의 타입과 type이 다르면, 변환해서 반환
        if(String.class.isInstance(value) && type==int.class) // String -> int
            return Integer.valueOf(""+value);

        return value;
    }

    // iv의 이름으로 setter의 이름을 만들어서 반환하는 메서드("day" -> "setDay")
    private static String getSetterName(String name) {
//		return "set"+name.substring(0,1).toUpperCase()+name.substring(1);
        return "set" + StringUtils.capitalize(name); // org.springframework.util.StringUtils
    }
}

/*
[실행결과]
method=public void com.fastcampus.ch2.MyDate.setYear(int)
method=public void com.fastcampus.ch2.MyDate.setMonth(int)
method=public void com.fastcampus.ch2.MyDate.setDay(int)
[private int com.fastcampus.ch2.MyDate.year, private int com.fastcampus.ch2.MyDate.month, private int com.fastcampus.ch2.MyDate.day]
obj=[year=2021, month=10, day=1]
 */

```

> - @RequestParam은 요청 파라미터를 연결할 매개변수에 붙이는 애노테이션. 기본적으로 생략 가능함
> - 컨트롤러에서 파라미터가 필수 입력일 때는 예외처리하고 그게 아니면 안해도됨
> - 컨트롤러에 여러개의 파라미터가 전달되는 경우. 해당 파라미터를 객체로 묶어서 처리하는게 유용함
> - 객체에 값이 담기는 작업을 내부적으로 어떻게 돌아가는지 보여줌. 데이터 바인드에 의해 처리됨

<br>

#### 👉 @RequestMapping

> - 적용대상을 Model 의 속성으로 자동추가해주는 애너테이션
> - 반환타입 또는 컨트롤러 메서드의 매개변수에 적용 가능함
> - <img src="/images/ModelAttribute적용그림.png" width="400" height="400"/>
> - 컨트롤러 파라미터에서 참조형 매개변수 앞에 @ModelAttribute를 생략할 수 있음
> - 컨트롤러 매개변수에 붙일 수 있는 애노테이션은 2개임
>   - (1) @RequestParam - 기본형, String에 사용함
>   - (2) ModelAttribute - 참조형(객체)
>

<br>

#### 👉 WebDataBinder 

> - <img src="/images/웹데이터바인더1.png" width="400" height="400"/>
> - 컨트롤러 메서드에서 적용되는 객체 
> - 클라이언트 요청에 담겨있는 데이터에 대한 전처리 작업을 담당함
> - 크게 2가지 작업을 처리함
>   - (1) 타입변환 : 데이터를 변환한 결과나 에러를 bindingResult에 저장함
>   - (2) 검증 : 타입 변환을 거친 데이터에 대해 데이터 검증을 처리하고 이 결과를 bindingResult에 저장함
> - 타입 변환, 데이터 검증을 처리한 결과나 에러를 bindingResult에 담고 이를 컨트롤러에 넘겨줌
> - 컨트롤러는 bindingResult를 가지고 작업 처리를 할 수 있게됨
> - @ExceptionHandler가 붙은 예외처리하는 메서드에서도 bindingResult를 사용할 수 있음

<br>

#### 👉 회원가입 화면 작성하기 

> - form은 기본적으로 GET 방식으로 전송함. 하지만, 주로 POST 방식으로 설정헤서 요청하는 경우가 많음
>   - action은 요청을 보낼 URL
>   - method 요청을 보내는 메서드 형식 - GET, POST
>   - onsubmit은 이벤트 발생할 때 자스로 핸들링할 함수를 연결함
> - 브라우저에서 데이터를 전송할 때 아스키가 아닌 것들은 URL 인코딩 처리됨
> - 특정 필드에 여러 데이터가 담긴 경우 ${paramValues}와 같이 작성해야함
> - 프론트단에서는 이벤트가 발생했을 때 자스로 1차 데이터 검증을 처리할 수 있음


<br>

#### 👉 @GetMapping과 @PostMapping

```java

// 1. 
model.addAttribute("msg", msg);
return "redirect:/register/add";

// 2. 
return "redirect:/register/add?msg="+msg;


// RequestMappingTest
@Controller
public class RequestMappingTest {
    //  @RequestMapping({"/login/hello.do", "/login/hi.do"}) 
    @RequestMapping("/login/hello.do") // http://localhost/ch2/login/hello.do
    public void test1(){
        System.out.println("urlpattern=/login/hello.do");
    }

    @RequestMapping("/login/*")   // /login/hello, /login/hi
    public void test2(){
        System.out.println("urlpattern=/login/*");
    }

    @RequestMapping("/login/**/tmp/*.do")   // /login/tmp/hello.do, /login/aaa/tmp/hello.do
    public void test3(){
        System.out.println("urlpattern=/login/**/tmp/*.do");
    }

    @RequestMapping("/login/??")
    public void test4(){   // /login/hi, /login/my.car
        System.out.println("urlpattern=/login/??");
    }

    @RequestMapping("*.do") // /hello.do, /hi.do, /login/hi.do
    public void test5(){
        System.out.println("urlpattern=*.do");
    }

    @RequestMapping("/*.???") //  /hello.aaa, /abc.txt
    public void test6(){
        System.out.println("urlpattern=*.???");
    }
}

```

> - @RequestMapping에 method 쓰는 방식 대신에 사용. 간략하게 사용할 수 있음
> - @RequestMapping을 간단하게 쓸수 있는 것이 @GetMapping과 @PostMapping임
> - 회원등록 실패시 리다이렉트를 처리할 때, 컨트롤러 처리 과정을 보면 위의 두 코드는 서로 일치하게 동작함
> - @RequestMapping의 URL 패턴 처리는 아래와 같음
>   - (1) exact mapping : 정확히 일치하는 경우
>   - (2) path mapping : 일부 경로가 일치하는 경우
>   - (3) extension mapping : 확장자가 일치하는 경우

<br>

#### 👉 URL 인코딩 - 퍼센트 인코딩

> - URL에 포함된 non-ASCII 문자를 문자 코드(16 진수) 문자열로 변환함
> - 요청을 받은 서버가 어떤 OS, 어떤 인코딩을 사용하는지 알 수 없음. 그래서 아스키를 활용해야함(인코딩 처리)
> - <img src="/images/URL인코딩처리.png" width="400" height="400"/>
> - 문자 코드를 UTF-8 문자열로 변환하는 작업. 문자코드(숫자) <-> 문자열
> - 브라우저에서 데이터를 전송할 때 브라우저가 URL 인코딩 처리해서 전송함

<br>

#### 👉 redirect와 forward

> - <img src="/images/redirect처리과정.png" width="400" height="400"/>
> - <img src="/images/forward처리과정.png" width="400" height="400"/>
> - redirect는 요청이 총 2번 이루어지고 각 요청의 request 객체는 서로 다른 객체임
> - 하지만, forward는 요청이 한 번이고 request 객체도 동일한 객체임

<br>

#### 👉 스프링에서 Redirect와 Forward 처리 과정

> - <img src="/images/스프링redirect처리과정.png" width="400" height="400"/>
> - <img src="/images/스프링forward처리과정.png" width="400" height="400"/>
> - redirect가 일어날 경우, DS는 RedirectView를 호출해서 리다이렉트를 담은 응답 정보를 생성하고 클라이언트에게 전달함
> - 컨트롤러에서 String인 뷰 이름을 반환하면 DS는 InternalResourceViewResolver를 통해서 뷰이름을 해석해서 실제 리소스 위치를 생성함
> - DS는 다시 해당 위치 정보를 JstlView에게 전달하고 JstlView는 해당 JSP에게 Model을 넘겨줌
> - JSP는 최종 응답을 생성해서 클라이언트에게 전달함



<br>

#### 👉 쿠키란?

> - 쿠키는 클라이언트 식별 기술
> - 이름과 값의 쌍으로 구성된 작은 정보, 아스키 문자만 가능함
>   - 도메인, 경로, 유효기간, 아이디, ... 을 주로 저장함
> - 서버에서 생성해서 브라우저에 저장함
> - 서버 요청시 domain, path 가 일치해야 전송함
> - HTTP 응답/요청 헤더에 쿠기가 등록된 상태로 전달됨
> 
> - 쿠키 생성 및 삭제 
> - <img src="/images/쿠키생성.png" width="400" height="400"/>
> - <img src="/images/쿠키삭제.png" width="400" height="400"/>
> - 쿠키 삭제할 때는 유효기간을 0으로 설정해주면됨
> - 쿠키에 한글, ... 을 저장할 때는 URLEncoder를 통해 인코딩해서 저장해야함

<br>

#### 👉 세션이란?

> - 세션은 서로 관련된 요청들을 하나로 묶은 것을 의미함
> - 브라우저마다 세션(개별 저장소)을 서버에서 제공함
> - 쿠키는 브라우저에 저장되고 세션은 서버에 저장됨
> - 세션을 삭제하는 방법에는 2가지가 있음
>   - (1) 수동종료 : invalidate()
>   - (2) 자동종료 : time-out
> - 브라우저에서 세션을 사용하기 위해 쿠키에 저장해둠
> - 이를 통해 추후에 요청을 보낼 때도 브라우저에서 온 요청이 이전의 요청과 같은지 다른지 판단할 수 있음

<br>

#### 👉 쿠키 VS 세션
> - <img src="/images/쿠키세션비교.png" width="400" height="400"/>


<br>

#### 👉 세션 실습

> - <img src="/images/세션실습1.png" width="400" height="400"/>
> - <img src="/images/세션실습2.png" width="400" height="400"/>
> - <img src="/images/세션실습3.png" width="400" height="400"/>
> - <img src="/images/세션실습4.png" width="400" height="400"/>
> - <img src="/images/세션실습5.png" width="400" height="400"/>
> - 개발을 진행하기 앞서 항상 그림을 그려서 작업틀을 구상해 놓아야함
> - 그림 그리는 것이 설계임
> - 메인 화면에서 메뉴 부분에서 Login/Logout을 보여줄 때 세션 스코프에 아이디가 있는지 없는지 여부로 처리함
> - 로그인 후, 게시판으로 이동시킬 때 각 페이지마다 URL이 어떻게 되는지 from, to 형식으로 직접 작성해보기
>   - 이 과정을 통해 알 수 있는 것은 from url을 저장해서 사용한다는 사실임
> - GET 방식에 쿼리스트링을 활용함. ?toURL='~~'에 from URL을 담고 로그인 페이지에서 input hidden에 from URL 저장해둠
> - 로그인 성공시 from URL로 이동시킴
> - 세션은 서버에 부담이 가는 작업. 따라서 유지기간이 짧을수록 좋음
> - <세션을 언제 시작할까 이미지>
> 
> - 위 과정을 처리하기 위해 세션이 필요없는 고세서는 session=false 처리함. 필요하다면 session=true 처리
> - session=false는 세션을 없애는게 아니라 session을 새로 생성 안한다는 의미임. 즉, session=false는 기존의 세션이 끊기는게 아님
> - 이를 적용하기 위해선 <%@ page session="false" %>를 JSP 상단에 적어 주면됨
> - @CookieValue 애노테이션이 있음. 해당 애노테이션은 쿠키에 존재하는 특정 이름의 값이 있으면 컨트롤러의 메서드 파라미터로 받아서 쓸 수 있게함
> - @CookieValue("id") String coolieId 형식으로 컨트롤러 메서드의 파라미터에 사용함



<br>

#### 👉 예외처리 1

```java
// ExceptionController - 특정 컨트롤러에서 발생하는 예외 처리기 
@Controller
public class ExceptionController {
    @ExceptionHandler({NullPointerException.class, FileNotFoundException.class})
    public String catcher2(Exception ex, Model m) {
        m.addAttribute("ex", ex);
        return "error";
    }

    @ExceptionHandler(Exception.class)
    @ResponseStatus(HttpStatus.INTERNAL_SERVER_ERROR) // 200 -> 500
    public String catcher(Exception ex, Model m) {
        System.out.println("catcher() in ExceptionController");
        System.out.println("m="+m);
//		m.addAttribute("ex", ex);

        return "error";
    }

    @RequestMapping("/ex")
    public String main(Model m) throws Exception {
        m.addAttribute("msg", "message from ExceptionController.main()");
        throw new Exception("¿¹¿Ü°¡ ¹ß»ýÇß½À´Ï´Ù.");
    }

    @RequestMapping("/ex2")
    public String main2() throws Exception {
        throw new NullPointerException("¿¹¿Ü°¡ ¹ß»ýÇß½À´Ï´Ù.");
    }
}

// GlobalController - 전역 예외 처리기 

@ControllerAdvice("com.fastcampus.ch3") 
public class GlobalCatcher {
    @ExceptionHandler({NullPointerException.class, FileNotFoundException.class})
    public String catcher2(Exception ex, Model m) {
        m.addAttribute("ex", ex);
        return "error";
    }

    @ExceptionHandler(Exception.class)
    public String catcher(Exception ex, Model m) {
        m.addAttribute("ex", ex);

        return "error";
    }
}
```
> - <img src="/images/예외처리1.png" width="400" height="400"/>
> - <img src="/images/예외처리2.png" width="400" height="400"/>
> - 컨트롤러에서 발생되는 공통에러를 처리하는 메서드를 만들 수 있음. 이때, 사용되는 것이 @ExcceptionHandler 애노테이션임
> - 어떤 예외일 때 해당 메서드가 호출되는지 지정할 수 있음
> - 그렇게 하면 해당 예외들은 @ExceptionHandler에 명시해야함
> - 이를 통해서 컨트롤러 내부에서 발생되는 중복된 예외처리 로직을 공통적으로 관리할 수 있음
> 
> - 여러 컨트롤러에서 발생하는 중복된 예외 처리 로직을 하나의 클래스로 효율적으로 다룰 수 있음. 이때 사용하는 애노테이션이 @ControllerAdvice임
> - 만약 @ExceptionHandler와 @ControllerAdvice가 동시에 적용된 경우 가까운 위치인 @ExceptionHandler가 호출됨
> - @ControllerAdvice에는 패키지를 지정해 줄 수 있음. 그러면 @ControllerAdvice는 해당 페키지에서 발생한 예외들만 처리하게됨
> 
> - 위에 부분을 요약하자면 @ExceptionHadnler를 통해 컨트롤러에서 발생하는 예외를 처리할 수 있음(개별 예외 처리)
> - @ControllerAdvice로 전역 예외 처리 클래스를 작성 가능함(물론, 적용할 패키지 영역 지정 가능함)

<br>

#### 👉 @ResponseStatus


```java
// (1) 예외 처리 매서드에 붙이는 경우
@Controller
public class ExceptionController {

    @ExceptionHandler(Exception.class)
    @ResponseStatus(HttpStatus.INTERNAL_SERVER_ERROR) // 200 -> 500
    public String catcher(Exception ex, Model m) {
        System.out.println("catcher() in ExceptionController");
        System.out.println("m="+m);
        return "error";
    }
}

// (2) 사용자 예외 클래스에 붙이는 경우 
@ResponseStatus(HttpStatus.BAD_REQUEST) // 500 -> 400
class MyException extends RuntimeException {
    MyException(String msg) {
        super(msg);
    }
    MyException() { this(""); }
}

// JSP 맨 위에 선언 라인에 <%@ page isErrorPage="true" %>를 추가해야함
// <error-page> 태그를 사용함
// servlet-context.xml에 등록함 
```


> - @ResponseStatus는 응답 메시지의 상태 코드를 변경할 때 사용함
> - 주로 예외 처리 메서드에 붙임. 에러가 발생했을 때 에러 페이지를 보여주면, 응답 코드가 200이됨
> - 하지만 에러에 대핸 처리는 200이면 안됨. 이를 4xx, 5xx로 변환해야함
> - 주로 2가지 경우에 사용함
>   - (1) 예외 처리 매서드에 붙이는 경우
>   - (2) 사용자 예외 클래스에 붙이는 경우 
> - 컨트롤러에서 model의 객체에 예외 정보를 저장하지 않아도 error.jsp에서 pageContext의 exception 객체를 통해 예외 정보를 사용할 수 있음
> - 단, JSP 맨 위에 선언 라인에 <%@ page isErrorPage="true" %>를 추가해야함
> - web.xml에서 에러 코드별로 error-page를 지정할 수있음. 이때 <error-page> 태그를 사용함
> - SimpleMappingExceptionResolver를 통해서도 특정 예외 종류가 발생했을 때 보여줄 에러 페이지를 지정할 수 있음
> - 예외 종류 별 뷰 매핑에 사용, servlet-context.xml에 등록함

<br>

#### 👉 예외가 발생했을 때 처리하는 흐름

```java
// DispatcherServlet.properties 설정 파일 
# Default implementation classes for DispatcherServlet's strategy interfaces.
        # Used as fallback when no matching beans are found in the DispatcherServlet context.
# Not meant to be customized by application developers.

org.springframework.web.servlet.LocaleResolver=org.springframework.web.servlet.i18n.AcceptHeaderLocaleResolver

org.springframework.web.servlet.ThemeResolver=org.springframework.web.servlet.theme.FixedThemeResolver

org.springframework.web.servlet.HandlerMapping=org.springframework.web.servlet.handler.BeanNameUrlHandlerMapping,\
org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerMapping,\
org.springframework.web.servlet.function.support.RouterFunctionMapping

org.springframework.web.servlet.HandlerAdapter=org.springframework.web.servlet.mvc.HttpRequestHandlerAdapter,\
org.springframework.web.servlet.mvc.SimpleControllerHandlerAdapter,\
org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter,\
org.springframework.web.servlet.function.support.HandlerFunctionAdapter


org.springframework.web.servlet.HandlerExceptionResolver=org.springframework.web.servlet.mvc.method.annotation.ExceptionHandlerExceptionResolver,\
org.springframework.web.servlet.mvc.annotation.ResponseStatusExceptionResolver,\
org.springframework.web.servlet.mvc.support.DefaultHandlerExceptionResolver

org.springframework.web.servlet.RequestToViewNameTranslator=org.springframework.web.servlet.view.DefaultRequestToViewNameTranslator

org.springframework.web.servlet.ViewResolver=org.springframework.web.servlet.view.InternalResourceViewResolver

org.springframework.web.servlet.FlashMapManager=org.springframework.web.servlet.support.SessionFlashMapManager
```

> - ExceptionResolver 처리 과정 설명, 컨트롤러에서 발생할 예외가 DS에 넘어옴
> - DS에는 handlerExceptionResolver(DS의 iv)에 다음과 같이 3개의 예외 처리기(ExcptionHResolver)가 존재함
>   - (1) ExceptionHandlerResolver 
>     - @ExceptionHandler를 사용한 예외 처리
>   
>   - (2) ResponseStatusExceptionResolver
>     - @ResponseStatus를 사용한 예외 처리, web.xml 참고 
>   
>   - (3) DefaultHandlerExceptionResolver
>     - 스프링에 정의된 예외의 상태코드 500을 400, 500 으로 바꿔줌
> 
> - 다음 3가지는 DS가 가지고 있는 예외 처리 기본 전략임
> - 해당 전략은 DispatcherServlet.properties에 정의되어 있음

<br>

#### 👉 스프링에서의 예외 처리

> - (1) 컨트롤러 메서드 내에서 try-catch로 예외 처리
> - (2) 같은 컨트롤러 안에 @ExceptionHandler 메서드가 처리됨
> - (3) 예외 처리를 해주는 별도의 클래스를 정의한 @ControllerAdvice, @ExceptionHandler를 사용함
> - (4) 예외 종류별로 뷰 지정, SimpleMappingExceptionResolver를 사용함
> - (5) 응답 상태 토드별로 뷰 지정, <error-page>


<br>

#### 👉 DispatcherServlet 파헤치기

> - <img src="/images/DS1.png" width="400" height="400"/>
> - <img src="/images/DS2.png" width="400" height="400"/>
> - <img src="/images/DS3.png" width="400" height="400"/>
> - <img src="/images/DS4.png" width="400" height="400"/>
> - <img src="/images/DS5.png" width="400" height="400"/>
> - 서블릿은 기본적으로 '입력/처리/출력' 형식으로 구성됨
> - 이를 효율적으로 처리하기 위해선 그 앞단에 DS를 둬서 전처리 작업을 처리함(Front-Controller)
> - 물론 DS는 전처리 말고도 여러 작업을 처리함 
> 
> - 특정 URL로 요청이 들어오면 DS는 HandlerMapping에 등록된 메서드 중에 해당 URL을 처리해 주는 메서드를 호출함
> 
> - DS가 바로 Controller를 호출하는 것이 아니라 HandlerAdapter를 통해서 특정 Controller를 호출함
> - 느슨한 연결을 통해서 변경에 유리하게 구성함. 이를 통해서 DS는 Controller만 호출할 수 있는게 아니라 Servlet ... 여러 객체들을 호출할 수 있음
> 
> - DS의 ViewResolver는 컨트롤러로부터 전달받은 뷰 이름에 '접두사'와 '접미사'를 붙여서 실제 뷰 이름을 반환함
> 
> - dispatcherServlet.properties에는 DS의 기본 전략이 정의되어 있음, 주로 전략 패턴으로 구성됨
> - DispatcherServlet의 주요 메서드 처리는 다음과 같음
>   - (1) initStrategies(ApplicationContext context) 
>     - 기본 전략을 초기화함
>   
>   - (2) doService(HttpServletRequest request, HttpServletResponse response)
>     - doDispatch() 메서드를 호출함
>   
>   - (3) doDispatch(HttpServletRequest request, HttpServletResponse response)
>     - 실제 요청 처리
>   
>   - (4) processDispatchResult(HttpServletRequest request, HttpServletResponse response, HandlerExecutionChain mappedHandler, ModelAndView mv, Exception exception)
>     - 예외가 발생했는지 확인하고, 발생하지 않았으면 render() 메서드를 호출함
>   
>   - (5) render(ModelAndView mv, HttpServletRequest request, HttpServletResponse response)
>     - 응답 결과를 생성해서 전송함


<br>

#### 👉 데이터 변환

```java
// RegisterController 데이터 변환 기능 처리 
@Controller 
public class RegisterController {
    @GetMapping("/register/add") // 4.3부터 추가
    public String register() {
        return "registerForm";  // WEB-INF/views/registerForm.jsp
    }
    
    @PostMapping("/register/add")
    public String save(@ModelAttribute("user") User user, Model m) {
        if(!isValid(user)) {
            String msg = URLEncoder.encode("id를 잘못입력하셨습니다.", "utf-8");

            m.addAttribute("msg", msg);
            return "redirect:/register/add"; // 신규회원 가입화면으로 이동(redirect)
        }

        return "registerInfo";
    }

    private boolean isValid(User user) {
        return false;
    }

}
```

> - <img src="/images/웹데이터바인더.png" width="400" height="400"/>
> - WebDataBinder가 데이터 변환과 검증을 처리함
> - String인 "2021/12/31" 을 Date로 변환하는 기능 추가함
> - @InitBinder로 메서드를 정의하여 변환기를 등록할 수 있음
> - @DateTimeFormat을 사용해서 직접 명시해서 사용할 수도 있음
> - @InitBinder는 특정 클래스에서 사용할 변환기를 등록함. 여러 클래스에서 적용할 변환기 등록은 WebBinderInitializer를 구현한 후 등록함
> 
> - (1) PropertyEditor
>   - 양방향 타입 변환
>   - (String -> 타입, 타입 -> String), 특정 타입이나 이름의 필드에 적용 가능함
>   - 디폴트 PropertyEditor는 스프링이 제공함
>   - 커스텀 PropertyEditor는 사용자가 직접 구현, PropertyEditorSupport를 상속하면 편리함
> 
> - (2) Converter 
>   - 단방향 타입 변환
>   - (타입 A -> 타입 B)
>   - PropertyEditor는 iv를 사용하기 때문에 stateful함. Converter는 stateless임.
>   - <converter 이미지>
> 
>  - (3) Formatter
>    - 양방향 타입 변환
>    - (String -> 타입, 타입 -> String)
>    - 바인딩할 필드에 적용. @NumberFormat, @DateTimeFormat, 등이 있음
>

<br>

#### 👉 데이터 검증

```java
// Validator 인터페이스
public interface Validator {
    boolean supports(Class<?> clazz);
    void validate(Object target, Errors errors);
}

// UserValidator 클래스
public class UserValidator implements Validator {
    @Override
    public boolean supports(Class<?> clazz) {
//			return User.class.equals(clazz); // 검증하려는 객체가 User타입인지 확인
        return User.class.isAssignableFrom(clazz); // clazz가 User 또는 그 자손인지 확인
    }

    @Override
    public void validate(Object target, Errors errors) {
        System.out.println("LocalValidator.validate() is called");

        User user = (User)target;

        String id = user.getId();
        
        ValidationUtils.rejectIfEmptyOrWhitespace(errors, "id",  "required");
        ValidationUtils.rejectIfEmptyOrWhitespace(errors, "pwd", "required");

        if(id==null || id.length() <  5 || id.length() > 12) {
            errors.rejectValue("id", "invalidLength");
        }
    }
}

// Validator를 이용한 검증 자동 

// 글로벌 Validator servlet-context.xml에 등록하기 


// registerController, UserValidator 

// MessageSource 인터페이스 
public interface MessageSource {
    String getMessage(String code, @Nullable Object[] args, @Nullable String defaultMessage Locale locale);
    String getMessage(String code, @Nullable Object[] args, Locale locale) throws NoSuchMessageException;
}
```

> - Validator란? 객체를 검증하기 위한 인터페이스, 객체 거증기 구현에서 사용함 
> - 하나의 Validator로 여러 객체를 검증할 때, 글로벌 Validator로 등록함
> - 글로벌 Validator로 등록하는 방법은 위에와 같음 
> - 글로벌 Validator와 로컬 Validator를 동시에 적용할 수 있음
> - 이때, binder.addValidators(new 사용할 검증기()) 형식으로 추가해주면됨
>
> - MessageSource
> - 다양한 리소스(파일, 배열)에서 메시지를 읽기 위한 인터페이스
> - MessageSource를 사용하려면 프로퍼티 파일을 메시지 소스로 하는 ResourceBundleMessageSource를 등록함
> - 이때, error_message.properties 파일을 만들어서 에러 메시지를 작성함

<br>




## 📌 03. Spring DI와 AOP 

#### 🧑🏻‍🏫 주요 내용 작성

<img src="/images/아직.jpeg" width="800" height="500"/>


#### 👉 Spring DI 흉내내기


> - <img src="/images/다형성.png" width="400" height="400"/>
> - <img src="/images/외부파일1.png" width="400" height="400"/>
> - <img src="/images/외부파일2.png" width="400" height="400"/>
> - 변경에 유리한 코드를 만들기 위해선 '다형성'을 적극 활용해야함
> - 내부 코드는 '다형성'으로 작성하고 사용할 의존 오브젝트는 외부의 팩토리 메서드 패턴을 통해 전달받는 구조로 사용함
> - 즉, 관심사를 '사용'과 '생성'으로 구분하고 '사용'하는 쪽에서는 사용하는 오브젝트의 구체 대상을 알 필요없이 인터페이스를 활용하게 하여 다형성을 적극 활용함
> - Spring DI 흉내내는 과정을 살펴보면 다음과 같음 
>   - 다형성 -> 팩토리 메서드 패턴('사용'과 '생성' 구분) -> 외부 파일 분리(변경되는 부분인 오브젝트 생성을 외부 파일로 분리) 
> - 외부 파일을 사용하게 하는 경우, 프로그램 소스 코드를 변경하지 않아도 쉽게 확장할 수 있게 해줌
> - OOP에서 핵심중 하나는 '분리'. '분리'는 아래와 같이 세분화할 수 있음
>   - (1) 변하는 것과 변하지 않는 것
>   - (2) 관심사
>   - (3) 중복코드(AOP)

<br>

#### 👉 Spring Container에서 객체찾기

> - <img src="/images/스프링컨테이너1.png" width="400" height="400"/>
> - <img src="/images/자동주입1.png" width="400" height="400"/>
> - <img src="/images/자동주입2.png" width="400" height="400"/>
> - 기본적으로 스프링 컨테이너는 맵으로 구성되어 있음
> - byName, byType으로 객체를 찾음. 즉, 이름으로 탐색하냐 타입으로 탐색하냐의 차이
> - 또한, 특정 오브젝트에서 의존하고 있는 오브젝트를 런타임에 주입해 줄 수 있는데, 크게 2가지로 나뉨
>   - (1) @Autowired : 타입으로 찾아서 주입
>   - (2) @Resource : 이름으로 찾아서 주입
> - 스프링 빈에는 크게 2가지 스코프가 있음. 하나는 Singleton, 다른 하나는 Prototype임


<br>

#### 👉 Root AC와 Servlet AC

> - <img src="/images/RootAC와ServletAC1.png" width="400" height="400"/>
> - <img src="/images/RootAC와ServletAC2.png" width="400" height="400"/>
> - <img src="/images/RootAC와ServletAC3.png" width="400" height="400"/>
> - <img src="/images/RootAC와ServletAC4.png" width="400" height="400"/>
> - <img src="/images/RootAC와ServletAC5.png" width="400" height="400"/>
> - 스프링이 web.xml 설정 파일을 읽어서 두 개의 AC를 생성하고 서로 연결함(부모 자식 관계)
> - 하나는 none-web이고 다른 하나는 web임. 서로 부모 자식 관계로 구성됨

<br>

#### 👉 IoC와 DI 

> - <img src="/images/IoC와 DI1.png" width="400" height="400"/>
> - <img src="/images/IoC와 DI2.png" width="400" height="400"/>
> - IoC란? 제어의 역전을 의미함
> - 제어의 흐름을 전통적인 방식과 다르게 뒤바꾸는 것을 말함
> - DI란? 의존성 주입을 의미함
> - IoC과정에서 많이 사용하는 기법임 

<br>

#### 👉 @Autowired 활용

> - <img src="/images/@Autowired%20활용.png" width="400" height="400"/>
> - iv, setter, 참조형 매개변수를 가진 생성자, 메서드에 적용 가능함
> - 생성자에 @Autowired를 사용하는 것을 권장함
> - 스프링 컨테이너에서 '타입'으로 빈을 검색해서 참조 변수에 자동 주입(DI)함
> - 검색된 빈이 n개라면, 그중에 참조변수와 이름이 일치하는 것을 주입
> - 주입 대상이 변수일 때, 검색된 빈이 1개가 아니면 예외발생함
> - 주입 대상이 배열일 때, 검색된 빈이 n개라도 예외 발생안함


<br>

#### 👉 @Resource 활용

> - 스프링 컨테이너에서 '이름'으로 빈을 검색해서 참조 변수에 자동 주입(DI)함
> - 일치하는 이름의 빈이 없으면 예외발생함

<br>

#### 👉 @Component 활용

> - <component-scan>로 @Component가 클래스를 자동 검색해서 빈으로 등록해줌

<br>

#### 👉 @Value와 @PropertySource

> - <img src="/images/@Value와@PropertySource.png" width="400" height="400"/>


<br>

#### 👉 스프링 애너테이션 vs 표준 애너테이션 

> - <img src="/images/애너테이션비교.png" width="400" height="400"/>


<br>

#### 👉 Transaction, Commit, Rollback

> - Transaction이란? 더이상 나눌 수 없는 작업 단위. 여러 작업을 하나의 작업으로 묶음
> - 계좌 이체의 경우, 출금과 입금이 하나의 tx로 묶어야함

<br>

#### 👉 Transaction의 속성 - ACID

> - <img src="/images/트랜잭션.png" width="400" height="400"/>
> - 원자성(Atomicity) 
>   - 나눌 수 없는 하나의 작업으로 다뤄져야함
> 
> - 일관성(Consistency)
>   - tx 수행 전과 후가 일관된 상태를 유지해야함
> 
> - 고립성(Isolation)
>   - 각 tx는 독립적으로 수행되야함
> 
> - 영속성(Durability)
>   - 성공한 tx의 결과는 유지되야함

<br>

#### 👉 커밋과 롤백

> - <img src="/images/커밋과롤백.png" width="400" height="400"/>
> - <img src="/images/자동커밋과수동커밋.png" width="400" height="400"/>
> - 커밋 : 작업 내용을 DB에 영구적으로 전달하는 것
> - 롤백 : 최근 변경사항을 취소(마지막 커밋으로 복귀 )

<br>

#### 👉 TX의 isolation level

> - <img src="/images/TX의isolationlevel.png" width="400" height="400"/>
> - 각 tx를 고립시키는 정도를 4가지 레벨로 구성함

<br>

#### 👉 READ UNCOMMITTED

> - <img src="/images/READUNCOMMITTED.png" width="400" height="400"/>
> - 커밋되지 않은 데이터를 읽기 가능
> - isolation level에서 가장 낮은 레벨(dirty read)

<br>

#### 👉 READ COMMITTED

> - <img src="/images/READCOMMITTED.png" width="400" height="400"/>
> - 커밋된 데이터만 읽기 가능
> - pahntom read라고도 함

<br>

#### 👉 REPEATABLE READ

> - <img src="/images/REPEATABLEREAD.png" width="400" height="400"/>
> - tx 시작 후 다른 tx의 변경을 무시됨

<br>

#### 👉 SERIALIZABLE 

> - <img src="/images/SERIALIZABLE.png" width="400" height="400"/>
> - 한번에 하나의 tx만 독립적으로 수행함

<br>

#### 👉 AOP의 개념과 용어 1

```java
public class AopMain {
    public static void main(String[] args) throws Exception {
        MyAdvice myAdvice = new MyAdvice();

        Class myClass = Class.forName("com.fastcampus.ch3.aop.MyClass");
        Object obj = myClass.newInstance();

        for(Method m : myClass.getDeclaredMethods()) {
            myAdvice.invoke(m, obj, null);
        }
    }
}

class MyAdvice {
    Pattern p = Pattern.compile("a.*");

    boolean matches(Method m){
        Matcher matcher = p.matcher(m.getName());
        return matcher.matches();
    }

    void invoke(Method m, Object obj, Object... args) throws Exception {
        if(m.getAnnotation(Transactional.class)!=null)
            System.out.println("[before]{");

        m.invoke(obj, args); // aaa(), aaa2(), bbb() 호출가능

        if(m.getAnnotation(Transactional.class)!=null)
            System.out.println("}[after]");
    }
}

class MyClass {
    @Transactional
    void aaa() {
        System.out.println("aaa() is called.");
    }
    void aaa2() {
        System.out.println("aaa2() is called.");
    }
    void bbb() {
        System.out.println("bbb() is called.");
    }
}
```

> - <img src="/images/AOP개념과용어1.png" width="400" height="400"/>
> - 중복 코드를 효율적으로 다루는 기술
> - 부가기능이 되는 로직을 담당하는 클래스를 정의해서 사용함. 이 부분이 핵심임. 애플리케이션 전체에 산재해있는 부가기능을 모듈화해서 사용하는 것
> - 핵심기능과 부가기능을 분리시킴. 이 과정에서 reflection API를 사용함
> - 부가기능을 적용할 대상의 패턴을 확인하거나 애노테이션이 적용됬는지를 확인해서 AOP를 적용해줄 수 있음
> - AOP를 통해 코드를 추가하는 부분은 위와 아래도 구성됨(물론, 프록시를 이용한 AOP에 한해서만 설명)
>   - AROUND = BEFORE + AFTER
>     - BEFORE : 위
>     - AFTER : 아래 

<br>

#### 👉 AOP의 개념과 용어 2 

> - <img src="/images/AOP개념과용어2.png" width="400" height="400"/>
> - <img src="/images/AOP개념과용어3.png" width="400" height="400"/>
> - <img src="/images/AOP관련용어.png" width="400" height="400"/>
> - 관점 지향 프로그래밍이라고함
> - 런타임 시에 부가기능(Advice)를 동적으로 추가해주는 기술을 말함
> - 간단하게, 메서드의 시작 또는 끝에 자동으로 코드 추가해줌 

<br>

#### 👉 Advice의 종류 

> - <img src="/images/advice종류.png" width="400" height="400"/>
> - Advice의 설정은 xml과 애노테이션 두 가지 방법으로 가능 

<br>

#### 👉 pointcut expression 
```java

```


> - <img src="/images/pointcut expression1.png" width="400" height="400"/>
> - <img src="/images/pointcut expression2.png" width="400" height="400"/>


<br>

#### 👉 @Transactional의 속성 

> - <img src="/images/@Transactional의 속성1.png" width="400" height="400"/>
> - <img src="/images/@Transactional의 속성2.png" width="400" height="400"/>
> - <img src="/images/@Transactional의 속성3.png" width="400" height="400"/>
> - <img src="/images/@Transactional의 속성4.png" width="400" height="400"/>
> - @Transactional은 기본적으로 Runtime Exception, error만 롤백처리함
> - 다른 예외도 적용 시키려면 rollbackFor 속성을 통해 지정해줄 수 있음 




## 📌 04. MyBatis로 게시판 구현

#### 🧑🏻‍🏫 주요 내용 작성

<img src="/images/아직.jpeg" width="800" height="500"/>

## 📌 05. Spring MVC로 웹사이트 만들어보기 

#### 🧑🏻‍🏫 주요 내용 작성

<img src="/images/스프링오브젝트.jpeg" width="800" height="500"/>