src/handlerClass/NullHandler.java

```java
	package handlerClass;

import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

public class NullHandler implements InterfaceHandler {

	@Override
	public String execute(HttpServletRequest request, HttpServletResponse response) throws Throwable {
		
		return "/view/nullPage.jsp";
	}

}

```

