# 알고리즘
[백준 2750번: 수 정렬하기](https://www.acmicpc.net/problem/2750)

```java
public class Main_2750_SortNum {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		int [] arr = new int [N];
		for (int i = 0; i < N; i++) {
			arr[i] = Integer.parseInt(br.readLine());
		}
		
		Arrays.sort(arr);
		
		for (int i = 0; i < N; i++) {
			System.out.println(arr[i]);
		}
		
	}//main
  
}//class
```
- 정렬문제 Arrays.sort를 이용하여 구현
