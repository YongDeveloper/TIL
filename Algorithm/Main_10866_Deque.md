# 알고리즘

[백준 10866번: 덱](https://www.acmicpc.net/problem/10866)

```java
public class Main_10866_Deque {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int TC = Integer.parseInt(st.nextToken());
		Deque<Integer> deque = new LinkedList<>();
		
		for (int tc = 1; tc <= TC; tc++) {
			
			st = new StringTokenizer(br.readLine());
			String str = st.nextToken();
			
			if(str.contains("push_front")) {
				int temp = Integer.parseInt(st.nextToken());
				deque.offerFirst(temp);
			}else if(str.contains("push_back")) {
				int temp = Integer.parseInt(st.nextToken());
				deque.offerLast(temp);
			}else if(str.equals("pop_front")) {
				if(deque.isEmpty()) System.out.println("-1");
				else System.out.println(deque.pollFirst());
			}else if(str.equals("pop_back")) {
				if(deque.isEmpty()) System.out.println("-1");
				else System.out.println(deque.pollLast());
			}else if(str.equals("size")) {
				System.out.println(deque.size());
			}else if(str.equals("empty")) {
				if(deque.isEmpty()) System.out.println("1");
				else System.out.println("0");
			}else if(str.equals("front")) {
				if(deque.isEmpty()) System.out.println("-1");
				else System.out.println(deque.peekFirst());
			}else if(str.equals("back")) {
				if(deque.isEmpty()) System.out.println("-1");
				else System.out.println(deque.peekLast());
			}
			
		}//tc
		
	}//main

}//class



```

- Deque를 이용하여 구현
