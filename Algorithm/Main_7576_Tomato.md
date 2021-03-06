# 알고리즘

[백준 7576번: 토마토](https://www.acmicpc.net/problem/7576)

```java
public class Main_7576_Tomato {

	private static int N,M;
	private static int[][] map;
	private static boolean[][] visited;
	private static int [] dx = {0,0,-1,1};
	private static int [] dy = {-1,1,0,0};
	private static Queue<Integer> qx = new LinkedList<Integer>();;
	private static Queue<Integer> qy = new LinkedList<Integer>();
	private static Integer x,y;
	private static int result;
	private static int nx,ny;
	
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		M = Integer.parseInt(st.nextToken());
		N = Integer.parseInt(st.nextToken());
		map = new int [N][M];
		visited = new boolean [N][M];
		
		for (int i = 0; i < N; i++) {
			st = new StringTokenizer(br.readLine());
			for (int j = 0; j < M; j++) {
				map[i][j] = Integer.parseInt(st.nextToken());
				//System.out.print(map[i][j]+" ");
				if(map[i][j]==1) {
					
					qx.offer(j);
					qy.offer(i);
					
				}
			}
			//System.out.println();
		}
		
		BFS();
		
		for (int i = 0; i < N; i++) {
			for (int j = 0; j < M; j++) {
				if(map[i][j] == 0) result = -1;
			}
		}
		
		if(result > 0) System.out.println(result-1);
		else System.out.println(result);
		
	}//main

	public static void BFS() {
		
		result = 0;
			
		while(!qx.isEmpty() && !qy.isEmpty()) {
			
			x = qx.poll();
			y = qy.poll();
			
			visited[y][x] = true;
			
			for (int i = 0; i < 4; i++) {
				ny = y + dy[i];
				nx = x + dx[i];
				
				if(ny>=0 && nx>=0 && ny<N && nx<M) {
					if(map[ny][nx]==0 && !visited[ny][nx]) {
						
						qx.offer(nx);
						qy.offer(ny);
						visited[ny][nx] = true;
						map[ny][nx] = map[y][x]+1;
						
						result = map[ny][nx];
					}
				}
			}
			
		}//while
		
	}//BFS
	
}//class



```

- BFS를 이용하여 구현.
