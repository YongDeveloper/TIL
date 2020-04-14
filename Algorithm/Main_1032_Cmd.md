# 알고리즘
[백준 1032번:제출](https://www.acmicpc.net/submit/1032)
```java
package charcter_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main_1032_Cmd {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		String [] str = new String [N];
		
		for (int i = 0; i < N; i++) {
			str[i] = br.readLine();
		}
		boolean check = false;
		
		for (int i = 0; i < str[0].length(); i++) {
			check = false;
			for (int j = 0; j < N-1; j++) {
				if(str[j].charAt(i)!=str[j+1].charAt(i)) {
					check = true;
					break;
				}
			}	
			
			if(!check) System.out.print(str[0].charAt(i));
			else System.out.print("?");
		}
		
	}//main

}//class

```
- 문제열 처리 문제.
