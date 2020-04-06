# 알고리즘

[백준 1181번:단어정렬](https://www.acmicpc.net/problem/1181)

```java
public class Main_1181_WordSort {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		HashSet<String> set = new HashSet<>();
		for (int i = 0; i < N; i++) {
			set.add(br.readLine());
		}
		List <String> list = new ArrayList<>(set);
		
		Collections.sort(list, new Comparator<String>() 
		{
			@Override
			public int compare(String o1, String o2) {
				if(o1.length() > o2.length()) return 1;
				else if(o1.length() < o2.length()) return -1;
				else return o1.compareTo(o2);
			}
		});
		
		for (String str : list) {
			System.out.println(str);
		}
		
	}//main

}//class
```
- 중복을 제거하기 위해 Hashset을 이용하였고
- 정렬을 하기 위해 list에 담았다
- Collections.sort(list, new Comparator<String>(){} 를 이용하여 단어 길이 오름차순으로 정렬한 후 사전순서로 정렬.
