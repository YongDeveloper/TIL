# 알고리즘
[백준 1551번:수열의 변화](https://www.acmicpc.net/problem/1551)
```java
package simulation_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_1551_TransferNum {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int K = Integer.parseInt(st.nextToken());
		int [] arr = new int [N];
		int cnt = 0;
		st = new StringTokenizer(br.readLine(),",");
		for (int i = 0; i < N; i++) {
			arr[i] = Integer.parseInt(st.nextToken());
		}
		while(cnt<K) {
			for (int i = 0; i < arr.length-1; i++) {
				arr[i] = arr[i+1]-arr[i];
			}
			cnt++;
		}
		for (int i = 0; i < arr.length-cnt-1; i++) {
			System.out.print(arr[i]+",");
		}
		System.out.println(arr[arr.length-cnt-1]);
	}//main

}//class

```
- 시뮬레이션 문제
- 배열의 차잇값을 다시 그 배열안에 넣어주고
- cnt 한 만큼만 출력하주는 방식으로 구현하였다.
