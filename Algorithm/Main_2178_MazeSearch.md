# 알고리즘
[백준 2178번: 미로 탐색](https://www.acmicpc.net/problem/2178)

```java

public class Main_2178_MazeSearch {

	private static int[][] map;
	private static int [] dx = {0,0,-1,1};
	private static int [] dy = {-1,1,0,0};
	private static boolean [][] visited;
	private static int M;
	private static int N;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		M = Integer.parseInt(st.nextToken());
		map = new int [N][M];
		visited = new boolean [N][M];
		String str = "";
		
		for (int i = 0; i < N; i++) {
			str = br.readLine();
			for (int j = 0; j < M; j++) {
				map[i][j] = str.charAt(j)-'0';
				//System.out.print(map[i][j]+ " ");
			}
			//System.out.println();
		}
		
		BFS(0,0);
		
		System.out.println(map[N-1][M-1]);
		
	}//main

	public static void BFS(int y, int x) {
		Queue<Integer> qx = new LinkedList<>();
		Queue<Integer> qy = new LinkedList<>();
		
		qx.offer(x);
		qy.offer(y);
		
		while(!qx.isEmpty() && !qy.isEmpty()) {
			x = qx.poll();
			y = qy.poll();
			
			visited[y][x] = true;
			
			for (int i = 0; i < 4; i++) {
				int ny = y + dy[i];
				int nx = x + dx[i];
				
				if(nx >=0 && ny >=0 && nx <M && ny<N) {
					if(map[ny][nx]==1 & !visited[ny][nx]) {
						
						qx.offer(nx);
						qy.offer(ny);
						visited[ny][nx] = true;
						map[ny][nx] = map[y][x]+1;
					}
				}
			}
			
		}//while
		
	}//BFS
	
}//class

```

- 사방탐색 BFS로 구현하였다.
