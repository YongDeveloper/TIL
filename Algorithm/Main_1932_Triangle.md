# 알고리즘
[백준 1932번: 정수 삼각형](https://www.acmicpc.net/problem/1932)

```java
public class Main_1932_Triangle {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int [][] dp = new int [N][N];
		int max = 0;
		
		st = new StringTokenizer(br.readLine());
		dp[0][0] = Integer.parseInt(st.nextToken());
		
		for (int i = 1; i < N; i++) {
			st = new StringTokenizer(br.readLine());
			
			for (int j = 0; j <= i; j++) {
				dp[i][j] = Integer.parseInt(st.nextToken());
				
				if(j==0) 	dp[i][j] += dp[i-1][j];
				else if(j==i) 	dp[i][j] += dp[i-1][j-1];
				else 	dp[i][j] += Math.max(dp[i-1][j-1], dp[i-1][j]);
				
				if(max < dp[i][j]) max = dp[i][j];
			}
		}
		System.out.println(max);
	}//main
}//class
```
- DP로 구현
- 가장자리에 있을 경우와 아닐때를 구분하여 구현
- 반복문을 이용하면서 max를 갱신하는 방법으로 구현
