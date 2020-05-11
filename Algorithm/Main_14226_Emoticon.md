# 알고리즘
[백준 14226번:이모티콘](https://www.acmicpc.net/problem/14226)
```java
package bfs_;

import java.io.*;
import java.util.*;

public class Main_14226_Emoticon {
	private static boolean[][] visited;
	private static int S;
	
	public static class Member{
		int emo;
		int clip;
		int time;
		public Member(int emo, int clip, int time) {
			this.emo = emo;
			this.clip = clip;
			this.time = time;
		}
	}//member

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		S = Integer.parseInt(br.readLine());
		visited = new boolean[2000][2000];
		BFS();
	}//main
	
	public static void BFS() {
		Queue<Member> queue = new LinkedList<>();
		queue.offer(new Member(1, 0, 0));
		
		while(!queue.isEmpty()) {
			Member mem = queue.poll();
			int nemo = mem.emo;
			int nclip = mem.clip;
			int ntime = mem.time;
			
			if(nemo == S) {
				System.out.println(ntime);
				return;
			}
			if(nemo > 0 && nemo < 2000) {
				if(!visited[nemo][nemo]) { // 복사 + 시간증가
					visited[nemo][nemo] = true;
					queue.offer(new Member(nemo, nemo, ntime+1));
				}
				if(!visited[nemo-1][nclip]) { // 삭제 + 시간증가
					visited[nemo-1][nclip] = true;
					queue.offer(new Member(nemo-1, nclip, ntime+1));
				}
			}
			if(nclip > 0 && nclip+nemo < 2000) { // 붙여넣기 + 시간증가
				visited[nclip+nemo][nclip] = true;
				queue.offer(new Member(nclip+nemo, nclip, ntime+1));
			}
		}
	}//BFS
}//class
```
- BFS로 구현.
