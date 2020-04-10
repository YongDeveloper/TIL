# 알고리즘
[백준 1543번:문서 검색](https://www.acmicpc.net/problem/1543)
```java
package charcter_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main_1543_DocuSearch {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String Docu = br.readLine();
		String index = br.readLine();
		int cnt = 0;
		for (int i = 0; i <= Docu.length()-index.length(); i++) {
			String temp = Docu.substring(i, i+index.length());
			if(temp.equals(index)) {
				cnt++; 
				i += index.length()-1;
			}
		}
		System.out.println(cnt);
	}//main

}//class

```
- 문자열 처리 문제
- substring을 이용하여 구현.
