# 알고리즘
[백준 1526번:가장 큰 금민수](https://www.acmicpc.net/problem/1526)
```java
package simulation_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main_1526_BigMinsu {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String strN = br.readLine();
		int N = Integer.parseInt(strN);
		while(true) {
			int cnt = 0;
			for (int i = 0; i < strN.length(); i++) {
				if(strN.charAt(i)=='4' || strN.charAt(i)=='7') cnt++;
			}
			if(cnt==strN.length()) break;
			else {
				N = Integer.parseInt(strN) -1 ;
				strN = Integer.toString(N);
			}
		}
		System.out.println(strN);
		
	}//main

}//class
```
- 시뮬레이션 문제
- 입력된 수부터 1씩 감소시키면서 
- 4또는 7의 숫자가 있는 지를 비교하여 모두 있으면 출력
