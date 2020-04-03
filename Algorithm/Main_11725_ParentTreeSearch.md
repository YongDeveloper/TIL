# 알고리즘

[백준 11725번 : 트리의 부모 찾기](https://www.acmicpc.net/problem/11725)

```java
public class Main_11725_ParentTreeSearch {

	private static ArrayList<Integer>[] list;
	private static int N;
	private static boolean [] visited;
	private static int [] parents;
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		list = new ArrayList[N+1];
		visited = new boolean[N+1];
		parents = new int [N+1];
		
		for (int i = 1; i <= N; i++) {
			list[i] = new ArrayList<Integer>();
		}
		
		for (int i = 1; i < N; i++) {
			st = new StringTokenizer(br.readLine());
			int a = Integer.parseInt(st.nextToken());
			int b = Integer.parseInt(st.nextToken());
			list[a].add(b);
			list[b].add(a);
		}
		for (int i = 1; i <= N; i++) {
			if(!visited[i]) DFS(i); 
		}
		
		for (int i = 2; i <= N; i++) {
			System.out.println(parents[i]);
		}
		
	}//main
	
	public static void DFS(int v) {
		if(visited[v]) return;
		else {
			visited[v] = true;
			for (int dv : list[v]) {
				if(!visited[dv]) {
					parents[dv] = v;
					DFS(dv);
				}
			}
		}
	}//DFS
}//class
```

- Arraylist를 이용하여 정점끼리의 관계를 나타냈다.
- 부모의 위치를 찾을 때 DFS로 구현하였다.
