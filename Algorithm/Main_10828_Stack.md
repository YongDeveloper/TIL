# 알고리즘

[백준 10828번: 스택](https://www.acmicpc.net/problem/10828)

```java
public class Main_10828_Stack {

	public static void main(String[] args) throws NumberFormatException, IOException {

		Stack<Integer> stack = new Stack <Integer>();
		
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int TC = Integer.parseInt(st.nextToken());
		
		for (int tc = 1; tc <= TC; tc++) {
			st = new StringTokenizer(br.readLine());
			String str = st.nextToken();
			if(str.contains("push")) {
				int num = Integer.parseInt(st.nextToken());
				stack.push(num);
			}
			
			else if(str.equals("pop")) {
				if(stack.isEmpty()) System.out.println(-1);
				else {
					int num = stack.pop();
					System.out.println(num);
				}
			}
			
			else if(str.equals("top")) {
				if(stack.isEmpty()) System.out.println(-1);
				else {
					int top = stack.pop();
					System.out.println(top);
					stack.push(top);
				}
			}
			
			else if(str.equals("size")) {
				System.out.println(stack.size());
			}
			
			else if(str.equals("empty")) {
				if(stack.isEmpty()) System.out.println(1);
				else System.out.println(0);
			}
			
		}//tc
		
	}//main

}//class

```

- 스택의 기본을 물어보는 문제
- JAVA API를 이용하여 문제를 해결.
