# JSP 프로젝트 - BBS 게시판 만들기
### 6. 게시판 데이터베이스 구축하기(BBS javaBean)
![image](https://user-images.githubusercontent.com/62415893/81495521-c3e8b880-92eb-11ea-83a5-013c5c54a9f6.png)
```java
package bbs;

public class BBS {

	private int bbsID;
	private String bbsTitle;
	private String userID;
	private String bbsDate;
	private String bbsContent;
	private int bbsAvailabe;
	
	public int getBbsID() {
		return bbsID;
	}
	public void setBbsID(int bbsID) {
		this.bbsID = bbsID;
	}
	public String getBbsTitle() {
		return bbsTitle;
	}
	public void setBbsTitle(String bbsTitle) {
		this.bbsTitle = bbsTitle;
	}
	public String getUserID() {
		return userID;
	}
	public void setUserID(String userID) {
		this.userID = userID;
	}
	public String getBbsDate() {
		return bbsDate;
	}
	public void setBbsDate(String bbsDate) {
		this.bbsDate = bbsDate;
	}
	public String getBbsContent() {
		return bbsContent;
	}
	public void setBbsContent(String bbsContent) {
		this.bbsContent = bbsContent;
	}
	public int getBbsAvailabe() {
		return bbsAvailabe;
	}
	public void setBbsAvailabe(int bbsAvailabe) {
		this.bbsAvailabe = bbsAvailabe;
	}
}
```
