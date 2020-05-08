# 알고리즘
[백준 1707번:이분 그래프](https://www.acmicpc.net/problem/1707)
```java
package bfs_;

import java.io.*;
import java.util.*;

public class Main_1710_BipartiteGraph {

	private static int[] palette;
	private static ArrayList[] list;
	private static int V, E;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int TC = Integer.parseInt(br.readLine());
		
		for (int tc = 1; tc <= TC; tc++) {
			
			StringTokenizer st = new StringTokenizer(br.readLine());
			V = Integer.parseInt(st.nextToken());
			E = Integer.parseInt(st.nextToken());
			palette = new int [V+1];
			list = new ArrayList[V+1];
			
			for (int i = 1; i <= V; i++) {
				list[i] = new ArrayList<>();
			}
			
			for (int i = 0; i < E; i++) {
				st = new StringTokenizer(br.readLine());
				int from = Integer.parseInt(st.nextToken());
				int to = Integer.parseInt(st.nextToken());
				list[from].add(to);
				list[to].add(from);
			}
			
			for (int i = 1; i <= V; i++) {
				if(palette[i]== 0) DFS(i, 1);
			}
			
			if(check()) System.out.println("YES");
			else System.out.println("NO");
			
		}//tc
	}//main
	
	public static void DFS(int v, int color) {
		palette[v] = color;
		
		for (int i = 0; i < list[v].size(); i++) {
			int index = (int) list[v].get(i);
			if(palette[index] == 0) DFS(index, color*-1);
		}
		
	}//DFS
	
	public static boolean check() {
		for (int i = 1; i <= V; i++) {
			for (int j = 0; j < list[i].size(); j++) {
				if(palette[i] == palette[(int) list[i].get(j)]) return false;
			}
		}
		return true;
	}//Check
}//class
```
- 이분 그래프 문제 : 인접정점 끼리는 다른 종류의 색깔이어야 한다.
- DFS로 구현하였다.
