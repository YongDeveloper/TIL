# 알고리즘
[백준 15650번: N과M (2)](https://www.acmicpc.net/problem/15650)

```java
public class Main_15650_NandM2 {

	private static int N;
	private static int R;
	private static int[] arr;
	private static boolean[] visited;
	private static boolean check;
	private static StringBuilder sb = new StringBuilder();

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		R = Integer.parseInt(st.nextToken());
		arr = new int [N+1];
		visited = new boolean [N+1];
		Perm(0,0);
		System.out.println(sb);
		
	}//main
	
	public static void Perm(int index, int cnt) {
		if(cnt==R) {
			for (int i = 0; i < R; i++) {
				sb.append(arr[i]+" ");
			}
			sb.append("\n");
		}
		for (int i = index+1; i <= N; i++) {
			if(!visited[i]) {
				visited[i] = true;
				arr[cnt] = i;
				Perm(i, cnt+1);
				visited[i] = false;
			}
		}
		
	}//Perm

}//class
```

- 백준 14549번 문제에 코드 한개만 추가하였다.
- Perm 메서드에서 반복문을 돌때 오름차순만 출력하기 위함
- index 변수를 추가하여 index 이상부터 반복문을 돌 수 있게 했다.
