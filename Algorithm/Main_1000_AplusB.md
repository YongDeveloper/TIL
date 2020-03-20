# 알고리즘
[백준 1000번: A+B ](https://www.acmicpc.net/problem/1000)

```java
package step1;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_1000_AplusB {

	public static void main(String[] args) throws IOException {
  
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in)); // 입력
		StringTokenizer st = new StringTokenizer(br.readLine()); // Stringtokenizer로 받아준다 
		int num1 = Integer.parseInt(st.nextToken()); // String을 숫자로 바꾸기 위해 Interger.parserInt
		int num2 = Integer.parseInt(st.nextToken()); // st.nextToken()을 이용
		System.out.println(num1+num2);
	}//main
}//class


```

