# 알고리즘
[백준 15654번:N과 M (5)](https://www.acmicpc.net/problem/15654)

```java
package backtracking_;

import java.io.*;
import java.util.*;

public class Main_15654_NandM5 {

	private static int[] arr;
	private static int[] set;
	private static int N, M;
	private static boolean[] visited;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		M = Integer.parseInt(st.nextToken());
		arr = new int [N];
		visited = new boolean[N];
		
		set = new int [M];
		st = new StringTokenizer(br.readLine());
		for (int i = 0; i < arr.length; i++) {
			arr[i] = Integer.parseInt(st.nextToken());
		}
		Arrays.sort(arr);
		Perm(0);
	}//main
	
	public static void Perm(int size) {
		if(size == M) {
			for (int i = 0; i < M; i++) {
				System.out.print(set[i]+" ");
			}
			System.out.println();
		}else {
			for (int i = 0; i < N; i++) {
				if(!visited[i]) {
					visited[i] = true;
					set[size] = arr[i];
					Perm(size+1);
					visited[i] = false;
				}
			}
		}
	}//Perm
}//class

```
- backtracking문제 순열로 구현
