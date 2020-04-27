# 알고리즘
[백준 17413번:단어 뒤집기2](https://www.acmicpc.net/problem/17413)

```java
package stack_;

import java.io.*;
import java.util.*;

public class Main_17413_WordReverse2 {

	public static Stack<Character> stack = new Stack<>();
	public static Queue<Character> queue = new LinkedList<>();
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine(); 
		boolean check = false;
		
		for (int i = 0; i < str.length(); i++) {
			if(str.charAt(i)=='<') {
				StackPrint();
				System.out.print("<");
				check = true;
				continue;
			}
			else if(str.charAt(i)=='>') {
				QueuePrint();
				System.out.print(">");
				check = false;
				continue;
			}
			if(!check) {
				if(i==str.length()-1) {
					stack.push(str.charAt(i));
					StackPrint();
				}
				if(str.charAt(i)!=' ') stack.push(str.charAt(i));
				if(str.charAt(i)==' ') {
					StackPrint();
					System.out.print(" ");
				}
			}else {
				if(str.charAt(i)!=' ') queue.offer(str.charAt(i));
				if(str.charAt(i)==' ') {
					QueuePrint();
					System.out.print(" ");
				}
			}
		}
		
	}//main
	public static void StackPrint() {
		while(!stack.isEmpty()) {
			System.out.print(stack.pop());
		}
	}
	
	public static void QueuePrint() {
		while(!queue.isEmpty()) {
			System.out.print(queue.poll());
		}
	}

}//class

```
- Stack과 Queue를 적절히 이용하여 구현.
