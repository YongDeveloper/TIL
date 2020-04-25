# 알고리즘
[백준 1463번:1로 만들기](https://www.acmicpc.net/problem/1463)
```java
package dp;

import java.io.*;

public class Main_1463_MakeOne {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		int[] dp = new int [1000001];
		dp[0] = 0; 
		dp[1] = 0;
		
		for (int i = 2; i <= N; i++) {
			dp[i] = dp[i-1] + 1;
			if(i%2==0) dp[i] = Math.min(dp[i], dp[i/2] + 1);
			if(i%3==0) dp[i] = Math.min(dp[i], dp[i/3] + 1);
		}
		System.out.println(dp[N]);
		
	}//main

}//class
```
- DP 문제. 
- 점화식을 구해서 구현.
