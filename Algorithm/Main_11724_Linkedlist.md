# 알고리즘
[백준 11724번: 연결 요소의 개수](https://www.acmicpc.net/problem/11724)
```java
package bfs_;

import java.io.*;
import java.util.*;

public class Main_11724_Linkedlist {

	public static ArrayList<Integer>[] list;
	private static boolean[] visited;
	private static int cnt;
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int M = Integer.parseInt(st.nextToken());
		
		list = new ArrayList[N+1];
		visited = new boolean[N+1];
		
		for (int i = 1; i <= N; i++) {
			list[i] = new ArrayList<>();
		}
		
		for (int i = 0; i < M; i++) {
			st = new StringTokenizer(br.readLine());
			int u = Integer.parseInt(st.nextToken());
			int v = Integer.parseInt(st.nextToken());
			list[u].add(v);
			list[v].add(u);
		}
		for (int i = 1; i <= N; i++) {
			Collections.sort(list[i]);
		}
		
		for (int i = 1; i <= N; i++) {
			if(!visited[i]) {
				DFS(i);
				cnt++;
			}
		}
		System.out.println(cnt);
		
	}//main
	public static void DFS(int i) {
		visited[i] = true;
		
		for (int v : list[i]) {
			if(!visited[v]) DFS(v);
		}
	}//DFS
	
}//class
```
- DFS 문제.
