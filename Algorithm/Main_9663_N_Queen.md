# 알고리즘
[백준 9663번: N-Queen](https://www.acmicpc.net/problem/9663)
```java
package dfs_;

import java.io.*;
import java.util.*;

public class Main_9663_N_Queen {

	private static int[][] map;
	private static int N, cnt=0;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		N = Integer.parseInt(br.readLine());
		map = new int [N][N];
		DFS(0);
		System.out.println(cnt);
	}//main
	public static void DFS(int index) {
		if(index==N) {
			//for (int i = 0; i < N; i++) System.out.println(Arrays.toString(map[i]));
			cnt++;
			return;
		}else {
			for (int i = 0; i < N; i++) {
				if(isOkay(index, i)) {
					map[index][i] = 1;
					DFS(index+1);
					map[index][i] = 0;
				}
			}
		}
	}//DFS
	public static boolean isOkay(int y, int x) {
		for (int r = y; r >= 0 ; r--) {
			if(map[r][x]==1) return false;
		}
		for (int r = y, c = x; r >= 0 && c>= 0; r--, c--) {
			if(map[r][c]==1) return false;
		}
		for (int r = y, c = x; r >= 0 && c< N; r--, c++) {
			if(map[r][c]==1) return false;
		}
		return true;
	}//isOkay
}//class
``` 
- DFS 문제. 백트랙킹으로 구현.
