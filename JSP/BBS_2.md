# JSP 프로젝트 - BBS 게시판 만들기
### 2. UserDAO 페이지 구성

#### UserDAO.java
```jsp
package user;

import java.sql.*;

public class UserDAO {
	
	private Connection con;
	private PreparedStatement ps;
	private ResultSet rs;
	
	public UserDAO() {
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
	
	public int login(String userID, String userPW) {
		String sql = "select userPW from user where userID=?";
		try {
			ps = con.prepareStatement(sql);
			ps.setString(1, userID);
			rs = ps.executeQuery();
			
			if(rs.next()) { // 그 결과가 존재 한다면
				if(rs.getString(1).equals(userPW)) return 1; // 로그인 성공
				else return 0; // 비밀번호 불일치 
			}
			return -1; // 아이디가 없음
			
		} catch (Exception e) {
			e.printStackTrace();
		}
		return -2; // 데이터베이스 오류
	}
	
}

```
