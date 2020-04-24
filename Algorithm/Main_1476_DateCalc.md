# 알고리즘
[백준 1476번:날짜 계산](https://www.acmicpc.net/problem/1476)
```java
package samsung_;

import java.io.*;
import java.util.*;

public class Main_1476_DateCalc {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int E = Integer.parseInt(st.nextToken());
		int S = Integer.parseInt(st.nextToken());
		int M = Integer.parseInt(st.nextToken());
		int Earth = 0; int Sun = 0; int Moon = 0;
		int cnt = 0;
		while(true) {
			cnt++; Earth++; Sun++; Moon++;
			if(Earth>=16) Earth-=15;
			if(Sun>=29) Sun-=28;
			if(Moon>=20) Moon-=19;
			if(E==Earth && S==Sun && M==Moon) break;
		}
		System.out.println(cnt);
	}//main

}//class

```
- bruteforce 문제.
