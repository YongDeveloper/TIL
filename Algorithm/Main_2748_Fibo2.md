# 알고리즘
[백준 2748번:피보나치 수2](https://www.acmicpc.net/problem/2748)

```java
public class Main_2748_Fibo2 {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		long [] f = new long [91];
		f[0] = 0;
		f[1] = 1;
		for (int i = 2; i < f.length; i++) {
			f[i] = f[i-1]+f[i-2];
		}
		System.out.println(f[N]);
	}//main
}//class
```
- DP 문제로 구현
- 재귀로 피보나치를 이용하였는데 시간초과
- 점화식을 세워 배열에 저장하였는데 런타임에러
- n의 값이 90 이하라 int 형 대신 long 형을 이용하였다.
