# 알고리즘
[백준 11656번:접미사 배열](https://www.acmicpc.net/problem/11656)
```java
package charcter_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;

public class Main_11656_SuffixArray {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		String [] arr = new String [str.length()];
		for (int i = 0; i < str.length(); i++) {
			arr[i] = str.substring(i, str.length());
		}
		Arrays.sort(arr);
		for (int i = 0; i < arr.length; i++) {
			System.out.println(arr[i]);
		}
		
	}//main

}//class
```
- 문자열 처리 문제
- substring으로 배열에 담아 출력.
