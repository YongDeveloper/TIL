# 알고리즘
[백준 10987번: 모음의 개수](https://www.acmicpc.net/problem/10987)
```java
package charcter_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main_10987_aeiou {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		char [] index = {'a','e','i','o','u'};
		int cnt = 0;
		
		for (int i = 0; i < str.length(); i++) {
			for (int j = 0; j < index.length; j++) {
				if(str.charAt(i)==index[j]) {
					cnt++;
					break;
				}
			}
		}
		System.out.println(cnt);
		
	}//main

}//class

```
- 문자열 처리 문제.
