# 알고리즘
[백준 11057번: 오르막 수](https://www.acmicpc.net/problem/11057)
```java
package dp_;

import java.io.*;

public class Main_11057_IncreaseNum {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		int [][] dp = new int [N+1][10];
		int result = 0;
		
		for (int i = 0; i < 10; i++) dp[1][i] = 1;
		for (int i = 2; i <= N; i++) {
			for (int j = 0; j < 10; j++) {
				for (int k = 0; k <= j; k++) {
					dp[i][j] += dp[i-1][k];
					dp[i][j] %= 10007;
				}
			}
		}
		for (int i = 0; i < 10; i++) {
			result += dp[N][i];
			result %= 10007;
		}
		System.out.println(result);
	}//main
}//class
```
- DP문제.
