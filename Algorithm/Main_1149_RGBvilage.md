# 알고리즘

[백준 1149번: RGB마을](https://www.acmicpc.net/problem/1149)
```java
public class Main_1149_RGBvilage {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int [][] dp = new int [N][3];
		int [][] arr = new int [N][3];
		for (int i = 0; i < N; i++) {
			st = new StringTokenizer(br.readLine());
			for (int j = 0; j < 3; j++) {
				arr[i][j] = Integer.parseInt(st.nextToken());
			}
		}
		for (int i = 0; i < 3; i++) {
			dp[0][i] = arr[0][i];
		}
		for (int i = 1; i < N; i++) {
			dp[i][0] = arr[i][0] + Math.min(dp[i-1][1], dp[i-1][2]);
			dp[i][1] = arr[i][1] + Math.min(dp[i-1][0], dp[i-1][2]);
			dp[i][2] = arr[i][2] + Math.min(dp[i-1][0], dp[i-1][1]);
		}
		int min = Math.min( Math.min(dp[N-1][0], dp[N-1][1]), dp[N-1][2]);
		System.out.println(min);
    
	}//main
}//class
```
- 실제 배열과 dp 배열을 따로 만들어서 구분하였다.
- 첫번째 배열만 DP 배열에 담고 그 다음 줄부터 최소값을 비교한다.
- 빨, 파, 초의 최소값을 이용해 최종 최소값을 구한다.
