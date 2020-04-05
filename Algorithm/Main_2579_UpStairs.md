# 알고리즘
[백준 2579번:계단 오르기](https://www.acmicpc.net/problem/2579)
```java
public class Main_2579_UpStairs {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		int [] dp = new int [N+1];
		int [] arr = new int [N+1];
		
		for (int i = 1; i <= N; i++) {
			arr[i] = Integer.parseInt(br.readLine());
		}
		dp[1] = arr[1];
		if(N>=2) dp[2] = dp[1] + arr[2];
		
		for (int i = 3; i <= N; i++) {
			dp[i] = Math.max(dp[i-2]+arr[i], dp[i-3]+arr[i-1]+arr[i]);
		}
		
		System.out.println(dp[N]);
		
	}//main

}//class
```

- DP를 이용해 구현
- 마지막 N번째 도착지점을 밟아야 하므로 N-1와 N-3를 밟을경우,
- 마지막 N번째 도착지점을 밟고 N-2를 밝을 경우를 나누어서 비교한다.
