# 알고리즘
[백준 1094번:막대기](https://www.acmicpc.net/problem/1094)
```java
public class Main_1094_Stick {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		int stick = 64; int cnt = 0; int sum = 0;
		
		while(N>0) {
			if(stick >N) stick /= 2;
			else {
				cnt++;
				N -= stick;
			}
		}

		System.out.println(cnt);
	
	}//main

}//class

```
- 시뮬레이션 문제
- 기존의 막대기 길이를 2로 나누면서 입력 수보다 작으면 N에서 빼주고 cnt 처리해준다.
