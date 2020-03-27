# 알고리즘

[백준 2606번:바이러스](https://www.acmicpc.net/problem/2606)

```java
package step28;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.Collections;
import java.util.LinkedList;
import java.util.Queue;
import java.util.StringTokenizer;

public class Main_2606_Virus {
	public static int N, cnt;
	public static ArrayList<Integer>[] list;
	public static StringBuilder sb = new StringBuilder();
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		st = new StringTokenizer(br.readLine());
		int M = Integer.parseInt(st.nextToken());
		int V = 1;
		
		list = new ArrayList[N+1];
		boolean [] visited = new boolean [N+1];
		cnt = -1;
		
		for (int i = 1; i <= N; i++) {
			list[i] = new ArrayList<>();
		}
		
		for (int i = 0; i < M; i++) {
			st = new StringTokenizer(br.readLine());
			int A = Integer.parseInt(st.nextToken());
			int B = Integer.parseInt(st.nextToken());
			
			list[A].add(B);
			list[B].add(A);
			
			Collections.sort(list[A]);
			Collections.sort(list[B]);
		}
		for (int i = 1; i <= N; i++) {
			Collections.sort(list[i]);
		}
		
		DFS(V, visited);
		//BFS(V, visited);
		//System.out.println(sb);
		System.out.println(cnt);
		
	}//main

	public static void DFS(int now, boolean [] visited) {
		if(visited[now]) return;
		visited[now] = true;
		sb.append(now+" ");
		cnt++;
		for (int next : list[now]) {
			DFS(next, visited);
		}
		
	}//DFS
	
	public static void BFS(int now, boolean [] visited) {
		Queue<Integer> queue = new LinkedList<Integer>();
		queue.offer(now);
		
		while(!queue.isEmpty()) {
			now = queue.poll();
			if(visited[now]) continue;
			visited[now] = true;
			sb.append(now+" ");
			cnt++;
			queue.addAll(list[now]);
			
		}
		
	}//BFS
	
}//class


```
- 제출시 DFS로 풀고 정답 후 BFS 방법까지 모두 풀어 보았다.
- Main_1260 방법과 같은 방식으로 해결.


