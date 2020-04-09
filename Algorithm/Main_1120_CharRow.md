# 알고리즘
[백준 1120번:문자열](https://www.acmicpc.net/problem/1120)
```java
package simulation_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_1120_CharRow {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		String A = st.nextToken();
		String B = st.nextToken();
		int max = Integer.MIN_VALUE;
		
		for (int i = 0; i <= B.length()-A.length(); i++) {
			String temp = B.substring(i, i+A.length());
			int cnt = 0;
			for (int j = 0; j < temp.length(); j++) {
				if(A.charAt(j)==temp.charAt(j)) cnt++;
			}
			if(max < cnt) max = cnt;
		}
		System.out.println(A.length()-max);
		
	}//main
	
}//class

```

- 처음엔 앞뒤로 추가해주면서 비교하려고 했지만 생각을 바꿔서
- 한칸씩 이동하면서 짧은쪽과 긴쪽에 문자를 비교한다.
- 가장 많이 일치하는 쪽에 기준을 설정하여 cnt를 센다.
