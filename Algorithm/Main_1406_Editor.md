# 알고리즘
[백준 1406번:에디터](https://www.acmicpc.net/problem/1406)
```java
package queue_deque_;

import java.io.*;
import java.util.*;

public class Main_1406_Editor {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		int N = Integer.parseInt(br.readLine());
		Stack<Character> left = new Stack<>();
		Stack<Character> right = new Stack<>();
		
		for (int i = 0; i < str.length(); i++) {
			left.push(str.charAt(i));
		}
		
		for (int i = 0; i < N; i++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			char ch = st.nextToken().charAt(0);
			if(ch=='L') {
				if(!left.isEmpty()) right.push(left.pop());
			}else if(ch=='D') {
				if(!right.isEmpty()) left.push(right.pop());
			}else if(ch=='B') {
				if(!left.isEmpty()) left.pop();
			}else if(ch=='P') {
				char c = st.nextToken().charAt(0);
				left.push(c);
			}
		}
		while(!left.isEmpty()) {
			right.push(left.pop());
		}
		while(!right.isEmpty()) {
			System.out.print(right.pop());
		}
		
	}//main
}//class
```
- Stack 문제.
