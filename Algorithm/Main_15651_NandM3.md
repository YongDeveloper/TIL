# 알고리즘
[백준 15651번: N과 M](https://www.acmicpc.net/problem/15651)

```java
public class Main_15651_NandM3 {
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
		Perm(0);
		System.out.println(sb);
		
	}//main
	
	public static void Perm(int cnt) {
		if(cnt==R) {
			for (int i = 0; i < R; i++) {
				sb.append(arr[i]+" ");
			}
			sb.append("\n");
		}else {
			for (int i = 1; i <= N; i++) {
				arr[cnt] = i;
				Perm(cnt+1);
			}
		}
	}//Perm
}//class
```
- 백준 15649번과 비교했을때 코드가 달라진것이 거의 없다.
- 이번 문제는 숫자를 뽑을때 중복을 허용한다는 점이다.
- 그러므로 Perm 메서드 안에 visited를 해줄 필요가 없다.

