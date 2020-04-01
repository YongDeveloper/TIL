# 알고리즘
[백준 7568번 : 덩치](https://www.acmicpc.net/problem/7568)

```java
public class Main_7568_Bulk {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int [] arr = new int [N];
		int [] brr = new int [N];
		int [] rank = new int [N];
		
		for (int i = 0; i < N; i++) {
			st = new StringTokenizer(br.readLine());
			arr[i] = Integer.parseInt(st.nextToken());
			brr[i] = Integer.parseInt(st.nextToken());
		}
		
		for (int i = 0; i < N; i++) {
			for (int j = 0; j < N; j++) {
				if(i==j) continue;
				if(arr[i]<arr[j] && brr[i]<brr[j]) rank[i]++;
			}
		}
		
		for (int i = 0; i < rank.length; i++) {
			System.out.print(rank[i]+1+" ");
		}
		
	}//main

}//class

```

- 이중 for문을 이용하여 완전탐색 방법으로 구현하였다.
