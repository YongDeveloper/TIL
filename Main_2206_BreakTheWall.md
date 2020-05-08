# 알고리즘
[백준 2206번:벽 부수고 이동하기](https://www.acmicpc.net/problem/2206)
```java
package bfs_;

import java.io.*;
import java.util.*;

public class Main_2206_BreakTheWall {

	private static int[][] map, wall;
	private static int [] dy = {0,0,1,-1};
	private static int [] dx = {1,-1,0,0};
	private static int N, M, min = Integer.MAX_VALUE;
	
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
		map = new int [N][M];
		wall = new int [N][M];
		
		for (int i = 0; i < N; i++) {
			String str = br.readLine();
			for (int j = 0; j < M; j++) {
				map[i][j] = str.charAt(j)-'0';
				wall[i][j] = Integer.MAX_VALUE;
			}
		}
		BFS(0, 0);
		if(min == Integer.MAX_VALUE) System.out.println("-1");
		else System.out.println(min);
		
	}//main
	public static void BFS(int y, int x) {
		Queue <Member> queue = new LinkedList<>();
		queue.offer(new Member(y, x, 1, 0));
		wall[y][x] = 0;
		
		while(!queue.isEmpty()) {
			Member mem = queue.poll();
			
			if(mem.y==N-1 && mem.x==M-1){
				min = mem.distance;
				break;
			}
			for (int i = 0; i < 4; i++) {
				int ny = mem.y + dy[i];
				int nx = mem.x + dx[i];
				
				if(nx<0 || nx>=M || ny<0 || ny>=N) continue;
				if(wall[ny][nx] <= mem.breakcnt) continue;
				
				if(map[ny][nx] == 0) {
					wall[ny][nx] = mem.breakcnt;
					queue.offer(new Member(ny, nx, mem.distance+1, mem.breakcnt));
					
				}else {
					if(mem.breakcnt==0) {
						wall[ny][nx] = mem.breakcnt + 1;
						queue.offer(new Member(ny, nx, mem.distance+1, mem.breakcnt+1));
					}
				}
			}
		}
	}//BFS
```
- 최단 경로를 구하는 문제. BFS로 구현.
