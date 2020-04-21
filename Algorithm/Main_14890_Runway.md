# 알고리즘
[백준 14890번:경사로](https://www.acmicpc.net/problem/14890)
```java
package simulation_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_14890_Runway {

	private static int N;
	private static int L;
	private static int[][] map;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		L = Integer.parseInt(st.nextToken());
		map = new int [N][N];
		
		for (int i = 0; i < N; i++) {
			st = new StringTokenizer(br.readLine());
			for (int j = 0; j < N; j++) {
				map[i][j] = Integer.parseInt(st.nextToken());
			}
		}
		
		int result = 0;
		for (int i = 0; i < N; i++) {
			if(Check(i,0,false)) result++;
			if(Check(0,i,true)) result++;
		}
		
		System.out.println(result);
		
	}//main
		public static boolean Check(int y, int x, boolean flag) {
			int [] height = new int [N];
			boolean [] visited = new boolean [N];
			for (int i = 0; i < N; i++) {
				if(!flag) height[i] = map[y][i];
				else height[i] = map[i][x];
			}
			
			for (int i = 0; i < height.length-1; i++) {
				
				if(height[i] == height[i+1]) continue;
				if(Math.abs(height[i+1]-height[i])>1) return false;
				
				if(Math.abs(height[i+1]-height[i])==1) {
					if(height[i+1] < height[i]) { // 내리막길
						for (int j = i+1; j <= i+L; j++) {
							if(j>=N || visited[j] || height[i+1]!=height[j]) return false;
							else visited[j] = true;
						}
					}	
					
					else if(height[i+1] > height[i]){ // 오르막길
						for (int j = i; j >= i-L+1; j--) {
							if(j<0 || visited[j] || height[i]!=height[j]) return false;
							else visited[j] = true;
						}
					}
				}
			}
			return true;
		}
}//class

```
- 시뮬레이션 문제.
