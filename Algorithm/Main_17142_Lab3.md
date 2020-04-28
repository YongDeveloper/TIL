# 알고리즘
[백준 17142번: 연구소3](https://www.acmicpc.net/problem/17142)
```java
package simulation_;

import java.io.*;
import java.util.*;

public class Main_17142_Lab3 {

	private static int N, M;
	private static int cnt = 0;
	private static int result = Integer.MAX_VALUE;
	private static int[][] map;
	private static boolean[] check;
	private static ArrayList<Member> virus;
	private static int[] dy = {0,0,1,-1};
	private static int[] dx = {1,-1,0,0};
	
	public static class Member{
		int y;
		int x;
		
		public Member(int y, int x) {
			this.y = y;
			this.x = x;
		}
		
	}//member
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		M = Integer.parseInt(st.nextToken());
		map = new int [N][N];
		
		virus = new ArrayList<>();
		
		for (int i = 0; i < N; i++) {
			st = new StringTokenizer(br.readLine());
			for (int j = 0; j < N; j++) {
				map[i][j] = Integer.parseInt(st.nextToken());
				if(map[i][j] == 2) virus.add(new Member(i,j));
				if(map[i][j] == 0) cnt++;
			}
		}
		check = new boolean [virus.size()];
		if(cnt!=0) Comb(0 , 0);
		else result = 0;
		
		if(result == Integer.MAX_VALUE) System.out.println("-1");
		else System.out.println(result);
		
	}//main

	public static void Comb(int depth, int start) {
		if(depth == M) {
			int [][] copyMap = copy();
			BFS(copyMap, cnt);
			return;
		}
		for (int i = start ; i < virus.size(); i++) {
			check[i] = true;
			Comb(depth+1, i+1);
			check[i] = false;
		}
			
	}//Comb
	public static void BFS(int [][] map, int cnt) {
		Queue<Member> queue = new LinkedList<>();
		for (int i = 0; i < virus.size(); i++) {
			if(check[i]) queue.offer(virus.get(i));
		}
		int time = 0;
		while(!queue.isEmpty()) {
			if(result <= time) break;
			int size = queue.size();
			
			for (int i = 0; i < size; i++) {
				Member member = queue.poll();
				
				for (int j = 0; j < 4; j++) {
					int ny = member.y + dy[j];
					int nx = member.x + dx[j];
					
					if(nx<0 || nx>=N || ny<0 || ny>=N 
							|| map[ny][nx] == 1 || map[ny][nx] == 2) continue;
					if(map[ny][nx] == 0) cnt--;
					map[ny][nx] = 2;
					queue.offer(new Member(ny,nx));
				}
			}
			time++;
			if(cnt==0) {
				result = time;
				return;
			}
		}
	}
	
	public static int [][] copy() {
		int [][] copy = new int [N][N];
		for (int i = 0; i < N; i++) {
			System.arraycopy(map[i], 0, copy[i], 0, N);
		}
		for (int i = 0; i < virus.size(); i++) {
			if(!check[i]) {
				Member member = virus.get(i);
				copy[member.y][member.x] = 7;
			}
		}
		return copy;
	}
}//class

```
- 시뮬레이션 문제.
