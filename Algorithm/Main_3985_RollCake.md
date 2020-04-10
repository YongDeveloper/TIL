# 알고리즘
[백준 3985번:롤 케이크](https://www.acmicpc.net/problem/3985)
```java
package simulation_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main_3985_RollCake {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int L = Integer.parseInt(br.readLine());
		int N = Integer.parseInt(br.readLine());
		int [] index = new int [L+1];
		int [] result = new int [L+1];
		
		int realMax = 0; int realMaxIndex = 0;
		int thinkMax = 0; int thinkMaxIndex = 0;
		
		for (int i = 1; i <= N; i++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			int start = Integer.parseInt(st.nextToken());
			int end = Integer.parseInt(st.nextToken());
			if(thinkMax < end-start) {
				thinkMax = end-start;
				thinkMaxIndex = i;
			}
			
			for (int j = start; j <= end; j++) {
				if(index[j]==0) index[j] = i;
			}
			
		}
		//System.out.println(Arrays.toString(index));
		
		for (int i = 1; i < index.length; i++) {
			if(index[i]!=0) result[index[i]]++;
		}
		
		//System.out.println(Arrays.toString(result));
		
		for (int i = 1; i < result.length; i++) {
			if(realMax < result[i]) {
				realMax = result[i];
				realMaxIndex = i;
			}
		}
		System.out.println(thinkMaxIndex);
		System.out.println(realMaxIndex);
	}//main

}//class

```
- 시뮬레이션 문제
- 최대값과 최대값의 해당하는 index 관리로 구현
