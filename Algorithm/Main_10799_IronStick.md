# 알고리즘
[백준 10799번:쇠막대기](https://www.acmicpc.net/problem/10799)
```java
package stack_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Stack;

public class Main_10799_IronStick {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		Stack<Character> stack = new Stack<>();
		int cnt = 0;
		for (int i = 0; i < str.length(); i++) {
			if(str.charAt(i)=='(') {
				stack.push(str.charAt(i));
			}else if(str.charAt(i-1)=='(' && str.charAt(i)==')') {
				stack.pop();
				cnt += stack.size();
			}else if(str.charAt(i-1)==')' && str.charAt(i)==')') {
				cnt++;
				stack.pop();
			}
		}
		System.out.println(cnt);
		
	}//main

}//class

```
- 스택 문제
