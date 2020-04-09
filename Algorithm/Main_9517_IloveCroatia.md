# 알고리즘
[백준 9517번:아이 러브 크로아티아](https://www.acmicpc.net/problem/9517)
```java
package simulation_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_9517_IloveCroatia {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int K = Integer.parseInt(br.readLine());
		int N = Integer.parseInt(br.readLine());
		int [] arr = new int [N];
		String [] str = new String [N];
		int time = 0;
		for (int i = 0; i < N; i++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			arr[i] = Integer.parseInt(st.nextToken());
			str[i] = st.nextToken();
		}
		
		for (int i = 0; i < arr.length; i++) {
			time += arr[i];
			if(time>=210) break;
			else {
				if(str[i].equals("T")) {
					K++;
					if(K>8) K -= 8;
					continue;
				}
				else continue;
			}
		}
		
		System.out.println(K);
	}//main

}//class

```

- 시뮬레이션 문제
- for문안에 continue;를 이용해서 N또는 P를 관리했다.
