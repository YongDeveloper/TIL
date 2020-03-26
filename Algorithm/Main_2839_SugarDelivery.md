# 알고리즘

[백준 2839번: 설탕 배달](https://www.acmicpc.net/problem/2839)

```java
public class Main_2839_SugarDelivery {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int num = Integer.parseInt(br.readLine());
		int cnt = 0;
		
		while(true) {
			if(num %5 == 0) num -=5;
			else if(num %3 == 0) num -=3;
			else num -=5;
			
			cnt++;
			
			if(num == 0) {
				System.out.println(cnt); 
				break;
			}
			if(num < 0 ) {
				System.out.println("-1");
				break;
			}
		}
		
	}//main

}//class


```
- 한꺼번에 나누지 않고 하나씩 빼가면서 갯수를 확인하였다.
- 더 많이 담을 수 있는 5kg 봉투부터 먼저 확인해야한다.

#### 200326


