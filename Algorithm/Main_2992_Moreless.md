# 알고리즘
[백준 2992번: 크면서 작은 수](https://www.acmicpc.net/problem/2992)
```java
package for_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;

public class Main_2992_Moreless {

	private static int[] arr;
	private static boolean[] visited;
	private static boolean check;
	private static int[] out;
	private static int input;
	private static int min=Integer.MAX_VALUE;
	

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		input = Integer.parseInt(str);
		int N = str.length();
		int R = str.length();
		visited = new boolean [N];
		arr = new int [N];
		out = new int [N];
		for (int i = 0; i < str.length(); i++) {
			arr[i] = str.charAt(i)-'0';
		}
		check = false;
		Perm(0, N, R);
		
		if(!check) System.out.println("0");
		else System.out.println(min);
	}//main

	public static void Perm (int depth, int n, int r) {
		if(depth == r) {
			String s = "";
			for (int i = 0; i < out.length; i++) {
				s += Integer.toString(out[i]);
			}
			int now = Integer.parseInt(s);
			if(now > input && min > now) {
				min = now; 
				check = true;
			}
		}
		for (int i = 0; i < n; i++) {
			if(!visited[i]) {
				visited[i] = true;
				out[depth] = arr[i];
				Perm(depth+1, n, r);
				visited[i] = false;
			}
		}
	}
}//class

```
- 순열 알고리즘으로 구현.
