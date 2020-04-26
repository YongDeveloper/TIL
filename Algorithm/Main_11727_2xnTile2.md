# 알고리즘
[백준 11727번: 2xn 타일링2](https://www.acmicpc.net/problem/11727)

```java
package dp;

import java.io.*;

public class Main_11727_2xnTile2 {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		int [] dp = new int [1001];
		dp[0] = 0; dp[1] = 1;
		for (int i = 2; i <= 1000; i++) {
			if(i%2==0) dp[i] = (dp[i-1]*2 + 1)% 10007;
			else if(i%2==1) dp[i] = (dp[i-1]*2 - 1)% 10007;
		}
		System.out.println(dp[N]);
	}//main

}//class

```
- DP 문제. 점화식을 구해 문제 해결.
