# 알고리즘
[백준 10757번:큰수 A+B](https://www.acmicpc.net/problem/10757)
```java
package asmd_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.math.BigInteger;
import java.util.StringTokenizer;

public class Main_10757_BigAplusB {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		BigInteger big1 = new BigInteger(st.nextToken());
		BigInteger big2 = new BigInteger(st.nextToken());
		
		System.out.println(big1.add(big2));
		
	}//main

}//class

```
- 큰수끼리의 합을 계산할 때는 BigInteger를 통해 계산한다.
