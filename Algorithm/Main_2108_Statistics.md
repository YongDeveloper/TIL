# 알고리즘
[백준 2108번:통계학](https://www.acmicpc.net/problem/2108)
```java
public class Main_2108_Statistics {

	private static int[] arr;
	private static int N;

	public static class Mode implements Comparable<Mode>{

		int num;
		int cnt;

		public Mode(int num, int cnt) {
			super();
			this.num = num;
			this.cnt = cnt;
		}

		public int getNum() {
			return num;
		}

		public int getCnt() {
			return cnt;
		}

		@Override
		public int compareTo(Mode o) {
			if(this.cnt > o.cnt) return -1;
			else if(this.cnt < o.cnt) return 1;
			else return Integer.compare(this.num, o.num);
		}
		
	}
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		N = Integer.parseInt(br.readLine());
		arr = new int [N];
		for (int i = 0; i < N; i++) {
			arr[i] = Integer.parseInt(br.readLine());
		}
		
		if(N==1) {
			System.out.println(arr[0]);
			System.out.println(arr[0]);
			System.out.println(arr[0]);
			System.out.println(0);
		}else {
			Avg();
			Middle();
			Mode();
			Range();
		}
		
	}//main

	public static void Avg() {
		double sum = 0;
		
		for (int i = 0; i < N; i++) {
			sum += arr[i];
		}
		System.out.println(Math.round(sum/N));
	}
	
	public static void Middle() {
		List<Integer> list = new ArrayList<>();
		for (int i = 0; i < N; i++) {
			list.add(arr[i]);
		}
		Collections.sort(list);
		System.out.println(list.get(N/2));
	}
	
	public static void Mode() {
		Arrays.sort(arr);
		List<Mode> list = new ArrayList<>();
		int now = 0;
		int prev = 0;
		int cnt = 1;
		
		for (int i = 1; i < N; i++) {
			now = arr[i];
			prev = arr[i-1];
			
			if(now == prev) cnt++;
			else {
				list.add(new Mode(prev,cnt));
				cnt = 1;
			}
			if(i == N-1) list.add(new Mode(now,cnt));
		}
		
		Collections.sort(list);
		
		if(list.get(0).cnt > list.get(1).cnt) System.out.println(list.get(0).num);
		else System.out.println(list.get(1).num);
		
	}//Mode
	
	public static void Range() {
		List<Integer> list = new ArrayList<>();
		for (int i = 0; i < N; i++) {
			list.add(arr[i]);
		}
		Collections.sort(list);
		System.out.println(list.get(N-1)-list.get(0));
	}
}//class

```
- 평균값, 중간값, 최빈값, 범위에 대한 메서드를 따로 구현하였다.
- 최빈값을 정렬하기 위해 Mode class를 생성해, Num에 대한 cnt를 정렬하였다.
