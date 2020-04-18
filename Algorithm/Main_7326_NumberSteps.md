[백준 7326번:Number Steps](https://www.acmicpc.net/problem/7326)
```java
package datastructure_;

import java.io.InputStreamReader;
import java.util.StringTokenizer;
import java.io.BufferedReader;
import java.io.IOException;

public class Main_7326_NumberSteps {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int TC = Integer.parseInt(br.readLine());
		
		for (int tc = 1; tc <= TC; tc++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			int x = Integer.parseInt(st.nextToken());
			int y = Integer.parseInt(st.nextToken());
			int cnt = 0; int dx = 0; int dy = 0;
			boolean check = false;
			while(true) {
				if(dx == x && dy == y) break;
				if(dx == 5000 && dy == 5000) {
					check = true; 
					break;
				}
				if(cnt%4==0) { dx++; dy++; cnt++;}
				else if(cnt%4==1) { dx++; dy--; cnt++;}
				else if(cnt%4==2) { dx++; dy++; cnt++;}
				else if(cnt%4==3) { dx--; dy++; cnt++;}
			}
			if(!check) System.out.println(cnt);
			else System.out.println("No Number");
		}//tc
		
	}//main

}//class

```
- 자료구조 문제였지만 시뮬레이션처럼 구현.
