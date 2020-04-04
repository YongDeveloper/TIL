# 알고리즘
[백준 9461번: 파도](https://www.acmicpc.net/problem/9461)

```java
public class Main_9461_Wave {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int TC = Integer.parseInt(br.readLine());
		for (int tc = 1; tc <= TC; tc++) {
			int N = Integer.parseInt(br.readLine());
			
			long [] dp = new long [101];
			dp[0] = 0; 
			dp[1] = 1;
			dp[2] = 1;
			dp[3] = 1;
			dp[4] = 2;
			
			for (int i = 5; i < dp.length; i++) {
				dp[i] = dp[i-1] + dp[i-5];
			}
			System.out.println(dp[N]);
      
		}//tc
    
	}//main
  
}//class
```
- DP 문제 점화식을 세워서 구현하였다.
- 4번째 배열까지 초기값을 넣어 주었다.
