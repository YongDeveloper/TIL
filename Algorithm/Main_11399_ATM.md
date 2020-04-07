# 알고리즘
[백준 11399번:ATM](https://www.acmicpc.net/problem/11399)

```java
public class Main_11399_ATM {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int [] arr = new int [N];
		int sum = 0;
		int min = Integer.MAX_VALUE;
		
		st = new StringTokenizer(br.readLine());
		for (int i = 0; i < arr.length; i++) {
			arr[i] = Integer.parseInt(st.nextToken());
			//System.out.print(arr[i]+" ");
		}
		
		Arrays.sort(arr);
		for (int i = 0; i < arr.length; i++) {
			for (int j = N-i; j > 0; j--) {
				sum += arr[i];
			}
		}
		System.out.println(sum);
		
	}//main

}//class
```
- 그리디 문제 : 정렬 후 최종 더하는 값이 최소 값이다
