# 알고리즘
[백준 3986번:좋은 단어](https://www.acmicpc.net/problem/3986)
```java
package charcter_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Stack;

public class Main_3986_GoodWord {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int TC = Integer.parseInt(br.readLine());
		int cnt = 0;
		for (int tc = 1; tc <= TC; tc++) {
			Stack<String> stack = new Stack<>();
			String [] str = br.readLine().split("");
			for (int i = 0; i < str.length; i++) {
				if(stack.isEmpty()) stack.push(str[i]);
				else {
					if(stack.peek().equals(str[i])) stack.pop();
					else stack.push(str[i]);
				}
			}
			if(stack.isEmpty()) cnt++;
		}//TC
		System.out.println(cnt);
	}//main
}//class

```
- 문자열 처리 문제
- 처음에는 String API을 이용하여 substring 처리해 주려고했으나 다시 생각했다.
- stack 문제인지 몰랐고 stack문제인걸 깨달은 후 바로 구현.
