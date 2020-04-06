# 알고리즘
[백준 11650번:좌표 정렬하기](https://www.acmicpc.net/problem/11650)

```java
public class Main_11650_MapSort {

	public static class Map implements Comparable <Map>{

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
			if(this.x > o.x) return 1;
			else if(this.x < o.x) return -1;
			else {
				if(this.y > o.y) return 1;
				else if(this.y < o.y) return -1;
				else return 0;
			}
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

- List에 좌표 x,y값을 Map Class에 담아서 정렬.
- 정렬 조건을 Map Class 내부에 설정해주어 구현.
