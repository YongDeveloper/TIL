# 알고리즘
[백준 7785번:회사에 있는 사람](https://www.acmicpc.net/problem/7785)
```java
package datastructure_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.Collections;
import java.util.Stack;
import java.util.StringTokenizer;

public class Main_7785_WhoIsInOffice {

	public static class Member implements Comparable<Member>{

		String name;
		String state;
		
		public Member(String name, String state) {
			this.name = name;
			this.state = state;
		}
		
		public String getName() {
			return name;
		}


		public String getState() {
			return state;
		}


		@Override
		public int compareTo(Member o) {
			return o.name.compareTo(this.name);
		}
		
	}
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		ArrayList<Member> list = new ArrayList<>();
		Stack<Integer> stack = new Stack<>();
		
		for (int i = 0; i < N; i++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			list.add(new Member(st.nextToken(), st.nextToken()));
		}

		Collections.sort(list);
		
		for (int i = 0; i < N; i++) {
			if(list.get(i).state.equals("leave")) {
				stack.push(i-1);
			}
		}
		while(!stack.isEmpty()) {
			int temp = stack.pop();
			list.remove(temp);
		}
		
		for (Member member : list) {
			if(member.state.equals("enter")) {
				System.out.println(member.name);
			}
		}
		
	}//main

}//class

```
- 자료구조 문제
- Arraylist와 stack을 이용하여 구현.
