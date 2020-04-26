# 알고리즘
[백준 11726번: 2xn 타일링](https://www.acmicpc.net/problem/11726)
```java
package dp;

import java.io.*;

public class Main_11726_2xnTile {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		int [] dp = new int [1001];
		dp[0] = 0; dp[1] = 1; dp[2] = 2;
		for (int i = 3; i <= 1000; i++) {
			dp[i] = (dp[i-1] + dp[i-2])%10007;
		}
		System.out.println(dp[N]);
	}//main

}//class
```
- DP 문제. 점화식을 이용해 구현.
