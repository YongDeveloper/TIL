# 알고리즘
[백준 10974번:모든 순열](https://www.acmicpc.net/problem/10974)
```java
package permutation_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;

public class Main_10974_AllPerm {

	private static int N;
	private static int[] arr;
	private static boolean[] visited;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		N = Integer.parseInt(br.readLine());
		arr = new int[N];
		visited = new boolean[N];
		Perm(0);
		
	}//main

	public static void Perm(int r) {
		if(r==N) {
			for (int i = 0; i < N; i++) {
				System.out.print(arr[i]+" ");
			}
			System.out.println();
		}else {
			for (int i = 0; i < N; i++) {
				if(!visited[i]) {
					visited[i] = true;
					arr[r] = i+1;
					Perm(r+1);
					visited[i] = false;
				}
			}
		}
		
	}//Perm
}//class

```
- 순열 문제.
