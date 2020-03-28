# 알고리즘

[백준 2447번:별 찍기 10](https://www.acmicpc.net/problem/2447)

```java
public class Main_2447_Star10 {
	
	public static char [][] map;
	
	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		map = new char [N][N];
		
		for (int i = 0; i < N; i++) {
			Arrays.fill(map[i], ' ');
		}
		
		Star(0,0,N);
		for (int i = 0; i < N; i++) {
			System.out.println(map[i]);
		}
		
		
	}//main

	public static void Star(int y, int x, int N) {
		
		if(N==1) {
			map[y][x]='*';
			return;
		}
		int k = N/3;
		for (int i = 0; i < 3; i++) {
			for (int j = 0; j < 3; j++) {
				if(i==1 && j==1) continue;
				Star(y+ k*i, x+k*j, k);
			}
		}
		
	}//star
	
}//class

```

- 모든 ' '을 채울때 Arrays.fill(map[i], ' ' )를 이용
- 재귀를 이용.
