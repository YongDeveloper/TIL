# 알고리즘
[백준 5586번: JOI와 IOI](https://www.acmicpc.net/problem/5586)
```java
package charcter_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main_5586_JOI {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		int cntJ = 0;
		int cntI = 0;
		for (int i = 0; i < str.length()-2; i++) {
			if(str.charAt(i)=='J') {
				if(str.substring(i, i+3).equals("JOI")) cntJ++;
			}
			else if(str.charAt(i)=='I') {
				if(str.substring(i, i+3).equals("IOI")) cntI++;
			}
		}
		
		System.out.println(cntJ);
		System.out.println(cntI);
		
	}//main

}//class

```
- 문자열 처리 문제.
