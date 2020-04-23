# 알고리즘
[백준 9613번:GCD 합](https://www.acmicpc.net/problem/9613)
```java
package samsung_;

import java.io.*;
import java.util.*;

public class Main_9613_SumOfGCD {

	private static long[] arr;
	private static int[] set;
	private static long sum;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int TC = Integer.parseInt(br.readLine());
		for (int tc = 1; tc <= TC; tc++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			int N = Integer.parseInt(st.nextToken());
			arr = new long [N];
			set = new int [2];
			for (int i = 0; i < arr.length; i++) {
				arr[i] = Integer.parseInt(st.nextToken());
			}
			sum = 0;
			Comb(set, 0, 0, arr.length, set.length);
			System.out.println(sum);
		}//tc
	}//main

	public static void Comb(int[] set, int size, int index, int n , int r) {
		if(r==0) {
			Process();
		}else if(n==index) return;
		else {
			set[size] = index;
			Comb(set, size+1, index+1, n, r-1);
			Comb(set ,size, index+1, n, r);
		}
		
	}//Comb
	
	public static void Process() {
		long num1 = arr[set[0]];
		long num2 = arr[set[1]];
		long temp = Math.min(num1, num2);
		while(temp > 0) {
			if(num1%temp==0 && num2%temp==0) {
				sum += temp;
				break;
			}
			temp--;
		}
	}//process
	
}//class

```
- 조합과 GCD에 관한 문제
- int형에서 long형으로 바꾸니 통과.
