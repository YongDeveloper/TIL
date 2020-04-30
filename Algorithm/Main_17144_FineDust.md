# 알고리즘
[백준 17144번: 미세먼지 안녕!](https://www.acmicpc.net/problem/17144)
```java
package simulation_;

import java.io.*;
import java.util.*;

public class Main_17144_FineDust {

	private static int R, C, T, sum;
	private static int[][] map;
	private static int [] dy = {0,0,1,-1};
	private static int [] dx = {1,-1,0,0};
	private static int [] cy = new int [2];
	private static int [] cx = new int [2];
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		R = Integer.parseInt(st.nextToken());
		C = Integer.parseInt(st.nextToken());
		T = Integer.parseInt(st.nextToken());
		map = new int [R][C];
		int c = 0;
		for (int i = 0; i < R; i++) {
			st = new StringTokenizer(br.readLine());
			for (int j = 0; j < C; j++) {
				map[i][j] = Integer.parseInt(st.nextToken());
				if(map[i][j]==-1) {
					cy[c] = i;
					cx[c] = j;
					c++;
				}
			}
		}
		for (int t = 0; t < T; t++) {
			Diffusion(t);
			Process();
			//MapPrint();
		}
		sum = 0;
		for (int i = 0; i < R; i++) {
			for (int j = 0; j < C; j++) {
				if(map[i][j]!= -1) sum += map[i][j];
			}
		}
		System.out.println(sum);
		
	}//main
	public static void Diffusion(int time) {
		int dir = 0;
		int [][] tempMap = new int [R][C];
		
		for (int i = 0; i < R; i++) {
			for (int j = 0; j < C; j++) {
				
				if(map[i][j]!=1 && map[i][j]!=0) {
					for (int k = 0; k < 4; k++) {
						int ny = i + dy[k];
						int nx = j + dx[k];
						if(ny>=0 && ny<R && nx>=0 && nx<C
								&& map[ny][nx]!=-1 ) {
							tempMap[ny][nx] += map[i][j]/5; 
							dir++;
						}
					}
					map[i][j] = map[i][j]-map[i][j]/5 * dir;
					dir = 0;
				}
			}
		}
		
		for (int i = 0; i < R; i++) {
			for (int j = 0; j < C; j++) {
				map[i][j] += tempMap[i][j];
			}
		}
		
	}//diffusion
	
	public static void Process() {
		// 위
		int r = cy[0]-1;
		int c = cx[0];
		for (; 0 <= r-1; r--) { // 상
			map[r][c] = map[r-1][c];
		}
		for (; c+1 < C; c++) { // 우
			map[r][c] = map[r][c+1];
		}
		for (; r+1 <= cy[0]; r++) { // 하
			map[r][c] = map[r+1][c];
		}
		for (; 1 <= c-1; c--) { // 좌
			map[r][c] = map[r][c-1];
		}
		map[r][c] = 0;

		//아래
		r = cy[1]+1; 
		c = cx[1];
		
		for (; r+1 < R; r++) { // 하
			map[r][c] = map[r+1][c];
		}
		for (; c+1 < C; c++) { // 우
			map[r][c] = map[r][c+1];
		}
		for (; cy[1]+1 <= r; r--) { // 상
			map[r][c] = map[r-1][c];
		}
		for (; 1 <= c-1; c--) { // 좌
			map[r][c] = map[r][c-1];
		}
		map[r][c] = 0;
		
	}//Process
	
	public static void MapPrint() {
		for (int i = 0; i < R; i++) {
			for (int j = 0; j < C; j++) {
				System.out.print(map[i][j]+" ");
			}
			System.out.println();
		}
		System.out.println();
	}
	
}//class

```
- 단순 시뮬레이션 문제.
