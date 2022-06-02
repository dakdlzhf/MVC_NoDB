src/frontController/FrontController.java

```java
	package frontController;

import java.io.FileInputStream;
import java.io.IOException;
import java.util.Iterator;
import java.util.Map;
import java.util.Properties;

import handlerClass.InterfaceHandler;
import handlerClass.NullHandler;
import jakarta.servlet.RequestDispatcher;
import jakarta.servlet.ServletException;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;

public class FrontController extends HttpServlet {

	private Map commandHandlerMap = new java.util.HashMap(); 

	@Override
	public void init() throws ServletException {
		String contextConfigFile = this.getInitParameter("handleProperties");
		System.out.println("contextConfigFile : " + contextConfigFile);
		Properties properties = new Properties();
		FileInputStream fis = null;

		
		try {
			fis = new FileInputStream(contextConfigFile);
			properties.load(fis);
		} catch (IOException e) {
			e.printStackTrace();
		} finally {
			if (fis != null) {
				try {
					fis.close();
				} catch (IOException e) {
					e.printStackTrace();
				}
			}
		}

		Iterator keyIter = properties.keySet().iterator();
		while (keyIter.hasNext()) {
			String command = (String) keyIter.next();
			System.out.println("command : " + command);
			String handlerClassName = properties.getProperty(command).trim();
			System.out.println("handlerClassName : " + handlerClassName);
			try {
				Class handlerClass = Class.forName(handlerClassName);
				Object handlerInstance = handlerClass.newInstance();
				commandHandlerMap.put(command, handlerInstance);
			} catch (ClassNotFoundException e) {
				e.printStackTrace();
			} catch (InstantiationException e) {
				e.printStackTrace();
			} catch (IllegalAccessException e) {
				e.printStackTrace();
			}
		}
	}

	@Override
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		System.out.println("doPost 실행");
		process(request,response);
	}

	@Override
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		System.out.println("doGet 실행");
		process(request,response);
	}
	
	private void process(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException{
		String command = request.getRequestURI();
		System.out.println("RequestURI   : " + request.getRequestURI()); 
		if(command.indexOf(request.getContextPath()) == 0) {
			command = command.substring(request.getContextPath().length());
			System.out.println("command    : " + command); 
		}
		InterfaceHandler handler = (InterfaceHandler)commandHandlerMap.get(command);
		if(handler == null) {
			handler = new NullHandler();
		}
		
		String viewPage = null;
		
		try {
			viewPage = handler.execute(request, response);
			
		} catch (Throwable e) {
			throw new ServletException(e);
		}
		RequestDispatcher dispatcher =
				request.getRequestDispatcher(viewPage);
		dispatcher.forward(request, response);
	}
	

	@Override
	public void destroy() {
		System.out.println("Servlet 소멸 : destroy ");
	}

}

```

