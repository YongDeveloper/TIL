# 알고리즘
[백준 14502번: 연구소](https://www.acmicpc.net/problem/14502)
```java
package dfs_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.StringTokenizer;

public class Main_14502_Lab {

	private static int[][] map;
	private static int[][] temp;
	private static int [] dx = {-1,1,0,0}; 
	private static int [] dy = {0,0,-1,1}; 
	private static int N;
	private static int M;
	private static ArrayList<Virus> virus;
	private static ArrayList<Virus> wall;
	private static int [] set;
	private static int max;

	public static class Virus{
		int y;
		int x;
		public Virus(int y, int x) {
			this.y = y;
			this.x = x;
		}
		
	}//Virus
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		M = Integer.parseInt(st.nextToken());
		map = new int [N][M];
		virus = new ArrayList<>();
		wall = new ArrayList<>();
		
		for (int i = 0; i < N; i++) {
			st = new StringTokenizer(br.readLine());
			for (int j = 0; j < M; j++) {
				map[i][j] = Integer.parseInt(st.nextToken());
				if(map[i][j]==2) virus.add(new Virus(i,j));
				if(map[i][j]==0) wall.add(new Virus(i,j));
				
			}
		}
		set = new int[3];
		int n = wall.size(); // 0(빈칸)인곳의 모든 좌표의 갯수
		int k = set.length; // 3개
		
		Comb(set, 0, n, k, 0);
		
		System.out.println(max);
		
	}//main

	public static void Comb(int[] set, int size, int n, int k, int index) {
		
		if(k==0) {
			temp = new int[N][M];
			Copy();
			// 새로운 맵 세팅하기
			for (int i = 0; i < size; i++) {
				Virus virus = wall.get(set[i]);
				temp[virus.y][virus.x] = 1;
			}// 새 맵에 바이러스 담기
			
			for (int i = 0; i < virus.size(); i++) {
				DFS_virus(virus.get(i));
			}// 2(바이러스) 기준으로 전파시키기
			
			int cnt = 0;
			for (int i = 0; i < N; i++) {
				for (int j = 0; j < M; j++) {
					if(temp[i][j]==0) cnt++;
				}
			}// 안전영역 개수 세기
			
			if(max < cnt) max = cnt;
			return;
			
		}
		
		else if(n==index) return;
		else {
			set[size] = index;
			Comb(set, size+1, n, k-1, index+1);
			Comb(set, size, n, k, index+1);
		}
		
	}//Comb - 벽 3개 세울곳 판단 후 안전영역 갯수 세기
	
	public static void DFS_virus(Virus virus) {
		int y = virus.y;
		int x = virus.x;

		for (int i = 0; i < 4; i++) {
			int ny = y + dy[i];
			int nx = x + dx[i];
			
			if(nx>=0 && ny>=0 && ny<N && nx<M) {
				if(temp[ny][nx] == 0) {
					temp[ny][nx] = 2;
					DFS_virus(new Virus(ny,nx));
				}
			}
		}
		
	}//DFS_virus : 0인곳을 2로 바꾸고  DFS
	
	public static void DFS_wall(int y, int x) {
		
		for (int i = 0; i < 4; i++) {
			int ny = y + dy[i];
			int nx = x + dx[i];
			
			if(nx>=0 && ny>=0 && nx<N && ny<M) {
				if(temp[ny][nx] == 0) wall.add(new Virus(ny,nx));
			}
		}
		
	}//0인곳에 벽세우기 
	
	public static void Copy() {
		for (int i = 0; i < N; i++) {
			for (int j = 0; j < M; j++) {
				temp[i][j] = map[i][j];
			}
		}
	}//copy - 맵 복사하기
	
	
}//class

```
- DFS 문제
