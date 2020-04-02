# 알고리즘
[백준 15652번:N과 M (4)](https://www.acmicpc.net/problem/15652)

```java
public class Main_15652_NandM4 {
	public static int [] arr;
	public static StringBuilder sb = new StringBuilder();
	private static int N;
	private static int R;
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		R = Integer.parseInt(st.nextToken());
		arr = new int [N+1];
		Perm(0,0);
		System.out.println(sb);
		
	}//main
	
	public static void Perm(int pre, int cnt) {
		if(cnt==R) {
			for (int i = 0; i < R; i++) {
				sb.append(arr[i]+" ");
			}
			sb.append("\n");
		}else {
			for (int i = 1; i <= N; i++) {
				if(i>=pre) {
					arr[cnt] = i;
					Perm(arr[cnt],cnt+1);
				}
			}
		}
	}//Perm
}//class

```

- 비내림차순 순열이므로 이전 수와 비교하기 위해 prev 변수를 설정
- 같은 수 중복을 허용하므로 visited 필요 없다.
