# 알고리즘
[백준 15686번:치킨배달](https://www.acmicpc.net/problem/15686)
```java
package simulation_;

import java.io.*;
import java.util.*;

public class Main_15686_ChickenDelivery {

	private static int N, M, dismin, min= Integer.MAX_VALUE;
	private static int[][] map;
	private static ArrayList<Member> home = new ArrayList<>();
	private static ArrayList<Member> chicken = new ArrayList<>();
	private static int[] set;
	private static Member [] comb;

	public static class Member{
		int y;
		int x;
		public Member(int y, int x) {
			this.y = y;
			this.x = x;
		}
	}
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		M = Integer.parseInt(st.nextToken());
		map = new int [N][N];
		
		for (int i = 0; i < N; i++) {
			st = new StringTokenizer(br.readLine());
			for (int j = 0; j < N; j++) {
				map[i][j] = Integer.parseInt(st.nextToken());
				if(map[i][j]==1) home.add(new Member(i,j));
				if(map[i][j]==2) chicken.add(new Member(i,j));
			}
		}
		set = new int [M];
		Comb(set, 0, 0, chicken.size(), M);		
		System.out.println(min);
	}//main

	public static void Comb(int [] set, int size, int index, int n, int r) {
		if(r==0) {
			comb = new Member[size];
			for (int i = 0; i < size; i++) {
				comb[i] = chicken.get(set[i]);
			}
			Process(comb);
			return;
		}else if(n==index) return;
		else {
			set[size] = index;
			Comb(set, size+1, index+1, n, r-1);
			Comb(set, size, index+1, n , r);
		}
	}//Comb
	
	public static void Process(Member[] comb) {
		int sum = 0;
		for (int i = 0; i < home.size(); i++) {
			Member hm = home.get(i);
			dismin = Integer.MAX_VALUE;
			
			for (int j = 0; j < comb.length; j++) {
				int distance = Math.abs(comb[j].y-hm.y) + Math.abs(comb[j].x-hm.x);
				if(dismin > distance) dismin = distance;
			}
			sum += dismin;
		}
		if(min > sum) min = sum;
	}//Process
}//class
```
- 시뮬레이션 문제.
