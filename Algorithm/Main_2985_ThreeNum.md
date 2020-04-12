# 알고리즘
[백준 2985번:세 수](https://www.acmicpc.net/problem/2985)
```java
package combination_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_2983_ThreeNum {

	private static int A;
	private static int B;
	private static int C;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		A = Integer.parseInt(st.nextToken());
		B = Integer.parseInt(st.nextToken());
		C = Integer.parseInt(st.nextToken());
		if(A+B==C) System.out.println(A+"+"+B+"="+C);
		else if(A-B==C) System.out.println(A+"-"+B+"="+C);
		else if(A*B==C) System.out.println(A+"*"+B+"="+C);
		else if(A/B==C) System.out.println(A+"/"+B+"="+C);
		
		else if(A==B+C) System.out.println(A+"="+B+"+"+C);
		else if(A==B-C) System.out.println(A+"="+B+"-"+C);
		else if(A==B*C) System.out.println(A+"="+B+"*"+C);
		else if(A==B/C) System.out.println(A+"="+B+"/"+C);
	}//main

}//class

```
- 조합 문제
