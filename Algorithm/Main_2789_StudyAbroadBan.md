# 알고리즘
[백준 2789:유학 금지](https://www.acmicpc.net/problem/2789)
```java
package for_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main_2789_StudyAbroadBan {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		char [] index = {'C','A','M','B','R','I','D','G','E'};
		boolean check = false;
		for (int i = 0; i < str.length(); i++) {
			check = false;
			for (int j = 0; j < index.length; j++) {
				if(str.charAt(i)==index[j]) {
					check = true;
					break;
				}
			}
			if(!check)System.out.print(str.charAt(i));
		}
	}//main

}//class

```
- 단순한 반복문 문제. 
