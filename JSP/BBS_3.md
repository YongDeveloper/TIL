# JSP 프로젝트 - BBS 게시판 만들기
### 3. loginAction.jsp 페이지
![image](https://user-images.githubusercontent.com/62415893/81414697-54a38500-9182-11ea-88bd-f6988f9867bf.png)

#### loginAction.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ page import="user.UserDAO" %>
<%@ page import="java.io.*" %>
<% request.setCharacterEncoding("UTF-8"); %>
<jsp:useBean id="user" class="user.User" scope="page" />
<jsp:setProperty name="user" property="userID" />
<jsp:setProperty name="user" property="userPW" />
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>JSP WEB PROJECT</title>
</head>
<body>
	<%
		UserDAO dao = new UserDAO();
		int result = dao.login(user.getUserID(), user.getUserPW());
			PrintWriter script = response.getWriter();
		if(result == 1){
			script.println("<script>");
			script.println("location.href='main.jsp'");
			script.println("</script>");
		}else if(result == 0){
			script.println("<script>");
			script.println("alert('비밀번호가 틀립니다.')");
			script.println("history.back()");
			script.println("</script>");
		}else if(result == -1){
			script.println("<script>");
			script.println("alert('존재하지 않는 아이디 입니다.')");
			script.println("history.back()");
			script.println("</script>");
		}else if(result == -2){
			script.println("<script>");
			script.println("alert('데이터베이스 오류 발생.')");
			script.println("history.back()");
			script.println("</script>");
		}
	%>
</body>
</html>
```
