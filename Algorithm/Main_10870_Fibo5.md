# 알고리즘
[백준 10870번:피보나치 수5](https://www.acmicpc.net/problem/10870)

```java
public class Main_10870_Fibo5 {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		Fibo(N);
		System.out.println(Fibo(N));
	}//main

	public static int Fibo(int N) {
		
		if(N<=1) return N;
		else return Fibo(N-1)+Fibo(N-2);
		
	}//Fibo
	
}//class

```
- 재귀를 이용한 피보나치 수열.

#### 200328
