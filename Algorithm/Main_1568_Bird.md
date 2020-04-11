# 알고리즘
[백준 1568번: 새](https://www.acmicpc.net/problem/1568)
```java
package search_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main_1568_Bird {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		int K = 1; 
		int cnt = 0;
		while(N>0) {
			if(N>=K) {
				N -= K; K++; cnt++;
			}else {//N < cnt
				K = 1; N -= K; K++; cnt++;
			}
		}
		System.out.println(cnt);
		
	}//main

}//class

```
- 탐색 문제
- 시뮬레이션 문제 처럼 구현
