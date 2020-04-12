# 알고리즘
[백준 2160번:그림 비교](https://www.acmicpc.net/problem/2160)
```java
package simulation_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;

public class Main_2160_PicVsPic {

	public static void main(String[] args) throws IOException {

		BufferedReader br =new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		int [][][] map = new int [N][5][7];
		int cnt = 0; int num1 = 0; int num2 = 0;
		int min = Integer.MAX_VALUE;
		
		for (int tc = 0; tc < N; tc++) {
			for (int i = 0; i < 5; i++) {
				String str = br.readLine();
				for (int j = 0; j < 7; j++) {
					map[tc][i][j] = str.charAt(j)-'0';
				}
			}
		}//input
		
		for (int tc1 = 0 ; tc1 < N; tc1++) {
			for (int tc2 = tc1+1; tc2 < N; tc2++) {
				cnt = 0;
				for (int k = 0; k < 5; k++) {
					for (int m = 0; m < 7; m++) {
						if(map[tc1][k][m]!=map[tc2][k][m]) cnt++;
					}
				}
				if(min > cnt) {
					min = cnt;
					num1 = tc1+1;
					num2 = tc2+1;
				}
			}
		}
		
		System.out.println(num1+" "+num2);
	}//main

}//class

```
- 시뮬레이션 문제
- 여러개의 for을 이용하여 구현 
