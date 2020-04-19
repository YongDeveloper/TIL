# 알고리즘
[백준 1085번:직사각형에서 탈출](https://acmicpc.net/problem/1085)
```java
package math_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_1085_Rectangular {

	public static void main(String[] args) throws IOException{

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int x = Integer.parseInt(st.nextToken());
		int y = Integer.parseInt(st.nextToken());
		int w = Integer.parseInt(st.nextToken());
		int h = Integer.parseInt(st.nextToken());
		int min = Integer.MAX_VALUE;
		
		if(min > Math.min(x, w-x)) min = Math.min(x, w-x);
		if(min > Math.min(y, h-y)) min = Math.min(y, h-y);
		
		System.out.println(min);
		
	}//main

}//class

```
- 수학 문제
- 경계값 비교만 하여 구현
