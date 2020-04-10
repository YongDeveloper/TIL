# 알고리즘
[백준 1764번:듣보잡](https://www.acmicpc.net/problem/1764)
```java
package charcter_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.Collections;
import java.util.HashSet;
import java.util.StringTokenizer;

public class Main_1764_NoHearNoSee {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int M = Integer.parseInt(st.nextToken());
		ArrayList<String> list = new ArrayList<>();
		HashSet<String> set = new HashSet<>();
		
		while(N-- > 0) {
			String str = br.readLine();
			set.add(str);
		}
		
		while(M-- > 0) {
			String str = br.readLine();
			if(set.contains(str)) list.add(str);
		}
		
		Collections.sort(list);
		System.out.println(list.size());
		for (String s : list) {
			System.out.println(s);
		}
	}//main

}//class

```
- 문자열 처리 문제
- 처음엔 for반복문으로 하나씩 비교했으나 시간초과.
- set과 list를 이용해 해결
