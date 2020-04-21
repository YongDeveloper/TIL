# 알고리즘
[백준 3055번:탈출](https://www.acmicpc.net/problem/3055)
```java
package simulation_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.LinkedList;
import java.util.Queue;
import java.util.StringTokenizer;

public class Main_3055_Exit {

	public static Queue<Member> queGo;
	public static Queue<Member> queStar;
	public static int [] dy = {1,-1,0,0};
	public static int [] dx = {0,0,1,-1};
	private static char[][] map;
	private static int cnt;
	private static int R, C;
	public static String str = "KAKTUS";

	public static class Member{
		int y;
		int x;
		public Member(int y, int x) {
			this.y = y;
			this.x = x;
		}
	}//Member class
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		R = Integer.parseInt(st.nextToken());
		C = Integer.parseInt(st.nextToken());
		map = new char [R][C];
		
		queGo = new LinkedList<>();
		queStar = new LinkedList<>();
		
		for (int i = 0; i < R; i++) {
			String [] str = br.readLine().split("");
			for (int j = 0; j < C; j++) {
				map[i][j] = str[j].charAt(0);
				if(map[i][j] == 'S') queGo.add(new Member(i,j));
				if(map[i][j] == '*') queStar.add(new Member(i,j));
			}
		}
		cnt = 0;
		BFS(map);
		System.out.println(cnt);
		
	}//main

	public static void BFS(char[][] map) {
		while(true) {
			cnt++;
			int sizeStar = queStar.size();
			for (int i = 0; i < sizeStar; i++) {
				Member mem = queStar.poll();
				
				for (int j = 0; j < 4; j++) {
					int ny = mem.y + dy[j];
					int nx = mem.x + dx[j];
					
					if(nx>=0 && ny>=0 && nx<C && ny <R) {
						if(map[ny][nx] == '.') {
							map[ny][nx] = '*';
							queStar.add(new Member(ny,nx));
						}
					}
				}
			}
			if(queGo.size()==0) {
				System.out.println(str);
				System.exit(0);
			}
			
			int sizeGo = queGo.size();
			for (int i = 0; i < sizeGo; i++) {
				
				Member mem = queGo.poll();
				
				for (int j = 0; j < 4; j++) {
					int ny = mem.y + dy[j];
					int nx = mem.x + dx[j];
					
					if(nx>=0 && ny>=0 && nx<C && ny<R) {
						if(map[ny][nx] == 'D') return;
						if(map[ny][nx] == '.') {
							map[ny][nx] = 'S';
							queGo.add(new Member(ny,nx));
						}
					}
				}
			}
		}
	}//BFS
	
}//class

```
- 시뮬레이션 문제.
- Queue를 이용하여 최단 경로를 찾았다.
