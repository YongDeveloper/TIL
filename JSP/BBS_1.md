# JSP 프로젝트 - BBS 게시판 만들기
### 1. 로그인페이지 구성
![image](https://user-images.githubusercontent.com/62415893/81380768-6109ec80-9146-11ea-84ab-f16dcc53e482.png)
#### login.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width" initial-scale="1.0">
<link rel="stylesheet" href="css/bootstrap.css">
<title>JSP WEB PROJECT</title>
</head>
<body>
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
				<li><a href="bbs.jsp"> 게시판 </a>
			</ul>
			<ul class="nav navbar-nav navbar-right">
				<li class="dropdown">
					<a href="#" class="dropdown-toggle"
						data-toggle="dropdown" role="button" aria-haspopup="true"
						aria-expanded="false">접속하기 <span class="caret"></span></a>
						
					<ul class="dropdown-menu">
						<li class="active"><a href="login.jsp">로그인</a>
						<li><a href="join.jsp">회원가입</a>
					</ul>
				</li>
			</ul>
		</div>
	</nav>
	<div class="container">
		<div class="col-lg-4"></div>
		<div class="col-lg-4">
			<div class="jumbotron" style="padding-top:20px">
				<form method="post" action="loginAction.jsp">
					<h3 style="text-align:center">로그인 화면</h3>
					<div class="form-group">
						<input type="text" class="form-control" placeholder="아이디"
							name="userID" maxlength="20">
					</div>
					<div class="form-group">
						<input type="text" class="form-control" placeholder="비밀번호"
							name="userPW" maxlength="20">
					</div>
					<input type="submit" class="btn btn-primary form-control" value="로그인">
				</form>
			</div>
		</div>
		<div class="col-lg-4"></div>
	</div>
	<script src="https://code.jquery.com/jquery-3.1.1.min.js"> </script>
	<script src="js/bootstrap.js"></script>
</body>
</html>
```
