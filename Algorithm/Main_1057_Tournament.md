# 알고리즘
[백준 1057번:토너먼트](https://www.acmicpc.net/problem/1057)
```java
package simulation_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_1057_Tournament {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int Kim = Integer.parseInt(st.nextToken());
		int Lim = Integer.parseInt(st.nextToken());
		int round = 0;
		
		while(Kim!=Lim) {
			round++;
			if(Kim%2==0) Kim /=2;
			else if(Kim%2==1) Kim = (Kim+1)/2; 
			if(Lim%2==0) Lim /=2;
			else if(Lim%2==1) Lim = (Lim+1)/2; 
		}
		
		System.out.println(round);
	}//main
	

}//class

```
- 시뮬레이션 문제
- 모든 사람의 경우를 고려하지 않고 Kim 과 Lim 의 경우만을 생각하여 구현.
