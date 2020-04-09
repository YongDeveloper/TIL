# 알고리즘
[백준 2998번:8진수](https://www.acmicpc.net/problem/2998)
```java
package charcter_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main_2998_OctalNum {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		String [] index = {"000","001","010","011","100","101","110","111"};
		if(str.length()%3==1) str = "00"+str;
		else if(str.length()%3==2) str = "0"+str;

		for (int i = 0; i < str.length()/3; i++) {
			for (int j = 0; j < index.length; j++) {
				if(str.substring(i*3, i*3+3).equals(index[j])) {
					System.out.print(j);
					continue;
				}
			}
		}
		
	}//main

}//class

```
- 문자열 처리 문제
- substring을 이용하여 문자열을 비교하였다.
