# 알고리즘
[백준 1158번:요세푸스 문제](https://www.acmicpc.net/problem/1158)
```java
package queue_deque_;

import java.io.*;
import java.util.*;

public class Main_1158_Yosepuse {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int K = Integer.parseInt(st.nextToken());
		Queue <Integer> queue = new LinkedList<>();
		
		for (int i = 1; i <= N; i++) {
			queue.offer(i);
		}
		System.out.print("<");
		while(!queue.isEmpty()) {
			for (int i = 0; i < K-1; i++) {
				int temp = queue.poll();
				queue.offer(temp);
			}
			if(queue.size()==1) break;
			System.out.print(queue.poll()+", ");
		}
		System.out.print(queue.poll());
		System.out.println(">");
		
	}//main

}//class

```
- Queue로 문제 해결.
