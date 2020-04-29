# 알고리즘
[백준 15683번:감시](https://www.acmicpc.net/problem/15683)
```java
package simulation_;

import java.io.*;
import java.util.*;

public class Main_15683_CCTV {

	private static int[][] map;
	private static ArrayList<CCTV> list = new ArrayList<>();
	private static int N, M;
	private static int min = Integer.MAX_VALUE;

	public static class CCTV{
		int y;
		int x;
		int type;
		public CCTV(int y, int x, int type) {
			this.y = y;
			this.x = x;
			this.type = type;
		}
	}//member
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		M = Integer.parseInt(st.nextToken());
		map = new int [N][M];
		for (int i = 0; i < N; i++) {
			st = new StringTokenizer(br.readLine());
			for (int j = 0; j < M; j++) {
				map[i][j] = Integer.parseInt(st.nextToken());
				if(map[i][j]>=1 && map[i][j]<=5) list.add(new CCTV(i,j, map[i][j]));
			}
		}
		DFS(0, map);
		System.out.println(min);
	}//main
	public static void DFS(int index, int [][] prev) {
		int [][] visited = new int [N][M];
		if(index==list.size()) {
			int cnt = 0;
			for (int i = 0; i < N; i++) {
				for (int j = 0; j < M; j++) {
					if(prev[i][j] == 0) cnt++;
				}
			}
			if(min > cnt) min = cnt;
		}
		else {
			CCTV cctv = list.get(index);
			int dy = cctv.y;
			int dx = cctv.x;
			int type = cctv.type;
			
			switch (type) {
			case 1:
				for (int k = 0; k < 4; k++) {
					for (int i = 0; i < N; i++) {
						System.arraycopy(prev[i], 0, visited[i], 0, M);
					}
					Detect(visited, dy, dx, k);
					DFS(index+1, visited);
				}
				break;
			case 2:
				for (int k = 0; k < 2; k++) {
					for (int i = 0; i < N; i++) {
						System.arraycopy(prev[i], 0, visited[i], 0, M);
					}
					Detect(visited, dy, dx, k); // 0동 1남
					Detect(visited, dy, dx, k+2);// 2서 3북
					DFS(index+1, visited);
				}
				break;
			case 3:
				for (int k = 0; k < 4; k++) {
					for (int i = 0; i < N; i++) {
						System.arraycopy(prev[i], 0, visited[i], 0, M);
					}
					Detect(visited, dy, dx, k); 		// 0동 1남 2서 3북
					Detect(visited, dy, dx, (k+1)% 4);  // 1남 2서 3북 0동
					DFS(index+1, visited);
				}
				break;
			case 4:
				for (int k = 0; k < 4; k++) {
					for (int i = 0; i < N; i++) {
						System.arraycopy(prev[i], 0, visited[i], 0, M);
					}
					Detect(visited, dy, dx, k); 		// 0동 1남 2서 3북
					Detect(visited, dy, dx, (k+1)% 4);  // 1남 2서 3북 0동
					Detect(visited, dy, dx, (k+2)% 4);  // 2서 3북 0동 1남
					DFS(index+1, visited);
				}
				break;
			case 5:
				for (int i = 0; i < N; i++) {
					System.arraycopy(prev[i], 0, visited[i], 0, M);
				}
				Detect(visited, dy, dx, 0);
				Detect(visited, dy, dx, 1);
				Detect(visited, dy, dx, 2);
				Detect(visited, dy, dx, 3);
				DFS(index+1, visited);
				break;
			}//switch
		}
	}//DFS
	
	public static void Detect(int [][] visited, int dy, int dx, int dir) {
		switch (dir) {
		case 0: // 동
			for (int i = dx; i < M; i++) {
				if(visited[dy][i]== 6) break;
				visited[dy][i] = 7; // 벽을 제외한 모든 수 7로 바꾼다.
			}
			break;
		case 1: // 남
			for (int i = dy; i < N; i++) {
				if(visited[i][dx]==6) break;
				visited[i][dx] = 7;
			}
			break;
		case 2: // 서
			for (int i = dx; i >= 0; i--) {
				if(visited[dy][i]==6) break;
				visited[dy][i] = 7;
			}
			break;
		case 3: // 북
			for (int i = dy; i >= 0; i--) {
				if(visited[i][dx]==6) break;
				visited[i][dx] = 7;
			}
			break;
		}
	}//Detect
}//class

```
- 시뮬레이션 문제. DFS로 구현.
- System.arraycopy를 잘 구현하기 
	- System.arraycopy(원본, 0, 복사본, 0, 길이);
	- 원본 맵을 복사할때 오리지날 원본 맵인지 이전 맵인지 잘 구분하자.
