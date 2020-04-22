# 알고리즘
[백준 2964번: 5와 6의 차이](https://www.acmicpc.net/problem/2864)
```java
package charcter_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_2864_Difference56 {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		String str1 = st.nextToken();
		String str2 = st.nextToken();
		String temp1 = str1;
		String temp2 = str2;
		for (int i = 0; i < str1.length(); i++) {
			temp1 = str1.replace('6', '5');
		}
		for (int i = 0; i < str2.length(); i++) {
			temp2 = str2.replace('6', '5');
		}
		int min = Integer.parseInt(temp1)+Integer.parseInt(temp2);
		
		for (int i = 0; i < str1.length(); i++) {
			temp1 = str1.replace('5', '6');
		}
		for (int i = 0; i < str2.length(); i++) {
			temp2 = str2.replace('5', '6');
		}
		int max = Integer.parseInt(temp1)+Integer.parseInt(temp2);
		
		System.out.println(min+" "+max);
	}//main

}//class

```
- 문자열 처리 문제.
- String API중 replace를 이용하여 구현.
