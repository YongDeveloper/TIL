# 알고리즘
[백준 1012번:유기농 배추](https://www.acmicpc.net/problem/1012)

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_1012_OrganicCabbage {

	private static int [] dx = {-1,1,0,0};
	private static int [] dy = {0,0,-1,1};
	private static boolean [][] visited;
	private static int [][] map;
	private static int cnt;
	private static int W;
	private static int D;
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int TC = Integer.parseInt(st.nextToken());
		
		for (int tc = 1; tc <= TC; tc++) {

			st = new StringTokenizer(br.readLine());
			W = Integer.parseInt(st.nextToken()); // 가로
			D = Integer.parseInt(st.nextToken()); // 세로
			int N = Integer.parseInt(st.nextToken()); // 갯수
			
			map = new int [W][D];
			visited = new boolean [W][D];
			cnt = 0;
			
			for (int i = 0; i < N; i++) {
				st = new StringTokenizer(br.readLine());
				map[Integer.parseInt(st.nextToken())][Integer.parseInt(st.nextToken())]=1;
			}// input
			
			for (int j = 0; j < W; j++) {
				for (int i = 0; i < D; i++) {
					//System.out.print(map[j][i]+" ");
					if(map[j][i]==1 && !visited[j][i]) {
						cnt++;
						DFS(j,i);
					}
				}
				//System.out.println();
			}
			System.out.println(cnt);
			
			
		}//TC
		
	}//main

	public static void DFS(int x, int y) {
		visited[x][y] = true;
		for (int i = 0; i < 4; i++) {
			int ny = x + dy[i];
			int nx = y + dx[i];
			
			if(ny >=0 && nx >=0 && ny <W && nx <D) {
				if(map[ny][nx]==1 && !visited[ny][nx]) {
					DFS(ny,nx);
				}
			}
		}
		
	}//DFS
	
}//class

```

- Main_2667_PostNum 문제와 비슷한 유형으로 DFS (사방탐색+재귀)를 이용하였다.

