# JAVA

### JDBC 를 이용하는 일반적인 순서

- DB 연결을 위한 Connection을 가져온다.
- SQL에 담은 Statement 또는 Preparedstatement 를 만든다.
- 만들어진 statement를 실행한다.
- 조회의 경우 SQL 의 쿼리 결과를 ResultSet으로 받아서 User에 옮겨준다.
- 작업 중에 생성된 Connection, statement, resultset 같은 리소스는 작업을 마친후 닫아준다.
- JDBC API가 만들어내는 예외를 직접 처리하거나, 메소드 밖으로 던진다.

```java
public class UserDao {

	public static void add (User user) throws ClassNotFoundException, SQLException {
		

		Class.forName("com.mysql.cj.jdbc.Driver");
		Connection conn = DriverManager.getConnection(
							"jdbc:mysql://localhost:3360/test?serverTimezone=UTC", "root", "1234");
		
		PreparedStatement ps = conn.prepareStatement(
								"insert into users(id, name, password) values(?,?,?) ");
		ps.setString(1, user.getId());
		ps.setString(2, user.getName());
		ps.setString(3, user.getPassword());
		
		ps.executeUpdate();
		ps.close();
		conn.close();
		
	}//add
	
	public static User get(String id) throws ClassNotFoundException, SQLException {
		
		Class.forName("com.mysql.cj.jdbc.Driver");
		Connection conn = DriverManager.getConnection(
							"jdbc:mysql://localhost:3360/test?serverTimezone=UTC", "root", "1234");
		PreparedStatement ps = conn.prepareStatement(
								"select * from users where id=");
		ps.setString(1, id);
		
		ResultSet rs = ps.executeQuery();
		rs.next();
		
		User user = new User();
		user.setId(rs.getString("id"));
		user.setName(rs.getString("name"));  
		user.setPassword(rs.getString("password"));
		
		rs.close();
		ps.close();
		conn.close();
		
		return user;
		
	}//get
	
}//class


```

#### 200329
