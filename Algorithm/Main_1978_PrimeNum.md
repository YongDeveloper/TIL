 # 알고리즘
 [백준 1978번:소수 찾기](https://www.acmicpc.net/problem/1978)
 ```java
 package math_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_1978_PrimeNum {

	private static int num;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int cnt = 0;
		
		st = new StringTokenizer(br.readLine());
		for (int i = 0; i < N; i++) {
			num = Integer.parseInt(st.nextToken());
			if(Prime(num)) cnt++;
		}
		System.out.println(cnt);
		
		
	}//main

	public static boolean Prime(int num) {
		if(num==1) return false;
		for (int i = 2; i < num; i++) {
			if(num%i == 0) return false;
		}
		return true;
	}
}//class

 ```
 - 수학 문제
 - 소수 찾기 문제는 자신보다 작은 숫자 중 하나라도 나누어떨어지면 
