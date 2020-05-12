# 알고리즘
[백준 13549번:숨바꼭질 3](https://www.acmicpc.net/problem/13549)
```java
package bfs_;

import java.io.*;
import java.util.*;

public class Main_13549_HideAndSeek3 {

	private static int N, K;
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		K = Integer.parseInt(st.nextToken());
		
		if(N>=K) System.out.println(N-K);
		else System.out.println(BFS(N));
		
	}//main
	
	public static int BFS(int N) {
		Queue<Integer> queue = new LinkedList<>();
		int [] arr = new int[100001];
		boolean [] visited = new boolean[100001];
		visited[N] = true;
		queue.offer(N);
		
		while(!queue.isEmpty()) {
			int now = queue.poll();
			if(now*2 <= 100000 && !visited[now*2]) {
				visited[now*2] = true;
				queue.offer(now*2);
				arr[now*2] = arr[now];
			}
			if(now-1 >= 0 && !visited[now-1]) {
				visited[now-1] = true;
				queue.offer(now-1);
				arr[now-1] = arr[now] + 1;
			}
			if(now+1 <= 100000 && !visited[now+1]) {
				visited[now+1] = true;
				queue.offer(now+1);
				arr[now+1] = arr[now] + 1;
			}
		}
		return arr[K];
	}//BFS
}//class
```
- BFS로 구현.
