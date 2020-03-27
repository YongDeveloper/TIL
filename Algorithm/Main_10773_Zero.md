# 알고리즘

[백준 10773번: 제로](https://www.acmicpc.net/problem/10773)

```java
public class Main_10773_Zero {

	public static void main(String[] args) throws IOException {

		Stack<Integer> stack = new Stack<>();
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int TC = Integer.parseInt(st.nextToken());
		int sum = 0;
		
		for (int tc = 1; tc <= TC; tc++) {
			st = new StringTokenizer(br.readLine());
			int num = Integer.parseInt(st.nextToken());
			if(num!=0) 	stack.push(num);
			else stack.pop();
			
		}//tc
		
		int size = stack.size();
		for (int i = 0; i < size; i++) {
			sum += stack.pop();
		}
		System.out.println(sum);
		
	}//main

}//class

```
- 다른 알고리즘 방법도 있지만 stack을 이용하여 문제를 해결하였다.
- 마지막에 스택에 넣어놓은 수들을 모두 빼내면서 합계를 더할때 
  stack.size()가 감소하므로 처음에 size 변수로 고정시켰다.
