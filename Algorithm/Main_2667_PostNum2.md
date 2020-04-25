# 알고리즘
[백준 2667번:단지번호붙이기](https://www.acmicpc.net/problem/2667)
```java
package dfs_bfs_;

import java.io.*;
import java.util.*;

public class Main_2667_PostNum2 {

		
	private static int N;
	private static int cnt;
	private static int [][] map;
	private static boolean [][] visited;
	private static int [] dx = {0,0,-1,1};
	private static int [] dy = {1,-1,0,0};
	private static ArrayList<Integer> list = new ArrayList<>(); 
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		map = new int [N][N];
		visited = new boolean [N][N];
		
		for (int i = 0; i < N; i++) {
			String [] str = br.readLine().split("");
			for (int j = 0; j < N; j++) {
				map[i][j] = str[j].charAt(0)-'0';
			}
		}
		for (int i = 0; i < N; i++) {
			for (int j = 0; j < N; j++) {
				if(map[i][j]==1 && !visited[i][j]) {
					cnt = 1;
					DFS(i,j);
					list.add(cnt);
				}
			}
		}
		Collections.sort(list);
		System.out.println(list.size());
		
		for (int i = 0; i < list.size(); i++) {
			System.out.println(list.get(i));
		}
			
		
	}//main

	public static int DFS(int y, int x) {
		visited[y][x] = true;
		for (int i = 0; i < 4; i++) {
			int ny = y + dy[i];
			int nx = x + dx[i];
			
			if(ny>=0 && nx>=0 && ny<N && nx<N) {
				if(map[ny][nx]==1 && !visited[ny][nx]) {
					DFS(ny,nx);
					cnt++;
				}
			}	
		}
		
		return cnt;
		
	}//DFS
	
}//class

```
- DFS 복습.
