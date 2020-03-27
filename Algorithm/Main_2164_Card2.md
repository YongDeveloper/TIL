# 알고리즘

[백준 2164번:카드2]()

```java
public class Main_2164_Card2 {

	public static void main(String[] args) throws IOException {

		Deque <Integer> deque = new LinkedList<Integer>();
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int num = Integer.parseInt(st.nextToken());
		int temp = 0;
		for (int i = num; i > 0 ; i--) {
			deque.offerLast(i);
		}// queue input
		while(true) {
			if(deque.size()>1) {
				deque.pollLast();
			}// top -> poll 시키기
			if(deque.size()==1) break;
			if(deque.size()>1) {
				temp = deque.pollLast();
				deque.offerFirst(temp);
			}// top -> bottom
		}
		System.out.println(deque.poll());
	}//main

}//class

```
### Deque(Double-Ended Queue)
- deque.offerLast();
- deque.pollLast();
- deque.offerFirst();
- deque.pollLast();
- Deque는 앞 뒤로 추가/삭제를 할 수 있다.
- Deque를 이용하여 문제를 해결.


#### 200327
