# 알고리즘
[백준 1182번:부분수열의 합](https://www.acmicpc.net/problem/1182)
```java
package bruteforce_;

import java.io.*;
import java.util.*;

public class Main_1182_SequenceSum {

	private static int[] arr, set;
	private static int N, S, cnt;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		S = Integer.parseInt(st.nextToken());
		arr = new int [N];
		set = new int [21];
		st = new StringTokenizer(br.readLine());
		for (int i = 0; i < arr.length; i++) {
			arr[i] = Integer.parseInt(st.nextToken());
		}
		Comb(set, 0, 0, N, S);
		System.out.println(cnt);
	}//main
	public static void Comb(int [] set, int size, int index, int N, int S) {
		if(N==index) {
			int sum = 0;
			for (int i = 0; i < size; i++) {
				//System.out.print(set[i]+" ");
				sum += set[i];
			}
			//System.out.println();
			if(size!=0 && sum==S) cnt++;
			return;
		}else {
			set[size] = arr[index];
			Comb(set, size+1, index+1, N, S);
			Comb(set, size, index+1, N, S);
		}
	}//Comb
}//class
```
- DFS 문제 subset으로 구현.
