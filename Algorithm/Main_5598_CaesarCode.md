# 알고리즘
[백준 5598번:카이사르 암호](https://www.acmicpc.net/problem/5598)
```java
package charcter_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main_5598_CaesarCode {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		int temp = 0;
		for (int i = 0; i < str.length(); i++) {
			temp = str.charAt(i);
			if(temp>67) System.out.print((char)(temp-3));
			else System.out.print((char)(temp+23));
		}
		
	}//main

}//class

```
- 문자열 처리 문제.
