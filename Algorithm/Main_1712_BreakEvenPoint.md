# 알고리즘
[백준 1712번:손익분기점](https://www.acmicpc.net/problem/1712)

```java
public class Main_1712_BreakEvenPoint {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int A = Integer.parseInt(st.nextToken());
		int B = Integer.parseInt(st.nextToken());
		int C = Integer.parseInt(st.nextToken());
		
		if(B >= C) System.out.println("-1");
		else {
			int D = A/(C-B);
			System.out.println(D+1);
		}
		
	}//main

}//class

```
- 문제에서 말하는 손익분기점의 의미대로 수식을 세운다
- B와 C의 값에 따라 손익분기점이 넘는지 안넘는지를 알 수 있다.
