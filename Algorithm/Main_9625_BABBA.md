# 알고리즘
[백준 9625번:BABBA](https://www.acmicpc.net/problem/9625)
```java
package for_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main_9625_BABBA {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		int [] f = new int [50];
		f[0] = 0; f[1] = 1;
		
		for (int i = 2; i < f.length; i++) {
			f[i] = f[i-1] +f[i-2];
		}
		System.out.println(f[N-1]+" "+f[N]);
		
	}//main

}//class

```
- 규칙을 찾아보니 피보나치 수열문제
- DP로 구현
