webapp/WEB-INF/lib/web.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="https://jakarta.ee/xml/ns/jakartaee" xmlns:web="http://xmlns.jcp.org/xml/ns/javaee" xsi:schemaLocation="https://jakarta.ee/xml/ns/jakartaee https://jakarta.ee/xml/ns/jakartaee/web-app_5_0.xsd" id="WebApp_ID" version="5.0">
  <display-name>mvctest0</display-name>
  
<servlet>
	<servlet-name>FrontController</servlet-name>
	<servlet-class>frontController.FrontController</servlet-class>
	
	<init-param>
		<param-name>handleProperties</param-name>
		<param-value>C:/aistudy/web/workspace/mvctest0/src/main/webapp/WEB-INF/config/handle.properties</param-value>
	</init-param>
</servlet>


<servlet-mapping>
	<servlet-name>FrontController</servlet-name>
	<url-pattern>/</url-pattern>
</servlet-mapping>


</web-app>
```

