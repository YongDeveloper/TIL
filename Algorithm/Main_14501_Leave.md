# 알고리즘
[백준 14501번:퇴사](https://www.acmicpc.net/problem/14501)
```java
package dfs_;

import java.io.*;
import java.util.*;

public class Main_14501_Leave {

	private static int[] T, P;
	private static int N, max = Integer.MIN_VALUE;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		N = Integer.parseInt(br.readLine());
		T = new int [N];
		P = new int [N];
		for (int i = 0; i < N; i++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			T[i] = Integer.parseInt(st.nextToken());
			P[i] = Integer.parseInt(st.nextToken());
		}
		DFS(0,0);
		System.out.println(max);
	}//main
	public static void DFS(int index, int price) {
		if(index>=N) {
			max = Math.max(max, price);
			return;
		}
		else {
			if(index + T[index] <=N) DFS(index+T[index], price+P[index]);
			else DFS(index + T[index], price);
			
			DFS(index+1, price);
		}
	}//DFS
}//class
```
- bruteforce 문제
- DFS, DP, 완탐의 방법이 있지만 DFS로 구현.
