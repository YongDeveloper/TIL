# 알고리즘
[백준 2922번:점수 계산](https://www.acmicpc.net/problem/2822)
```java
package for_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.Comparator;

public class Main_2822_ScoreCalc {

	public static class Member{
		int score;
		int index;
		public Member(int score, int index) {
			super();
			this.score = score;
			this.index = index;
		}
		public int getScore() {
			return score;
		}
		public int getIndex() {
			return index;
		}
		@Override
		public String toString() {
			return "Member [score=" + score + ", index=" + index + "]";
		}
		
	}//member
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		ArrayList<Member> list = new ArrayList<>();
		int sum = 0;
		int [] temp = new int[5];
		
		for (int i = 0; i < 8; i++) {
			list.add(new Member(Integer.parseInt(br.readLine()), i+1));
		}
		
		Collections.sort(list, new Comparator<Member>() {

			@Override
			public int compare(Member o1, Member o2) {
				return Integer.compare(o1.score, o2.score);
			}
		});
		for (int i = 3; i < 8; i++) {
			sum += list.get(i).score;
		}
		System.out.println(sum);
		
		for (int i = 3; i < 8; i++) {
			temp[i-3] = list.get(i).index;
		}
		Arrays.sort(temp);
		for (int i : temp) {
			System.out.print(i+" ");
		}
	}//main

}//class

```
- for 처리 문제
