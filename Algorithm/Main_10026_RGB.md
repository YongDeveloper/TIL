# 알고리즘
[백준 10026번:적록색약](https://www.acmicpc.net/problem/10026)
```java
package bfs_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.LinkedList;
import java.util.Queue;

public class Main_10026_RGB {

	private static char[][] map;
	private static boolean [][] visited;
	private static int N;
	private static int [] dx = {-1,1,0,0};
	private static int [] dy = {0,0,-1,1};
	private static Queue<Member> queue = new LinkedList<>();

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
		N = Integer.parseInt(br.readLine());
		map = new char [N][N];
		for (int i = 0; i < N; i++) {
			String str = br.readLine();
			for (int j = 0; j < N; j++) {
				map[i][j] = str.charAt(j);
			}
		}
		
		int result1 = BFS();
		
		for (int i = 0; i < N; i++) {
			for (int j = 0; j < N; j++) {
				if(map[i][j]=='R') map[i][j]='G';
			}
		}
		
		int result2 = BFS();
		
		System.out.println(result1 +" "+result2);
	}//main

	public static int BFS() {
		int cnt = 0;
		visited = new boolean [N][N];

		for (int i = 0; i < N; i++) {
			for (int j = 0; j < N; j++) {
				
				if(visited[i][j]) continue;
				visited[i][j] = true;
				queue.offer(new Member(i,j));
				
				while(!queue.isEmpty()) {
					Member member = queue.poll();
					
					for (int k = 0; k < 4; k++) {
						int ny = member.y + dy[k];
						int nx = member.x + dx[k];
						
						if(nx>=0 && ny>=0 && nx<N && ny<N) {
							if(!visited[ny][nx] && map[ny][nx]==map[i][j]) {
								
								visited[ny][nx] = true;
								queue.offer(new Member(ny,nx));
							}
						}
					}
				}
				cnt++;
			}
		}
		return cnt;
		
	}//BFS
	
}//class

```
- BFS 문제.
