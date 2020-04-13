# 알고리즘
[백준 2902번:KMP는 왜 KMP일까?](https://www.acmicpc.net/problem/2902)
```java
package charcter_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main_2903_KMP {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		System.out.print(str.charAt(0));
		for (int i = 0; i < str.length(); i++) {
			if(str.charAt(i)=='-') System.out.print(str.charAt(i+1));
		}
		
	}//main

}//class

```
- 문자열 처리 문제
