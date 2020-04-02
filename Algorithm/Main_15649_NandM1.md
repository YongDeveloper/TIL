# 알고리즘

[백준 15649번: N과 M (1)](https://www.acmicpc.net/problem/15649)

```java
public class Main_15649_NandM1 {
	public static int [] arr;
	public static boolean [] visited;
	public static StringBuilder sb = new StringBuilder();
	private static int N;
	private static int R;
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		R = Integer.parseInt(st.nextToken());
		arr = new int [N+1];
		visited = new boolean [N+1];
		Perm(0);
		System.out.println(sb);
		
	}//main
	
	public static void Perm(int cnt) {
		if(cnt==R) {
			for (int i = 0; i < R; i++) {
				sb.append(arr[i]+" ");
			}
			sb.append("\n");
		}
		for (int i = 1; i <= N; i++) {
			if(!visited[i]) {
				visited[i] = true;
				arr[cnt] = i;
				Perm(cnt+1);
				visited[i] = false;
			}
		}
	}//Perm
	
}//class

```

- 순열을 이용하여 백트랙킹을 구현
- Stringbuilder를 이용하여 문자열을 출력하는 방식으로 구현.

