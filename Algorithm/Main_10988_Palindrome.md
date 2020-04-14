# 알고리즘
[백준 10988번:팰린드롬인지 확인하기](https://www.acmicpc.net/problem/10988)
```java
package charcter_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main_10988_Palindrome {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		int cnt = 0;
		for (int i = 0; i < str.length()/2; i++) {
			if(str.charAt(i)==str.charAt(str.length()-i-1)) cnt++;
		}
		if(cnt==str.length()/2) System.out.println(1);
		else System.out.println(0);
		
	}//main

}//class

```
- 문자열 처리 문제.
