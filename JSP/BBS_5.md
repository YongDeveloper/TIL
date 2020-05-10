# JSP 프로젝트 - BBS 게시판 만들기
### 5. 접속한 회원 세션 관리하기 + 게시판 만들기
![image](https://user-images.githubusercontent.com/62415893/81495142-1674a580-92e9-11ea-847f-6cafd525a6d8.png)
![image](https://user-images.githubusercontent.com/62415893/81495332-8a637d80-92ea-11ea-81ad-6ad57cfb9545.png)
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ page import="java.io.*" %>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width" initial-scale="1.0">
<link rel="stylesheet" href="css/bootstrap.css">
<title>JSP WEB PROJECT</title>
</head>
<body>
	<%
		String userID = null;
		if(session.getAttribute("userID") != null){
			userID = (String) session.getAttribute("userID");
		}
	%>

	<nav class="navbar navbar-default">
		<div class="navbar header">
			<button type="button" class="navbar-toggle collapsed"
				data-toggle="collapse" data-target="#bs-example-navbar-collapsed-1"	
				aria-expanded="false">
				<span class="icon-bar"></span>
				<span class="icon-bar"></span>
				<span class="icon-bar"></span>
			</button>	
			<a class ="navbar-brand" href="main.jsp"> JSP 게시판 웹 사이트</a>
		</div>
		<div class="collapse navbar-collapse" id="bs-example-navbar-collapsed-1">
			<ul class="nav navbar-nav">
				<li><a href="main.jsp"> 메인 </a>
				<li class="active"><a href="bbs.jsp"> 게시판 </a>
			</ul>
			
			<%
				if(userID == null){
			%>
			<ul class="nav navbar-nav navbar-right">
				<li class="dropdown">
					<a href="#" class="dropdown-toggle"
						data-toggle="dropdown" role="button" aria-haspopup="true"
						aria-expanded="false">접속하기 <span class="caret"></span></a>
						
					<ul class="dropdown-menu">
						<li><a href="login.jsp">로그인</a>
						<li class="active"><a href="join.jsp">회원가입</a>
					</ul>
				</li>
			</ul>
			<%
				}else{
			%>
			<ul class="nav navbar-nav navbar-right">
				<li class="dropdown">
					<a href="#" class="dropdown-toggle"
						data-toggle="dropdown" role="button" aria-haspopup="true"
						aria-expanded="false">회원 관리 <span class="caret"></span></a>
					<ul class="dropdown-menu">
						<li><a href="logoutAction.jsp">로그아웃</a>
					</ul>
				</li>
			</ul>
			<%
				}
			%>
		</div>
	</nav>
	<div class="container">
		<div class="row">
			<table class="table table-striped" style="text-aling:center; border: 1px solid #dddddd">
				<thead>
					<tr>
						<th style="background-color: #eeeeee; text-align:center;"> 번호</th>
						<th style="background-color: #eeeeee; text-align:center;"> 제목</th>
						<th style="background-color: #eeeeee; text-align:center;"> 작성자</th>
						<th style="background-color: #eeeeee; text-align:center;"> 작성일</th>
					</tr>
				</thead>
				<tbody>
					<tr>
						<td style="text-align:center">1</td>
						<td style="text-align:center">안녕하세요</td>
						<td style="text-align:center">홍길동</td>
						<td style="text-align:center">2020-05-08</td>
					</tr>
				</tbody>
			</table>
			<a href="write.jsp" class="btn btn-primary pull-right">글쓰기</a>
		</div>
	</div>
	<script src="https://code.jquery.com/jquery-3.1.1.min.js"> </script>
	<script src="js/bootstrap.js"></script>
</body>
</html>
```
