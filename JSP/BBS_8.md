# JSP 프로젝트 - BBS 게시판 만들기
### 8. 게시판 글 수정, 삭제, Main 제작 
![image](https://user-images.githubusercontent.com/62415893/81563505-4c8d5480-93d1-11ea-8038-b52794942850.png)
![image](https://user-images.githubusercontent.com/62415893/81563552-5a42da00-93d1-11ea-940e-ebb2cef71ef9.png)
![image](https://user-images.githubusercontent.com/62415893/81563631-79416c00-93d1-11ea-9724-0010d576be05.png)
![image](https://user-images.githubusercontent.com/62415893/81563660-82323d80-93d1-11ea-8b42-802436a8f9c3.png)
![image](https://user-images.githubusercontent.com/62415893/81563697-95450d80-93d1-11ea-854b-9f2cb1dbb050.png)
#### BbsDAO.java
```java
package bbs;

import java.sql.*;
import java.util.*;

public class BbsDAO {
	private Connection con;
	private ResultSet rs;
	
	public BbsDAO() {
		try {
			String dbURL = "jdbc:mysql://localhost:3306/bbs?serverTimezone=UTC";
			String dbID = "root";
			String dbPW = "1234";
			Class.forName("com.mysql.jdbc.Driver");
			con = DriverManager.getConnection(dbURL, dbID, dbPW);
		} catch (Exception e) {
			e.printStackTrace();
		}
	}//dao
	
	public String getDate() {
		String sql = "SELECT NOW()";
		try {
			PreparedStatement ps = con.prepareStatement(sql);
			rs = ps.executeQuery();
			if(rs.next()) {
				return rs.getString(1);
			}
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return ""; // 데이터베이스 오류
	}
	
	public int getNext() {
		String sql = "select bbsID from bbs order by bbsID desc";
		try {
			PreparedStatement ps = con.prepareStatement(sql);
			rs = ps.executeQuery();
			if(rs.next()) {
				return rs.getInt(1) + 1;
			}
			return 1; // 첫번째 게시물인 경우
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return -1; // 데이터베이스 오류
	}
	
	public int write(String bbsTitle, String userID, String bbsContent) {
		String sql = "INSERT INTO bbs values (?,?,?,?,?,?)";
		try {
			PreparedStatement ps = con.prepareStatement(sql);
			ps.setInt(1, getNext());
			ps.setString(2, bbsTitle);
			ps.setString(3, userID);
			ps.setString(4, getDate());
			ps.setString(5, bbsContent);
			ps.setInt(6, 1);
			return ps.executeUpdate();
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return -1; // 데이터베이스 오류
	}
	public ArrayList<BBS> getList(int pageNum){
		ArrayList<BBS> list = new ArrayList<BBS>();
		String sql ="select * from bbs where bbsID < ? and bbsAvailable = 1 order by bbsID desc limit 10";
		try {
			PreparedStatement ps = con.prepareStatement(sql);
			ps.setInt(1, getNext() - (pageNum -1) * 10 );
			rs = ps.executeQuery();
			while(rs.next()) {
				BBS bbs = new BBS();
				bbs.setBbsID(rs.getInt(1));
				bbs.setBbsTitle(rs.getString(2));
				bbs.setUserID(rs.getString(3));
				bbs.setBbsDate(rs.getString(4));
				bbs.setBbsContent(rs.getString(5));
				bbs.setBbsAvailabe(rs.getInt(6));
				list.add(bbs);
			}
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return list;
	}//list
	
	public boolean nextPage(int pageNum){
		String sql ="select * from bbs where bbsID < ? and bbsAvailable = 1";
		try {
			PreparedStatement ps = con.prepareStatement(sql);
			ps.setInt(1, getNext() - (pageNum -1) * 10 );
			rs = ps.executeQuery();
			if(rs.next()) {
				return true;
			}
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return false;
	}//nextpage
	public BBS getBbs(int bbsID) {
		String sql ="select * from bbs where bbsID = ?";
		try {
			PreparedStatement ps = con.prepareStatement(sql);
			ps.setInt(1, bbsID);
			rs = ps.executeQuery();
			if(rs.next()) {
				BBS bbs = new BBS();
				bbs.setBbsID(rs.getInt(1));
				bbs.setBbsTitle(rs.getString(2));
				bbs.setUserID(rs.getString(3));
				bbs.setBbsDate(rs.getString(4));
				bbs.setBbsContent(rs.getString(5));
				bbs.setBbsAvailabe(rs.getInt(6));
				return bbs;
			}
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return null;
	}//getbbs
	public int update(int bbsID, String bbsTitle, String bbsContent) {
		String sql = "update bbs set bbsTitle=?, bbsContent=? where bbsID=?";
		try {
			PreparedStatement ps = con.prepareStatement(sql);
			ps.setString(1, bbsTitle);
			ps.setString(2, bbsContent);
			ps.setInt(3, bbsID);
			return ps.executeUpdate();
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return -1; // 데이터베이스 오류
	}
	public int delete(int bbsID) {
		String sql = "update bbs set bbsAvailable = 0 where bbsID=?";
		try {
			PreparedStatement ps = con.prepareStatement(sql);
			ps.setInt(1, bbsID);
			return ps.executeUpdate();
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return -1; // 데이터베이스 오류
	}
}//class
```

#### view.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ page import="java.io.*" %>
<%@ page import="bbs.BBS" %>
<%@ page import="bbs.BbsDAO" %>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width" initial-scale="1.0">
<link rel="stylesheet" href="css/bootstrap.css">
<link rel="stylesheet" href="css/custom.css">
<title>JSP WEB PROJECT</title>
</head>
<body>
	<%
		String userID = null;
		if(session.getAttribute("userID") != null){
			userID = (String) session.getAttribute("userID");
		}
		int bbsID = 0;
		if(request.getParameter("bbsID")!=null){
			bbsID = Integer.parseInt(request.getParameter("bbsID"));
		}
		if(bbsID == 0){
			PrintWriter script = response.getWriter();
			script.println("<script>");
			script.println("alert('유효하지 않은 글입니다')");
			script.println("location.href='bbs.jsp'");
			script.println("</script>");
		}
		BBS bbs = new BbsDAO().getBbs(bbsID);
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
			<a class ="navbar-brand" href="main.jsp"> 용구니의 JSP 게시판 웹 사이트</a>
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
						<th colspan="3" style="background-color: #eeeeee; text-align:center;"> 게시판 글 보기</th>
					</tr>
				</thead>
				<tbody>
					<tr>
						<td style="width:20%"> 글제목 </td>
						<td colspan="2"><%=bbs.getBbsTitle().replaceAll(" ", "&nbsp;").replaceAll("<", "&lt").replaceAll(">", "&gt").replaceAll("\n", "<br>") %></td>
					</tr>
					<tr>
						<td> 작성자 </td>
						<td colspan="2"><%=bbs.getBbsID() %></td>
					</tr>
					<tr>
						<td> 작성 일자 </td>
						<td colspan="2"><%=bbs.getBbsDate() %></td>
					</tr>
					<tr>
						<td> 내용 </td>
						<td colspan="2" style="min-height:200px; text-align:left"><%=bbs.getBbsContent().replaceAll(" ", "&nbsp;").replaceAll("<", "&lt").replaceAll(">", "&gt").replaceAll("\n", "<br>") %></td>
					</tr>
				</tbody>
			</table>
			<a href="bbs.jsp" class="btn btn-primary">목록</a>
			<%
				if(userID != null && userID.equals(bbs.getUserID())){
			%>
				<a href ="update.jsp?bbsID=<%=bbs.getBbsID() %>" class="btn btn-primary">수정</a>
				<a onclick="return confirm('정말로 삭제하시겠습니까?')" href ="deleteAction.jsp?bbsID=<%=bbs.getBbsID() %>" class="btn btn-primary">삭제</a>
			<%
				}
			%>
		</div>
	</div>
	<script src="https://code.jquery.com/jquery-3.1.1.min.js"> </script>
	<script src="js/bootstrap.js"></script>
</body>
</html>
```
### update.jsp
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ page import="java.io.*" %>
<%@ page import="bbs.BBS" %>
<%@ page import="bbs.BbsDAO" %>
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
		if(userID ==null){
			PrintWriter script = response.getWriter();
			script.println("<script>");
			script.println("alert('로그인을 해주세요.')");
			script.println("location.href='login.jsp'");
			script.println("</script>");
		}
		int bbsID = 0;
		if(request.getParameter("bbsID")!=null){
			bbsID = Integer.parseInt(request.getParameter("bbsID"));
		}
		if(bbsID == 0){
			PrintWriter script = response.getWriter();
			script.println("<script>");
			script.println("alert('유효하지 않은 글입니다')");
			script.println("location.href='bbs.jsp'");
			script.println("</script>");
		}
		
		BBS bbs = new BbsDAO().getBbs(bbsID);
		if(!userID.equals(bbs.getUserID())) {
			PrintWriter script = response.getWriter();
			script.println("<script>");
			script.println("alert('권한이 없습니다.')");
			script.println("location.href='bbs.jsp'");
			script.println("</script>");
			
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
			<a class ="navbar-brand" href="main.jsp"> 용구니의 JSP 게시판 웹 사이트</a>
		</div>
		<div class="collapse navbar-collapse" id="bs-example-navbar-collapsed-1">
			<ul class="nav navbar-nav">
				<li><a href="main.jsp"> 메인 </a>
				<li class="active"><a href="bbs.jsp"> 게시판 </a>
			</ul>
			
		</div>
	</nav>
	<div class="container">
		<div class="row">
			<form method="post" action="updateAction.jsp?bbsID=<%=bbsID%>">
				<table class="table table-striped" style="text-aling:center; border: 1px solid #dddddd">
					<thead>
						<tr>
							<th colspan="2" style="background-color: #eeeeee; text-align:center;"> 게시판 글 수정 양식</th>
						</tr>
					</thead>
					<tbody>
						<tr>
							<td><input type="text" class="form-control" placeholder="글 제목" name="bbsTitle" maxlength="50" value="<%= bbs.getBbsTitle()%>"></td>
						</tr>
						<tr>
							<td><textarea class="form-control" placeholder="글 내용" name="bbsContent" maxlength="2048" style="height:350px"><%= bbs.getBbsContent() %>"</textarea></td>
						</tr>
					</tbody>
				</table>
				<input type="submit" class="btn btn-primary pull-right" value="수정">
			</form>
		</div>
	</div>
	<script src="https://code.jquery.com/jquery-3.1.1.min.js"> </script>
	<script src="js/bootstrap.js"></script>
</body>
</html>
```
