# 알고리즘
[백준 5555번:반지](https://www.acmicpc.net/problem/5555)
```java
package charcter_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main_5555_Ring {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		int N = Integer.parseInt(br.readLine());
		int cnt = 0;
		String [] arr = new String [N];
		
		for (int i = 0; i < N; i++) {
			arr[i] = br.readLine();
			arr[i] += arr[i];
			if(arr[i].contains(str)) {
				cnt++; continue;
			}
		}
		System.out.println(cnt);
		
	}//main

}//class

```
- 문제열 처리 문제.
