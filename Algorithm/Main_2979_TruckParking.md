# 알고리즘
[백준 2979번:트럭 주차](https://www.acmicpc.net/problem/2979)
```java
public class Main_2979_TruckParking {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int [] index = new int[101];
		int sum = 0;
		
		int A = Integer.parseInt(st.nextToken());
		int B = Integer.parseInt(st.nextToken());
		int C = Integer.parseInt(st.nextToken());
		
		for (int i = 0; i < 3; i++) {
			st = new StringTokenizer(br.readLine());
			int start = Integer.parseInt(st.nextToken());
			int finish = Integer.parseInt(st.nextToken());
			for (int j = start; j < finish; j++) {
				index[j]++;
			}
		}
		
		for (int i = 1; i < index.length; i++) {
			if(index[i]==1) sum += index[i]*A;
			else if(index[i]==2) sum += index[i]*B;
			else if(index[i]==3) sum += index[i]*C;
		}
		
		System.out.println(sum);
		
	}//main

}//class

```
- 시뮬레이션 문제
- 카운팅 정렬을 통해 쉽게 계산가능.
