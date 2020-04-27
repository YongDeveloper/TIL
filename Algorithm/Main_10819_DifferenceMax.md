# 알고리즘
[백준 10819번: 차이를 최대로](https://www.acmicpc.net/problem/10819)
```java
package bruteforce_;

import java.io.*;
import java.util.*;

public class Main_10819_DifferenceMax {

	private static int[] arr;
	private static int[] set;
	private static boolean[] visited;
	private static int sum, max, N;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		arr = new int [N];
		set = new int [N];
		visited = new boolean [N];
		max = Integer.MIN_VALUE;
		
		st = new StringTokenizer(br.readLine());
		for (int i = 0; i < arr.length; i++) {
			arr[i] = Integer.parseInt(st.nextToken());
		}
		Perm(0);
		System.out.println(max);
		
	}//main
	public static void Perm(int size) {
		if(size==N) {
			Process();
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
	
	public static void Process() {
		sum = 0;
		for (int i = 0; i < set.length-1; i++) {
			sum += Math.abs(set[i] - set[i+1]);
		}
		if(max < sum) max = sum;
	}//Process
}//class

```
- bruteforce 문제.
- 순열로 문제 구현.
