# 알고리즘
[백준 2178번:미로 탐색](https://www.acmicpc.net/problem/2178)
```java
package dfs_bfs_;

import java.io.*;
import java.util.*;

public class Main_2178_MazeSearch2 {

	private static int [] dx = {0,0,1,-1};
	private static int [] dy = {1,-1,0,0};
	private static boolean [][] visited;
	private static int[][] map;
	private static int M, N;

	public static class Member{
		int y;
		int x;
		public Member(int y, int x) {
			this.y = y;
			this.x = x;
		}
		
	}//Member
	
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
			}
		}
		BFS(0,0);
		System.out.println(map[N-1][M-1]);
		
	}//main

	public static void BFS(int y, int x) {
		
		Queue<Member> queue = new LinkedList<>();
		queue.offer(new Member(y,x));
		
		while(!queue.isEmpty()) {
			Member member = queue.poll();
			visited[member.y][member.x] = true;
			
			for (int i = 0; i < 4; i++) {
				int ny = member.y + dy[i];
				int nx = member.x + dx[i];
				
				if(nx>=0 && ny>=0 && nx<M && ny<N 
						&& map[ny][nx]==1 & !visited[ny][nx]) {
						
						queue.offer(new Member(ny,nx));
						visited[ny][nx] = true;
						map[ny][nx] = map[member.y][member.x] + 1;
				}
			}
		}//while
	}//BFS
	
}//class

```
- BFS 복습.
