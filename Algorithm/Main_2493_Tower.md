# 알고리즘
[백준 2493번:탑](https://www.acmicpc.net/problem/2493)
```java
package stack_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Stack;
import java.util.StringTokenizer;

public class Main_2493_Tower {

	public static class Tower{
		Long high;
		int index;
		
		public Tower(Long high, int index) {
			this.high = high;
			this.index = index;
		}
	}
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		Stack<Tower> stack = new Stack<>();
		
		StringTokenizer st = new StringTokenizer(br.readLine());
		for (int i = 1; i <= N; i++) {
			Long h = Long.parseLong(st.nextToken());
			while(!stack.isEmpty()) {
				if(stack.peek().high >= h) {
					System.out.print(stack.peek().index+" ");
					break;
				}
				stack.pop();
			}
			if(stack.isEmpty()) System.out.print(0+" ");
			stack.push(new Tower(h,i));
		}
		
	}//main

}//class
```
- Stack 을 이용한 문제.
