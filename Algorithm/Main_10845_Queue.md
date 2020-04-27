# 알고리즘
[백준 10845번:큐](https://www.acmicpc.net/problem/10845)
```java
package queue_deque_;

import java.io.*;
import java.util.*;

public class Main_10845_Queue {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int TC = Integer.parseInt(st.nextToken());
		Queue <Integer> queue = new LinkedList<>();
		int N = 0;
		
		for (int tc = 1 ; tc <= TC; tc++) {
			st = new StringTokenizer(br.readLine());
			String str = st.nextToken();
			if(str.equals("push")) {
				N = Integer.parseInt(st.nextToken());
				queue.offer(N);
			}else if(str.equals("front")) {
				if(queue.isEmpty()) System.out.println("-1");
				else System.out.println(queue.peek());
			}else if(str.equals("back")) {
				if(queue.isEmpty()) System.out.println("-1");
				else System.out.println(N);
			}else if(str.equals("size")) {
				System.out.println(queue.size());
			}else if(str.equals("empty")) {
				if(queue.isEmpty()) System.out.println("1");
				else System.out.println("0");
			}else if(str.equals("pop")) {
				if(!queue.isEmpty()) {
					int temp = queue.poll();
					System.out.println(temp);
				}else System.out.println("-1");
			}
		}
	}//main
}//class

```
- Queue로 구현.
