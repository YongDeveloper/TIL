# 알고리즘
[백준 7576번:토마토](https://www.acmicpc.net/problem/7576)
```java
package dfs_bfs_;

import java.io.*;
import java.util.*;

public class Main_7576_Tomato2 {

	private static int N, M, result;
	private static int[][] map;
	private static boolean[][] visited;
	private static int [] dx = {0,0,-1,1};
	private static int [] dy = {-1,1,0,0};
	private static Queue<Member> queue =  new LinkedList<>();
	
	public static class Member{
		int y;
		int x;
		public Member(int y, int x) {
			this.y = y;
			this.x = x;
		}
	}
	
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
				if(map[i][j]==1) queue.offer(new Member(i,j));
			}
		}
		result = 0;
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
		
		while(!queue.isEmpty()) {
			
			Member member = queue.poll();
			visited[member.y][member.x] = true;
			
			for (int i = 0; i < 4; i++) {
				int ny = member.y + dy[i];
				int nx = member.x + dx[i];
				
				if(ny>=0 && nx>=0 && ny<N && nx<M
						&& map[ny][nx]==0 && !visited[ny][nx]) {
						
					queue.offer(new Member(ny,nx));
					visited[ny][nx] = true;
					map[ny][nx] = map[member.y][member.x] + 1;
					result = map[ny][nx];
					
				}
			}
			
		}//while
	}//BFS
	
}//class

```
- BFS 문제 복습.
