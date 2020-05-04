# 알고리즘
[백준 11723번: 집합](https://www.acmicpc.net/problem/11723)
```java
package bitmask_;

import java.io.*;
import java.util.*;

public class Main_11723_Set {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringBuilder sb = new StringBuilder();
		int TC = Integer.parseInt(br.readLine());
		int bitmask = 0;
		
		for (int tc = 1; tc <= TC; tc++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			String str = st.nextToken();
			
			if(str.equals("all")) bitmask |= (1<<21) -1;
			else if(str.equals("empty")) bitmask = 0;
			else {
				int num = Integer.parseInt(st.nextToken());
				if(str.equals("add")) bitmask |=(1 << num);
				else if(str.equals("remove")) bitmask &= ~(1 << num);
				else if(str.equals("check")) {
					if((bitmask & (1 << num))==0) sb.append("0\n");
					else sb.append("1\n");
				}else if(str.equals("toggle")) bitmask ^= (1 << num);
			}
		}//tc
		System.out.println(sb.toString());
		
	}//main
}//class
```
- 비트마스크 연산을 이용하여 구현.
