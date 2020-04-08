# 알고리즘
[백준 5532번:방학숙제](https://www.acmicpc.net/problem/5532)
```java
public class Main_5532_VacationHw {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int L = Integer.parseInt(br.readLine());
		double A = Integer.parseInt(br.readLine());
		double B = Integer.parseInt(br.readLine());
		double C = Integer.parseInt(br.readLine());
		double D = Integer.parseInt(br.readLine());
		
		double lang = A/C;
		double math = B/D;
		
		long x1 = Math.round(Math.ceil(lang));
		long x2 = Math.round(Math.ceil(math));
		
		System.out.println(L-(Math.max(x1, x2)));
		
	}//main

}//class


```
- 시뮬레이션 문제이지만 Math함수의 올림함수 Math.ceil()과 반올림함수 Math.round()를 이용하여 구현
