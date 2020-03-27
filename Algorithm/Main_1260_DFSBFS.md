# 알고리즘

[백준 1260번:DFSBFS](https://www.acmicpc.net/problem/1260)

```java
public class Main_1260_DFSBFS {

	public static ArrayList<Integer>[] list;
	public static int N;
	
	public static StringBuilder DFSResult = new StringBuilder();
	public static StringBuilder BFSResult = new StringBuilder();
	
	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		int M = Integer.parseInt(st.nextToken());
		int V = Integer.parseInt(st.nextToken());
		
		list = new ArrayList[N+1];
		boolean [] visited = new boolean [N+1];
		
		for (int i = 1; i <= N; i++) {
			list[i] = new ArrayList<Integer>();
		}
		
		for (int i = 0; i < M ; i++) {
			st = new StringTokenizer(br.readLine());
			int A = Integer.parseInt(st.nextToken()); 
			int B = Integer.parseInt(st.nextToken());
			
			list[A].add(B);
			list[B].add(A);
			
			Collections.sort(list[A]);
			Collections.sort(list[B]);
			
		}// list 구현하기
		
		for (int i = 1; i <= N; i++) {
			Collections.sort(list[i]);
		}
		
		DFS(V, visited);
		visited = new boolean [N+1];
		BFS(V, visited);
		System.out.println(DFSResult);
		System.out.println(BFSResult);
		
		
	}//main
	
	private static void DFS(int now, boolean [] visited) {
		if(visited[now]) return;
		visited[now] = true;
		DFSResult.append(now+" ");
		
		for (int next : list[now]) {
			DFS(next, visited);
		}
		
	}//DFS
	
	private static void BFS(int now, boolean [] visited) {
		
		Queue<Integer> queue = new LinkedList<Integer>();
		queue.offer(now);
		
		while(!queue.isEmpty()) {
			
			now = queue.poll();
			if(visited[now]) continue;
			visited[now] = true;
			BFSResult.append(now+" ");
			queue.addAll(list[now]);
			
		}//while
		
	}//BFS
	
}//class


```
- 배열대신 ArrayList를 이용하였다.
- DFS는 재귀함수를 이용하였고 BFS는 Queue를 이용하였다.

