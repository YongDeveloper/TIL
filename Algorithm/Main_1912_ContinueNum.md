# 알고리즘
[백준 1912번:연속합](https://www.acmicpc.net/problem/1912)
```java
package math_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_1912_ContinueNum {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		int [] arr = new int [N];
		int [] dp = new int [N];
		
		StringTokenizer st = new StringTokenizer(br.readLine());
		for (int i = 0; i < N; i++) {
			arr[i] = Integer.parseInt(st.nextToken());
		}
		dp[0] = arr[0];
		int max = arr[0];
		
		for (int i = 1; i < dp.length; i++) {
			dp[i] = Math.max(dp[i-1]+arr[i], arr[i]);
			max = Math.max(max, dp[i]);
		}
		System.out.println(max);
		
	}//main

}//class

```
- 수학 문제였지만 알고보니 DP 문제
