# 알고리즘
[백준 6603번:로또](https://www.acmicpc.net/problem/6603)
```java
package dfs_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_6603_Lotto {

	private static int[] arr;
	private static int N;
	private static int K = 6;
	private static int[] set;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		while(true) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			N = Integer.parseInt(st.nextToken());
			if(N==0) break;
			arr = new int [N];
			set = new int [49];
			for (int i = 0; i < N; i++) {
				arr[i] = Integer.parseInt(st.nextToken());
			}
			Comb(set,0,0,N,K);
			System.out.println();
			
		}//while
	}//main

	public static void Comb (int [] set, int size, int index, int N, int K) {
		if(K==0) {
			for (int i = 0; i < size; i++) {
				System.out.print(arr[set[i]] +" ");
			}
			System.out.println();
			return;
		}else if(index==N) return;
		
		set[size] = index;
		Comb(set, size+1, index+1, N, K-1);
		Comb(set, size, index+1, N, K);
	}
}//class

```
- 조합문제로 구현.
