# 알고리즘
[백준 15662번:톱니바퀴(2)](https://www.acmicpc.net/problem/15662)

```java
package simulation_;

import java.io.*;
import java.util.*;

public class Main_15662_Gear2 {

	private static int N, D, T, K, cnt, index;
	private static String[] str;
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		T = Integer.parseInt(st.nextToken());
		str = new String[T+1];
		
		for (int i = 1; i <= T; i++) {
			st = new StringTokenizer(br.readLine());
			str[i] = st.nextToken();
		}
		st = new StringTokenizer(br.readLine());
		K = Integer.parseInt(st.nextToken());
		cnt = 0;
		for (int i = 0; i < K; i++) {
			st = new StringTokenizer(br.readLine());
			N = Integer.parseInt(st.nextToken());
			D = Integer.parseInt(st.nextToken());
			Process();
		}
		for (int i = 1; i <= T; i++) {
			if(str[i].charAt(0)=='1') cnt++;
		}
		System.out.println(cnt);
		
	}//main
	public static void Process() {
		int indexUp = N;
		while(true) { 
			if(indexUp+1<=T && str[indexUp].charAt(2) != str[indexUp+1].charAt(6)) indexUp++;
			else break;
		}
		int indexDown = N;
		while(true) {
			if(indexDown-1>=1 && str[indexDown].charAt(6) != str[indexDown-1].charAt(2)) indexDown--;
			else break;
		}
		
		if(D==1) { // 시계 방향
			index = N;
			while(true) {
				if(index > indexUp) break;
				Clockwise();
				index++;
				
				if(index > indexUp) break;
				unClockwise();
				index++;
			}// 오른쪽
			index = N-1;
			while(true) {//
				if(index < indexDown) break;
				unClockwise();
				index--;
				
				if(index < indexDown) break;
				Clockwise();
				index--;
			}//왼쪽
		}
		else if(D==-1) {// 반시계
			index = N;
			while(true) {
				if(index > indexUp) break;
				unClockwise();
				index++;
				
				if(index > indexUp) break;
				Clockwise();
				index++;
			}//오른쪽
			index = N-1;
			while(true) {
				if(index < indexDown) break;
				Clockwise();
				index--;
				
				if(index < indexDown) break;
				unClockwise();
				index--;
			}//왼쪽
		}
	}
	public static void Clockwise() {
		str[index] = str[index].substring(7) + str[index].substring(0, 7); // 시계
	}
	public static void unClockwise() {
		str[index] = str[index].substring(1) + str[index].substring(0, 1); // 반시계
	}
}//class
```
- 단순 시뮬레이션 문제.
