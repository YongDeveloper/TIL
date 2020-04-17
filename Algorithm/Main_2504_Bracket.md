# 알고리즘
[백준 2504번:괄호의 값](https://www.acmicpc.net/problem/2504)
```java
package stack_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Stack;

public class Main_2504_Bracket {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		Stack<Character> stack = new Stack<>();
		int sum = 0; int multi = 1;
		
		for (int i = 0; i < str.length(); i++) {
			switch (str.charAt(i)) {
			case '(':
				stack.push(str.charAt(i));
				multi *= 2;
				break;
			case ')':
				if(stack.isEmpty() || stack.peek()!='(') {
					sum = 0;
					break;
				}
				if(str.charAt(i-1)== '(') sum += multi;
				stack.pop();
				multi /= 2;
				break;
			case '[':
				stack.push(str.charAt(i));
				multi *= 3;
				break;
			case ']':
				if(stack.isEmpty() || stack.peek()!='[') {
					sum = 0;
					break;
				}
				if(str.charAt(i-1)== '[') sum += multi;
				stack.pop();
				multi /= 3;
				break;
			}
		}
		if(stack.isEmpty()) System.out.println(sum);
		else System.out.println(0);
	}//main

}//class

```
- 시뮬레이션 문제.
