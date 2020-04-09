# 알고리즘
[백준 1592번:영식이와 친구들](https://www.acmicpc.net/problem/1592)
```java
package simulation_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_1592_YoungsikFriend {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int M = Integer.parseInt(st.nextToken());
		int L = Integer.parseInt(st.nextToken());
		
		int [] index = new int [N+1];
		int now = 1; int cnt = 0;
		
		index[now]++;
		cnt++;
		while(true) {
			if(index[now] == M) break;
			else {
				if(index[now]%2==1) now += L;
				else if(index[now]%2==0) now -=L;
				if(now>N) now -=N;
				else if(now<=0) now+=N;
				//System.out.print(now+" ");
				cnt++;
				index[now]++;
			}
		}
		System.out.println(cnt-1);
	}//main
}//class

```
- 시뮬레이션 문제 하나하나씩 차근차근 구현
