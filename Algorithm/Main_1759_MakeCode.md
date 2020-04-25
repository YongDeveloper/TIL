# 알고리즘
[백준 1759번:암호 만들기](https://www.acmicpc.net/problem/1759)
```java
package bruteforce_;

import java.io.*;
import java.util.*;

public class Main_1759_MakeCode {
	private static ArrayList<String> list = new ArrayList<>();
	private static char [] index = {'a','e','i','o','u'};
	private static char[] arr;
	private static int [] set;
	private static int L, C, cnt; 
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		L = Integer.parseInt(st.nextToken());
		C = Integer.parseInt(st.nextToken());
		arr = new char [C];
		String [] str = br.readLine().split(" ");
		for (int i = 0; i < arr.length; i++) {
			arr[i] = str[i].charAt(0);
		}
		Arrays.sort(arr);
		set = new int [L];
		Comb(set, 0, 0, arr.length, set.length);
		
		Collections.sort(list);
		for (String s : list) {
			System.out.println(s);
		}
		
	}//main

	public static void Comb(int[] set, int size, int index, int n , int r) {
		if(r==0) {
			Process();
		}else if(n==index) return;
		else {
			set[size] = index;
			Comb(set, size+1, index+1, n, r-1);
			Comb(set, size, index+1, n, r);
		}
	}//Comb
	
	public static void Process() {
		cnt = 0;
		for (int i = 0; i < set.length; i++) {
			for (int j = 0; j < index.length; j++) {
				if(arr[set[i]] == index[j]) {
					cnt++;
					break;
				}
			}
		}
		String str = "";
		if(cnt>=1 && (L-cnt)>=2) {
			for (int i = 0; i < set.length; i++) {
				str += arr[set[i]];
			}
			list.add(str);
		}
	}//Process
}//class

```
- bruteforce 문제
- 조합과 정렬로 문제 해결.
