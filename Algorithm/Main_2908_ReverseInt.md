# 알고리즘

[백준 2908번: 상수](https://www.acmicpc.net/problem/2908)

```java
public class Main_2908_ReverseInt {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int num1 = Integer.parseInt(st.nextToken());
		int num2 = Integer.parseInt(st.nextToken());
		
		num1 = reverse(num1);
		num2 = reverse(num2);
		
		System.out.println(num1>num2 ? num1 : num2);
		
	}//main

	public static int reverse(int input) {
		String out = "";

		while(input !=0) {
			out += input%10; // 1의 자리 숫자를 out에 저장
			input = input/10; // 10,100의 자리 숫자를 다시 input에 넣어서 반복
		}
		
		return Integer.parseInt(out);
	}
	
}//class


```
