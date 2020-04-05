# 알고리즘
[백준 1427번:소트인사이드](https://www.acmicpc.net/problem/1427)
```java
public class Main_1427_SortInside {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String [] str = br.readLine().split("");
		Integer [] arr = new Integer [str.length];
		
		for (int i = 0; i < arr.length; i++) {
			arr[i] = Integer.parseInt(str[i]);
		}
		Arrays.sort(arr, Collections.reverseOrder());
		
		for (int i = 0; i < arr.length; i++) {
			System.out.print(arr[i]);
		}
	}//main

}//class
```
- 내림차순 정렬은 Arrays.sort(arr, Collections.reverseOrder()); API를 사용하였다 (대신 Integer 배열이어야)
- 또하나의 방법은 List를 이용하여 Collections.reverse(list); 를 해주면 된다.
