# 알고리즘

[백준 4949번:균형잡힌 세상](https://www.acmicpc.net/problem/4949)

```java

public class Main_4949_BalenceWorld {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		while(true) {
			String str = br.readLine();
			Stack<Character> stack = new Stack<Character>();
			
			if(str.equals(".")) break;
			
			for (int i = 0; i < str.length(); i++) {
				char c = str.charAt(i);
				
				if(c=='(' || c=='[') stack.push(c);
				else if(c==')' || c==']') {
					if(stack.isEmpty() || 
						(stack.peek()=='(' && c==']') || 
						(stack.peek()=='[' && c==')')) {
						
						stack.push(c);
						break;
					}
					stack.pop();
				}
				
			}
			
			if(stack.isEmpty()) System.out.println("yes");
			else System.out.println("no");
			
		}//while
		
	}//main

}//class

```

- stack을 이용.
- ( 혹은 [ 가 들어오면 바로 스택에 넣는다.
- 스택이 비어있는데 닫는 괄호가 들어오거나, [ -> ) 혹은 ( -> ] 들어오면 반복문을 중단.


