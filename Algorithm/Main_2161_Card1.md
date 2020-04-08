# 알고리즘
[백준 2161번:카드1](https://www.acmicpc.net/problem/2161)
```java
public class Main_2161_Card1 {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		int temp = 0;
		Queue<Integer> queue = new LinkedList<>();
		
		for (int i = 1; i <= N; i++) {
			queue.offer(i);
		}

		while(true) {
			System.out.print(queue.poll()+" ");
			if(!queue.isEmpty()) {
				temp = queue.poll();
				queue.offer(temp);
			}else break;
		}
		
	}//main

}//class

```
- 시뮬레이션 문제이지만 Queue를 이용하여 구현.
