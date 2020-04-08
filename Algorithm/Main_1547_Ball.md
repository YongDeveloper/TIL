# 알고리즘
[백준 1547번:공](https://www.acmicpc.net/problem/1547)
```java
public class Main_1547_Ball {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int check = 1;
		int [][] map = new int [N][2];
		
		for (int i = 0; i < map.length; i++) {
			st = new StringTokenizer(br.readLine());
			for (int j = 0; j < map[i].length; j++) {
				map[i][j] = Integer.parseInt(st.nextToken());
			}
		}
		
		for (int i = 0; i < map.length; i++) {
			if(map[i][0]!=check && map[i][1]!=check) continue;
			else if(map[i][0]==check && map[i][1]==check) check = -1;
			else {
				if(map[i][0]==check) check = map[i][1];
				else check = map[i][0];
			}
		}
		System.out.println(check);
	}//main

}//class

```
- 시뮬레이션 문제
- 이차원 배열을 이용하여 조건문을 이용해 구현.
