# 알고리즘
[백준 10808번:알파벳 개수](https://www.acmicpc.net/problem/10808)
```java
package simulation_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main_10808_AlpabetNum {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		int [] index = new int [26];
		for (int i = 0; i < str.length(); i++) {
			index[str.charAt(i)-97]++;
		}
		for (int i = 0; i < index.length; i++) {
			System.out.print(index[i]+" ");
		}
		
	}//main

}//class

```
- 문자열 처리 문제
- 카운팅 정렬을 이용하여 구현
- 소문자에서 숫자로 표현하기 위해 아스키코드를 이용하여 처리
