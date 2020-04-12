# 알고리즘
[백준 1100번:하얀 칸](https://www.acmicpc.net/problem/1100)
```java
package charcter_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main_1100_WhiteSpace {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = 8;
		int cnt = 0;
		for (int i = 0; i < N; i++) {
			String [] str = br.readLine().split("");
			for (int j = 0; j < N; j++) {
				if((i+j)%2==0 && str[j].equals("F")) cnt++;
			}
		}
		
		System.out.println(cnt);
		
	}//main

}//class
```
- 간단한 문자열 처리 문제.
