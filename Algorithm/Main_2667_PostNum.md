# 알고리즘

[백준 2667번:단지번호붙이기](https://www.acmicpc.net/problem/2667)

```java
public class Main_2667_PostNum {
		
	private static int N;
	private static int cnt;
	private static int [][] map;
	private static boolean [][] visited;
	private static int [] dx = {0,0,-1,1};
	private static int [] dy = {1,-1,0,0};
	private static ArrayList<Integer> list = new ArrayList<>(); 
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		map = new int [N][N];
		visited = new boolean [N][N];
		
		for (int i = 0; i < N; i++) {
			String [] str = br.readLine().split("");
			for (int j = 0; j < N; j++) {
				map[i][j] = str[j].charAt(0)-'0';
				//System.out.print(map[i][j]+" ");
			}
			//System.out.println();
		}
		
		
		for (int i = 0; i < N; i++) {
			for (int j = 0; j < N; j++) {
				if(map[i][j]==1 && !visited[i][j]) {
					cnt = 1;
					DFS(i,j);
					list.add(cnt);
				}
			}
		}
		
		Collections.sort(list); // 리스트 오름차순 정렬
		System.out.println(list.size()); // 전체 리스트 갯수
		
		for (int i = 0; i < list.size(); i++) {
			System.out.println(list.get(i));
		} // 출력
			
		
	}//main

	public static int DFS(int y, int x) {
		visited[y][x] = true;
		for (int i = 0; i < 4; i++) {
			int ny = y + dy[i];
			int nx = x + dx[i];
			
			if(ny>=0 && nx>=0 && ny<N && nx<N) {
				if(map[ny][nx]==1 && !visited[ny][nx]) {
					DFS(ny,nx);
					cnt++;
				}
			}	
		}
		
		return cnt;
		
	}//DFS
	
}//class

```
- DFS (사방탐색 방법 + 재귀) 를 이용하였다.
- visited를 전역변수로 설정하여, 입력변수를 줄였다
- DFS 클래스에서 먼저 visited = true 한후 사방탐색한다. 조건문을 넣고 다시 재귀를 돌린다.
- ArrayList를 이용하여 각 영역별 크기를 담았다. 

