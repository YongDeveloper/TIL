# 알고리즘
[백준 1018번: 체스판 다시 칠하기](https://www.acmicpc.net/problem/1018)

```java
	public class Main_1018_Chess {
	
		public static void main(String[] args) throws IOException {
	
			String [] chess = {"WBWBWBWB","BWBWBWBW",
					"WBWBWBWB","BWBWBWBW",
					"WBWBWBWB","BWBWBWBW",
					"WBWBWBWB","BWBWBWBW"};
			
			BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
			StringTokenizer st = new StringTokenizer(br.readLine());
			int N = Integer.parseInt(st.nextToken());
			int M = Integer.parseInt(st.nextToken());
			String [] str = new String [N];
			String temp = "";
			int cnt = 0;
			int min = Integer.MAX_VALUE;
			for (int i = 0; i < N; i++) {
				str[i] = br.readLine();
			}
			
			for (int i = 0; i < N-7; i++) {
				for (int j = 0; j < M-7; j++) {
					cnt = 0;
					for (int k = 0; k < 8; k++) {
						temp = str[i+k].substring(j, j+8);
						
						for (int m = 0; m < 8; m++) {
							if(temp.charAt(m)==chess[k].charAt(m)) cnt++;
						}
					}
					if(cnt>=32) cnt = 64-cnt;
					if(min > cnt) min = cnt;
				}
			}
			
			System.out.println(min);
			
		}//main
	
	}//class
```

- 체스판을 미리 String 배열에 담아 놓은 후 비교하는 방식으로 구현
- (1.1) 이 B일때의 체스판과 W일때 체스판을 구분해주어야 하지만 if(cnt>=32) cnt = 64-cnt;로 한가지만 구현
- 반복문 i와 j 은 비교를 시작할 좌표에 대한 반복이고
- 반복문 k는 8개씩 끊어서 비교하려는 배열, 반복문 m은 한글자씩 비교하는 반복문이다.
- 좌표를 이동할 때마다 cnt를 세주어 min 값을 도출했다.
