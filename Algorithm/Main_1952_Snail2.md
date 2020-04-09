# 알고리즘
[백준 1952번:달팽이2](https://www.acmicpc.net/problem/1952)
```java
package simulation_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_1952_Snail2 {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int M = Integer.parseInt(st.nextToken());
		int N = Integer.parseInt(st.nextToken());
		int [][] map = new int [M][N];
		boolean [][] visited = new boolean [M][N];
		int [] dx = {1,0,-1,0};
		int [] dy = {0,1,0,-1};
		int x = 0; int y = 0; int cnt = 0; int dir = 0;
		
		while(true) {
			
			if(visited[y][x]) break;
			else {
				visited[y][x] = true;
				int nx = x + dx[dir];
				int ny = y + dy[dir];
				
				if(nx<0 || ny<0 || nx>=N || ny>=M || visited[ny][nx]) {
					dir++;
					if(dir>=4) dir-=4;
					cnt++;
				}
				x = x + dx[dir];
				y = y + dy[dir];
			}
		}
		System.out.println(cnt-1);
	}//main

}//class
```
- 시뮬레이션 문제
- 배열돌리기나 사방탐색으로 구현하였다.
