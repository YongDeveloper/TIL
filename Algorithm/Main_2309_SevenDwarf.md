# 알고리즘
[백준 2309번:일곱 난쟁이](https://www.acmicpc.net/problem/2309)

```java
package samsung_;

import java.io.*;
import java.util.*;

public class Main_2309_SevenDwarf {

	private static int[] arr;
	private static int[] set;
	private static int sum;
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		arr = new int[9];
		set = new int[7];
		for (int i = 0; i < arr.length; i++) {
			arr[i] = Integer.parseInt(br.readLine());
		}
		Comb(set, 0, 0, arr.length, set.length);
	}//main
	public static void Comb(int[] set , int size, int index, int n, int r) {
		if(r==0) {
			Process();
		}else if (n==index) return;
		else {
			set[size] = index;
			Comb(set, size+1, index+1 , n , r-1);
			Comb(set, size, index+1, n, r);
		}
	}//Comb
	public static void Process() {
		sum = 0;
		for (int i = 0; i < set.length; i++) {
			sum += arr[set[i]];
		}
		if(sum==100) {
			for (int i = set.length-1; i > 0; i--) {
				for (int j = 0; j < i; j++) {
					if(arr[set[j]] > arr[set[j+1]]) {
						int temp = arr[set[j]];
						arr[set[j]] = arr[set[j+1]];
						arr[set[j+1]] = temp;
					}
				}
			}// bubble sort
			for (int i = 0; i < set.length; i++) {
				System.out.println(arr[set[i]]);
			}
			System.exit(0);
		}
	}//Process
}//class

```
- bruteforce 문제
- 정답이 여러개일 경우 하나만 맞으면 System.exit(0); 으로 빠져나온다.
