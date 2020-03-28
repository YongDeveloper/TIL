# 알고리즘

[백준 10872번:팩토리얼](https://www.acmicpc.net/problem/10872)

```java
public class Main_10872_Factorial {

	public static int result;
	
	public static void Factorial(int N) {
		if(N==0 || N==1) return;
		else {
			result *= N;
			Factorial(N-1);
		}
		
	}//Factorial
	
	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int N = Integer.parseInt(br.readLine());
		result = 1;
		Factorial(N);
		System.out.println(result);
		
	}//main
	
}//class

```

- for문 말고 재귀를 이용하여 문제를 해결
- N==0일때도 생각할것.
