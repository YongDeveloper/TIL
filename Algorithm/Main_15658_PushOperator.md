# 알고리즘
[백준 15658번: 연산자 끼워넣기2](https://www.acmicpc.net/problem/15658)

```java
package bruteforce_;

import java.io.*;
import java.util.*;

public class Main_15658_PushOperator {

	private static int max = Integer.MIN_VALUE, min = Integer.MAX_VALUE;
	private static int N;
	private static int[] arr;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		N = Integer.parseInt(br.readLine());
		arr = new int [N];
		StringTokenizer st = new StringTokenizer(br.readLine());
		for (int i = 0; i < N; i++) {
			arr[i] = Integer.parseInt(st.nextToken());
		}
		st = new StringTokenizer(br.readLine());
		int A = Integer.parseInt(st.nextToken());
		int S = Integer.parseInt(st.nextToken());
		int M = Integer.parseInt(st.nextToken());
		int D = Integer.parseInt(st.nextToken());
		
		DFS(arr[0], 1, A, S, M, D);
		System.out.println(max);
		System.out.println(min);
	}//main
	
	public static void DFS(int sum, int index, int A, int S, int M, int D) {
		if(index==N) {
			if(sum > max) max = sum;
			if(sum < min) min = sum;
			return;
		}else {
			if(A>0)    	DFS(sum+arr[index], index+1, A-1, S, M, D);
			if(S>0) DFS(sum-arr[index], index+1, A, S-1, M, D);
			if(M>0) DFS(sum*arr[index], index+1, A, S, M-1, D);
			if(D>0) DFS(sum/arr[index], index+1, A, S, M, D-1);
		}
	}//Process
}//class
```
- Bruteforce 문제
- 순열로 구현했더니 시간초과.
- DFS로
