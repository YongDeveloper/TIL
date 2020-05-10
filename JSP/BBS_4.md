# JSP 프로젝트 - BBS 게시판 만들기
### 4. 회원가입 기능 구현하기

![1](https://user-images.githubusercontent.com/62415893/81494816-96e5d700-92e6-11ea-816e-cdac6a05fac1.jpg)
![2](https://user-images.githubusercontent.com/62415893/81494817-98170400-92e6-11ea-8da4-314155a9f757.jpg)
#### joinAction.jsp

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ page import="user.UserDAO" %>
<%@ page import="java.io.*" %>
<% request.setCharacterEncoding("UTF-8"); %>
<jsp:useBean id="user" class="user.User" scope="page" />
<jsp:setProperty name="user" property="userID" />
<jsp:setProperty name="user" property="userPW" />
<jsp:setProperty name="user" property="userName" />
<jsp:setProperty name="user" property="userGender" />
<jsp:setProperty name="user" property="userEmail" />
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>JSP WEB PROJECT</title>
</head>
<body>
	<%
		if(user.getUserID() == null || 	user.getUserPW() == null || user.getUserName() == null || 
				user.getUserGender() == null || user.getUserEmail() == null ) {
			PrintWriter script = response.getWriter();
			script.println("<script>");
			script.println("alert('입력사항을 모두 입력해주세요.')");
			script.println("history.back()");
			script.println("</script>");
		}else{
			UserDAO dao = new UserDAO();
			PrintWriter script = response.getWriter();
			int result = dao.join(user);
			if(result == -1){
				script.println("<script>");
				script.println("alert('이미 존재하는 아이디 입니다.')");
				script.println("history.back()");
				script.println("</script>");
			}else{
				script.println("<script>");
				script.println("location.href='main.jsp'");
				script.println("</script>");
			}
		}
	%>
</body>
</html>
```
