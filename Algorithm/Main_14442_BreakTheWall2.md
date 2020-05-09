# 알고리즘
[백준 14442번: 벽 부수고 이동하기 2](https://www.acmicpc.net/problem/14442)
```java
package bfs_;

import java.io.*;
import java.util.*;

public class Main_14442_BreakTheWall2 {

	private static int N, M, K, min = Integer.MAX_VALUE;
	private static int[][] map, wall;
	private static int [] dy = {0,0,1,-1};
	private static int [] dx = {1,-1,0,0};

	public static class Member{
		int y;
		int x;
		int distance;
		int breakcnt;
		public Member(int y, int x, int distance, int breakcnt) {
			this.y = y;
			this.x = x;
			this.distance = distance;
			this.breakcnt = breakcnt;
		}
	}
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		M = Integer.parseInt(st.nextToken());
		K = Integer.parseInt(st.nextToken());
		map = new int [N][M];
		wall = new int [N][M];
		for (int i = 0; i < N; i++) {
			String str = br.readLine();
			for (int j = 0; j < M; j++) {
				map[i][j] = str.charAt(j)-'0';
				wall[i][j] = Integer.MAX_VALUE;
			}
		}
		BFS(0,0);
		if(min==Integer.MAX_VALUE) System.out.println("-1");
		else System.out.println(min);
		
	}//main
	public static void BFS(int y, int x) {
		Queue<Member> queue = new LinkedList<>();
		queue.offer(new Member(y, x, 1, 0));
		wall[y][x] = 0;
		
		while(!queue.isEmpty()) {
			Member mem = queue.poll();
			
			if(mem.y == N-1 && mem.x == M-1) {
				min = mem.distance;
				break;
			}
			
			for (int i = 0; i < 4; i++) {
				int ny = mem.y + dy[i];
				int nx = mem.x + dx[i];
				
				if(nx<0 || nx>=M || ny<0 || ny>=N) continue;
				if(wall[ny][nx] <= mem.breakcnt) continue;
				
				if(map[ny][nx] == 1) { // 벽
					if(mem.breakcnt < K) {
						wall[ny][nx] = mem.breakcnt + 1;
						queue.offer(new Member(ny, nx, mem.distance+1, mem.breakcnt+1));
					}
				}else if(map[ny][nx] == 0) { // 빈공간
					wall[ny][nx] = mem.breakcnt;
					queue.offer(new Member(ny, nx, mem.distance+1, mem.breakcnt));
				}
			}
		}
	}//BFS
}//class

```
- BFS로 구현.
