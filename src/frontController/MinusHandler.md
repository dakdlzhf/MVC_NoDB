src/handlerClass/MinusHandler.java

```java
package handlerClass;

import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import model.MinusService;

public class MinusHandler implements InterfaceHandler {

	@Override
	public String execute(HttpServletRequest request, HttpServletResponse response) throws Throwable {
		
		int n1 = Integer.parseInt(request.getParameter("n1"));
		int n2 = Integer.parseInt(request.getParameter("n2"));
		
		MinusService min = new MinusService();
		int result = min.minus(n1, n2);
		
		request.setAttribute("result",result);
		return "/view/minus.jsp";
	}

}
	
```

