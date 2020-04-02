# 알고리즘
[백준 1436번:영화감독 숌](https://www.acmicpc.net/problem/1436)

```java
public class Main_1436_MovieDirector {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String strN = br.readLine();
		String strK = "";
		int N = Integer.parseInt(strN);
		int result = 0;
		int cnt = 0;
		int K = 1;
		
		while(true) {
			strK = Integer.toString(K);
			if(strK.contains("666")) {
				cnt++;
				if(cnt==N) {
					result = K;
					break;
				}
			}
			K++;
		}//while
		
		System.out.println(result);
	}//main

}//class
```

- 숫자 1부터 시작하여 1씩 증가시키면서 숫자에 "666"이 포함되어있는지를 확인한다.
- "666"를 발견한다면 cnt를 증가시켜주면서 input과 비교하여 같으면 출력한다.
