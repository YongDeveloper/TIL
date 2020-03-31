# 알고리즘

[백준 11866번: 요세푸스문제0](https://www.acmicpc.net/problem/11866)

```java
public class Main_11866_Yosepuse {

	private static int K, N;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		K = Integer.parseInt(st.nextToken());
		
		QUE();
		
	}//main
	public static void QUE() {
		
		Deque<Integer> deque = new LinkedList<>();
		int cnt = 0;
		int temp = 0;
		int [] arr = new int [N];
		
		for (int i = 1; i <= N; i++) {
			deque.offerLast(i);
		}
		while(cnt<N) {
			for (int i = 0; i < K; i++) {
				deque.offerLast(deque.pollFirst());
			}
			//System.out.print(deque.peekLast()+ " ");
			arr[cnt++]=deque.peekLast();
			deque.pollLast();
		}//while

		System.out.print("<");
		for (int i = 0; i < arr.length-1; i++) {
			System.out.print(arr[i]+", ");
		}
		System.out.println(arr[arr.length-1]+">");
	}//Queue
	
}//class

```

- Deque를 이용하여 문제를 해결
