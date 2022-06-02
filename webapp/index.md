webapp/index.jsp

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%
String root = request.getContextPath();
%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
	<h1>MVC 패턴 연습</h1>
	<h3>더하기</h3>
	<form action="<%=root%>/add" method="post">
	<input type="text" name="n1" />
	<input type="text" name="n2" />
	<input type="submit" value="더하기" />
	</form>
	<h3>빼기</h3>
	<form action="<%=root%>/minus" method="post">
	<input type="text" name="n1" />
	<input type="text" name="n2" />
	<input type="submit" value="빼기" /></form>
</body>
</html>
```

