# 알고리즘
[백준 1475번:방 번호](https://www.acmicpc.net/problem/1475)
```java
package charcter_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;

public class Main_1475_RoomNum {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		int [] index = new int [10];
		for (int i = 0; i < str.length(); i++) {
			if(str.charAt(i)=='6') {
				if(index[6]>index[9]) index[9]++;
				else index[6]++;
			}
			else if(str.charAt(i)=='9') {
				if(index[9]>index[6]) index[6]++;
				else index[9]++;
			}
			else index[str.charAt(i)-'0']++;
		}
		Arrays.sort(index);
		System.out.println(index[index.length-1]);
	}//main

}//class
```
- 문자열 정렬 문제
- 6와 9를 서로 대신할 수 있으므로 조건문만 추가하여 구현
