# 알고리즘
[백준 2468번:안전 영역](https://www.acmicpc.net/problem/2468)
```java
package dfs_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_2468_SafetyRegion {

	public static int [] dy = {0,0,-1,1};
	public static int [] dx = {-1,1,0,0};
	private static boolean[][] visited;
	private static int[][] map;
	private static int N;
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		map = new int [N][N];
		visited = new boolean [N][N];
		int maxhigh = 0; int cnt = 0;
		int max = Integer.MIN_VALUE;
		
		for (int i = 0; i < N; i++) {
			st = new StringTokenizer(br.readLine());
			for (int j = 0; j < N; j++) {
				map[i][j] = Integer.parseInt(st.nextToken());
				if(maxhigh < map[i][j]) maxhigh = map[i][j];
			}
		}
		
		for (int k = 1; k <= maxhigh; k++) {
			cnt = 0;
			visited = new boolean [N][N];
			for (int i = 0; i < N; i++) {
				for (int j = 0; j < N; j++) {
					if(!visited[i][j] && map[i][j] >= k) {
						cnt++;
						DFS(i,j,k);
					}
				}
			}
			if(max < cnt) max = cnt;
		}
		System.out.println(max);
		
	}//main

	public static void DFS(int y, int x, int high) {
		
		if(visited[y][x]) return;
		visited[y][x] = true;
		
		for (int i = 0; i < 4; i++) {
			int ny = y + dy[i];
			int nx = x + dx[i];
			
			if(nx>=0 && ny>=0 && nx<N && ny<N) {
				if(!visited[ny][nx] && map[ny][nx]>= high) {
					DFS(ny, nx, high);
				}
			}
		}
		
	}//DFS
	
}//class

```
- DFS문제
