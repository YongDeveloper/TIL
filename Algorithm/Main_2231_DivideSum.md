# 알고리즘
[백준 2231번: 분해합](https://www.acmicpc.net/problem/2231)

```java
package step13;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_2231_DivideSum {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		String strN= st.nextToken();
		int N = Integer.parseInt(strN);
		int K = N;
		String strK = "";
		int result = 0;
		int sum = 0;
		
		while(K>=0) {
			K--;
			strK = Integer.toString(K);
			sum = 0;
			
			for (int i = 0; i < strK.length(); i++) {
				sum += strK.charAt(i)-'0';
			}
			sum += K;
			//System.out.println(sum);
			if(sum==N) result = K;
			
		}//while
		
		System.out.println(result);
		
	}//main

}//class

```

- 주어진 N 수보다 -1씩 해준다음에 분해합을 계산한다. 
- 0이 될때까지 1씩 감소한 수가 N과 같으면 result값에 덮어 씌어준다.
