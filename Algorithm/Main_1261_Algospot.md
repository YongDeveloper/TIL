# 알고리즘
[백준 1261번: 알고스팟](https://www.acmicpc.net/problem/1261)
```java
package bfs_;

import java.io.*;
import java.util.*;

public class Main_1261_Algospot {

	private static int[][] map, weight;
	private static boolean[][] visited;
	private static int [] dy = {0,0,1,-1};
	private static int [] dx = {1,-1,0,0};
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
		M = Integer.parseInt(st.nextToken());
		N = Integer.parseInt(st.nextToken());
		map = new int [N][M];
		weight = new int [N][M];
		visited = new boolean [N][M];
		
		for (int i = 0; i < N; i++) {
			String str = br.readLine();
			for (int j = 0; j < M; j++) {
				map[i][j] = str.charAt(j)-'0';
			}
		}
		BFS(0,0);
		System.out.println(weight[N-1][M-1]);
	}//main

	public static void BFS(int y, int x) {
		Deque <Member> deque = new LinkedList<>();
		deque.offerLast(new Member(y, x));
		
		while(!deque.isEmpty()) {
			Member mem = deque.pollLast();
			visited[y][x] = true;
			
			for (int i = 0; i < 4; i++) {
				int ny = mem.y + dy[i];
				int nx = mem.x + dx[i];
				
				if(nx>=0 && ny>=0 && nx<M && ny<N && !visited[ny][nx]) {
					if(map[ny][nx]== 0) {
						weight[ny][nx] = weight[mem.y][mem.x];
						deque.addLast(new Member(ny,nx));
						
					}else if(map[ny][nx]== 1) {
						weight[ny][nx] = weight[mem.y][mem.x] + 1;
						deque.addFirst(new Member(ny,nx));
					}
					visited[ny][nx] = true;
				}
			}
		}
	}//BFS
}//class

```
- Deque를 이용하여 구현.
