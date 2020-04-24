# 알고리즘
[백준 9095번:1,2,3 더하기](https://www.acmicpc.net/problem/9095)
```java
package samsung_;

import java.io.*;

public class Main_9095_123Plus {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int [] dp = new int [11];
		dp[0] = 1; dp[1] = 1; dp[2] = 2;
		for (int i = 3; i < dp.length; i++) {
			dp[i] = dp[i-1] + dp[i-2] + dp[i-3];
		}
		int TC = Integer.parseInt(br.readLine());
		for (int tc = 1; tc <= TC; tc++) {
			int N = Integer.parseInt(br.readLine());
			System.out.println(dp[N]);
		}//tc
		
	}//main

}//class

```
- DP 문제. 점화식을 이용하여 구현.
