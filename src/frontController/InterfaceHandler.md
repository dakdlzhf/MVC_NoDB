

```java
	package handlerClass;

import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

public interface InterfaceHandler {
	String execute(HttpServletRequest request, HttpServletResponse response) throws Throwable;
}

```

