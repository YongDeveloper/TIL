# 알고리즘
[백준 15656번: N과 M (7)](https://www.acmicpc.net/problem/15656)
```java
package backtracking_;

import java.io.*;
import java.util.*;

public class Main_15656_NandM7 {

	private static int[] arr;
	private static int[] set;
	private static int N, M;
	public static StringBuilder sb = new StringBuilder();

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		M = Integer.parseInt(st.nextToken());
		arr = new int [N];
		set = new int [M];
		st = new StringTokenizer(br.readLine());
		for (int i = 0; i < arr.length; i++) {
			arr[i] = Integer.parseInt(st.nextToken());
		}
		Arrays.sort(arr);
		Perm(0);
		System.out.println(sb);
		
	}//main
	
	public static void Perm(int size) {
		if(size == M) {
			for (int i = 0; i < M; i++) {
				sb.append(set[i]+" ");
			}
			sb.append("\n");
		}else {
			for (int i = 0 ; i < N; i++) {
				set[size] = arr[i];
				Perm(size+1);
			}
		}
	}//Perm
}//class
```
- backtracking 문제. 순열로 구현.
