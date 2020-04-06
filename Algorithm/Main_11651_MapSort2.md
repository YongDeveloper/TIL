# 알고리즘
[백준 11651번:좌표 정렬하기2](https://www.acmicpc.net/problem/11651)
```java
public class Main_11651_MapSort2 {

	public static class Map implements Comparable<Map>{

		int x;
		int y;
		
		public Map(int x, int y) {
			this.x = x;
			this.y = y;
		}

		public int getX() {
			return x;
		}

		public int getY() {
			return y;
		}

		@Override
		public int compareTo(Map o) {
			if(this.y > o.y) return 1;
			else if(this.y < o.y ) return -1;
			else return Integer.compare(this.x, o.x);
		}
		
	}
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		List<Map> list = new ArrayList<>();
		
		for (int i = 0; i < N; i++) {
			st = new StringTokenizer(br.readLine());
			list.add(new Map(Integer.parseInt(st.nextToken()),
					Integer.parseInt(st.nextToken())));
		}
		
		Collections.sort(list);
		
		for (Map map : list) {
			System.out.println(map.x+" "+map.y);
		}
		
		
	}//main

}//class
```
- 좌표 정렬하기1 문제와 같은 방법으로 구현.
- Class를 생성하여 좌표 x,y를 담고 클래스 내부에서 정렬조건을 추가하였다.
