# 알고리즘
[백준 2529번: 부등호](https://www.acmicpc.net/problem/2529)
```java
package bruteforce_;

import java.io.*;
import java.util.*;

public class Main_2529_Inequality {

	private static ArrayList<String> list = new ArrayList<>();
	private static char[] index;
	private static int[] set;
	private static boolean[] visited;
	private static int N;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		N = Integer.parseInt(br.readLine());
		index = new char [N];
		StringTokenizer st = new StringTokenizer(br.readLine());
		for (int i = 0; i < N; i++) {
			index[i] = st.nextToken().charAt(0);
		}
		set = new int [N+1];
		visited = new boolean [10];
		Perm(0);
		Collections.sort(list);
		System.out.println(list.get(list.size()-1));
		System.out.println(list.get(0));
	}//main
	public static void Perm(int size) {
		if(size==N+1) {
			Process();
		}else {
			for (int i = 0; i < 10; i++) {
				if(!visited[i]) {
					visited[i] = true;
					set[size] = i;
					Perm(size+1);
					visited[i] = false;
				}
			}
		}
	}//Perm
	public static void Process() {
		String str = "";
		str += set[0];
		for (int i = 0; i < index.length; i++) {
			if(index[i]=='<' && set[i] < set[i+1] ||
					index[i]=='>' && set[i] > set[i+1]) {
				str += set[i+1];
			}else return;
		}
		list.add(str);
	}//Process
}//class
```
- 순열 DFS로 구현. 마지막은 list에 담아서 정렬 후 출력.
