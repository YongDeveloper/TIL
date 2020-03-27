# 알고리즘
[백준 18258번:큐2](https://www.acmicpc.net/problem/18258)

```java
public class Main_18258_Queue2 {

	public static void main(String[] args) throws IOException {

		Queue<Integer> queue = new LinkedList<>();
		
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int TC = Integer.parseInt(st.nextToken());
		int num = 0;
		
		for (int tc = 1; tc <= TC; tc++) {
			
			st = new StringTokenizer(br.readLine());
			String str = st.nextToken();
			
			if(str.contains("push")) {
				num = Integer.parseInt(st.nextToken());
				queue.offer(num);
				
			}else if(str.equals("pop")) {
				if(queue.isEmpty()) bw.write(-1+"\n");
				else bw.write(queue.poll()+"\n");
				
			}else if(str.equals("size")) {
				bw.write(queue.size()+"\n");
				
			}else if(str.equals("empty")) {
				if(queue.isEmpty()) bw.write(1+"\n");
				else bw.write(0+"\n");
				
			}else if(str.equals("front")){
				if(queue.isEmpty()) bw.write(-1+"\n");
				else bw.write(queue.peek()+"\n");
				
			}else if(str.equals("back")) {
				if(queue.isEmpty()) bw.write(-1+"\n");
				else bw.write(num+"\n");
				
			}
			
		}//tc
		bw.flush();
		bw.close();
		
	}//main

}//class
```
- 큐에 넣기 : queue.offer();
- 큐에 있는것 빼기 (가장 먼저 넣은 것) : queue.poll();
- 큐 크기 확인 : queue.size();
- 큐 맨 앞 확인 : queue.peek(); (peek();는 큐에 있는것을 빼지 않는다)
- 큐 맨 뒤 확인 : 따로 API는 없지만 최근에 넣은것을 변수로 사용.
- 시간초과로 인해 출력을 System.out대신 bufferedWriter를 이용.


