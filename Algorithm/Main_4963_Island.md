# 알고리즘
[백준 4963번:섬의 개수](https://www.acmicpc.net/problem/4963)
```java
package bfs_;

import java.io.*;
import java.util.*;

public class Main_4963_Island {

	private static int [] dy = {0,0,1,-1,1,1,-1,-1};
	private static int [] dx = {1,-1,0,0,1,-1,1,-1};
	private static boolean[][] visited;
	private static int[][] map;
	private static int w, h, cnt;
	
	private static class Member{
		int y;
		int x;
		public Member(int y, int x) {
			this.y = y;
			this.x = x;
		}
	}

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		while(true) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			w = Integer.parseInt(st.nextToken());
			h = Integer.parseInt(st.nextToken());
			if(w == 0 && h == 0) break;
			map = new int [h][w];
			cnt = 0;
			for (int i = 0; i < h; i++) {
				st = new StringTokenizer(br.readLine());
				for (int j = 0; j < w; j++) {
					map[i][j] = Integer.parseInt(st.nextToken());
				}
			}
			visited = new boolean[h][w];
			
			for (int i = 0; i < h; i++) {
				for (int j = 0; j < w; j++) {
					if(map[i][j] == 1 && !visited[i][j]) {
						cnt++;
						BFS(i,j);
					}
				}
			}
			System.out.println(cnt);
		}
	}//main
	public static void BFS(int y, int x) {
		Queue<Member> queue = new LinkedList<>();
		queue.offer(new Member(y,x));
		visited[y][x] = true;
		
		while(!queue.isEmpty()) {
			Member member = queue.poll();
			
			for (int i = 0; i < dx.length; i++) {
				int ny = member.y + dy[i];
				int nx = member.x + dx[i];
				
				if(nx>=0 && nx<w && ny>=0 && ny<h
						&& !visited[ny][nx] && map[ny][nx] == 1) {
					visited[ny][nx] = true;
					queue.offer(new Member(ny,nx));
				}
			}
		}
	}//BFS
}//class

```
- BFS 문제. 
