# 알고리즘
[백준 1904번:01타일](https://www.acmicpc.net/problem/1904)

```java
public class Main_1904_Tile {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		long [] dp = new long [1000001];
		dp[1] = 1;
		dp[2] = 2;

		for (int i = 3; i <= N; i++) {
			dp[i] = (dp[i-1] + dp[i-2]) % 15746;
		}
		System.out.println(dp[N]);
		
	}//main

}//class
```
- DP 문제 - 점화식을 이용하여 구현
- 피보나치 수열이었다.
