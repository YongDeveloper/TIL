# 알고리즘
[백준 2910번:빈도 정렬](https://www.acmicpc.net/problem/2910)
```java
package datastructure_;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.HashMap;
import java.util.Iterator;
import java.util.Stack;
import java.util.StringTokenizer;

public class Main_2910_FrequencyArray {

	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int C = Integer.parseInt(st.nextToken());
		int [] arr = new int [N];
		st = new StringTokenizer(br.readLine());
		Stack<Integer> stack = new Stack<>();
		
		for (int i = 0; i < N; i++) {
			arr[i] = Integer.parseInt(st.nextToken());
			if(stack.isEmpty()) stack.push(arr[i]);
			else if(stack.search(arr[i])==-1) stack.push(arr[i]); 
		}
		
		HashMap<Integer, Integer> map = new HashMap<>();
		
		for (int i = 0; i < N; i++) {
			if(map.containsKey(arr[i])) {
				map.replace(arr[i], map.get(arr[i])+1);
			}else {
				map.put(arr[i], 1);
			}
		}
		
		ArrayList<Integer> list = new ArrayList<Integer>(map.keySet());
		Collections.sort(list, new Comparator<Integer>() {

			@Override
			public int compare(Integer o1, Integer o2) {
				if(map.get(o2)== map.get(o1)) {
					return Integer.compare(stack.search(o2), stack.search(o1));
				}
				else return Integer.compare(map.get(o2), map.get(o1));
			}
		});
		
		
		Iterator<Integer> iter = list.iterator();
		while(iter.hasNext()) {
			Integer element = iter.next();
			for (int i = 0; i < map.get(element); i++) {
				System.out.print(element+" ");
			}
		}
		
	}//main

}//clas

```
- Stack과 Hashmap, Arraylist를 이용하여 구현.
