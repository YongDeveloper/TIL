# 알고리즘
[백준 11047번:동전 0](https://www.acmicpc.net/problem/11047)
```java
public class Main_11047_Coin0 {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int K = Integer.parseInt(st.nextToken());
		int [] arr = new int [N+1];
		int cnt = 0;
		for (int i = 1; i <= N; i++) {
			arr[i] = Integer.parseInt(br.readLine());
		}
		while(K>0) {
			if(K >= arr[N]) {
				cnt++;	K -= arr[N];
			}else if(K < arr[N]) N--;
		}
		
		System.out.println(cnt);
	}//main
	
}//class
```
- 그리디 문제 : 전체 금액에서 큰 금액의 종류부터 감소하는 방향으로 구현.
