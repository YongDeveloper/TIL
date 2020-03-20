# 알고리즘

[ 백준 2588번: 곱셈 ](https://www.acmicpc.net/problem/2588)

## 전체 소스 코드

```java

public class Main_2588_Multiply {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int num1 = Integer.parseInt(br.readLine());
		int num2 = Integer.parseInt(br.readLine());
		int temp = num2;
		while(temp>0) {
			System.out.println(num1*(temp%10));
			temp = temp/10;
			
		}
		System.out.println(num1*num2);
	}//main

}//class


```

## 중요 코드 내용
- 1의 자리수부터 차례대로 자리수 가져오기

```java

while(temp>0) {
	System.out.println(num1*(temp%10));
	temp = temp/10;
}

```


