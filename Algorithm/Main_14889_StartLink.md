# 알고리즘
[백준 14889번: 스타트와 링크](https://www.acmicpc.net/problem/14889)
```java
package bruteforce_;

import java.io.*;
import java.util.*;

public class Main_14889_StartLink {

	private static int min = Integer.MAX_VALUE;
	private static int[][] map;
	private static int[] set, arr;
	private static boolean[] visited;
	private static int N, sub;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		N = Integer.parseInt(br.readLine());
		map = new int [N+1][N+1];
		for (int i = 1; i <= N; i++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			for (int j = 1; j <= N; j++) {
				map[i][j] = Integer.parseInt(st.nextToken());
			}
		}
		arr = new int [N];
		for (int i = 1; i <= N; i++) {
			arr[i-1] = i;
		}
		set = new int [N/2];
		Comb(set, 0, 0, N, set.length);
		System.out.println(min);
	}//main
	public static void Comb(int [] set, int size, int index, int n, int r) {
		if(r==0) {
			visited = new boolean[N+1];
			for (int i = 0; i < set.length; i++) {
				visited[set[i]] = true;
			}
			Process();
			return;
		}else if(n==index) return;
		else {
			set[size] = arr[index];
			Comb(set, size+1, index+1, N, r-1);
			Comb(set, size, index+1, N, r);
		}
	}//Comb
	public static void Process() {
		int start = 0;
		int link = 0;
		for (int i = 1; i <= N; i++) {
			if(visited[i]) {
				for (int j = 1; j <= N; j++) {
					if(i==j) continue;
					if(visited[j]) start += map[i][j];
				}
			}else {
				for (int j = 1; j <= N; j++) {
					if(i==j) continue;
					if(!visited[j]) link += map[i][j];
				}
			}
		}
		sub = (int) Math.abs(start-link);
		if(min > sub) min = sub;
	}//Process
}//class
```
- 조합으로 구현. 
