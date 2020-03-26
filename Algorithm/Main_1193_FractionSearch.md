# 알고리즘

[백준 1193번:분수찾기](https://www.acmicpc.net/problem/1193)

```java
public class Main_1193_FractionSearch {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int num = Integer.parseInt(br.readLine());
		boolean check = false;
		int y = 1; int x = 1;
		
		for (int i = 1; i < num; i++) {
			if(check) {
				y++; x--;
				if (x == 0) {
					check = false;
					x++;
				}
			}else {
				y--; x++;
				if(y == 0) {
					check = true;
					y++;
				}
			}
			
		}
		System.out.println(y+"/"+x);
	}//main

}//class

```
- 해당 숫자를 처음부터 하나씩 증가 시키면서 좌표를 이동
- x 와 y는 처음 (1.1) 좌표이다
- 도착지점에 x==0 이거나 y==0이면 check해 방향을 바꾼다.
