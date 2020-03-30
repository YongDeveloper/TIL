# 알고리즘

[백준 1697번: 숨바꼭질](https://www.acmicpc.net/problem/1697)


```java

public class Main_1697_HideAndSeek {

	private static int N, K, cnt;
	private static int [] visited = new int [100001];
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		K = Integer.parseInt(st.nextToken());
		
		BFS(N);
//		for (int i = 0; i < 20; i++) {
//			System.out.print(i%10+" ");
//		}
//		System.out.println();
//		for (int i = 0; i < 20; i++) {
//			System.out.print(visited[i]-1+" ");
//		}
		System.out.println(visited[K]-1);
		
	}//main
	
	public static void BFS(int N) {
		
		Queue<Integer> queue = new LinkedList<>();
		queue.offer(N);
		visited[N] = 1;
		
		while(!queue.isEmpty()) {
			
			N = queue.poll();
			
			if (N==K) {
				break;
			}
			if(N+1<=100000 && visited[N+1]==0) {
				queue.offer(N+1);
				visited[N+1] = visited[N]+1;
			}
			if(N-1>=0 && visited[N-1]==0) {
				queue.offer(N-1);
				visited[N-1] = visited[N]+1;
			}
			if(N*2<=100000 && visited[N*2]==0) {
				queue.offer(N*2);
				visited[N*2] = visited[N]+1;
			}
			
		}//while
		
	}//BFS
	
}//class

```

5 17
0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 
5 4 3 2 1 0 1 2 2 2 1 2 2 3 3 4 3 4 3 3

- BFS를 이용하여 구현.
