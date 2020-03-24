# 알고리즘

[백준 11720번: 숫자의 합](https://www.acmicpc.net/problem/11720)

```java

public class Main_11720_SumOfDigit {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int num = Integer.parseInt(st.nextToken());
		int sum = 0;
		
		String [] str = br.readLine().split("");
		for (int i = 0; i < num; i++) {
			sum += str[i].charAt(0)-'0';
		}
		System.out.println(sum);
		
	}//main
}//class


```
- br.readLine().split(""); 을 사용하여 한글자 한글자 단위로 끊어서 String 배열에 넣는다
- str[i].charAt(0)-'0' 을 통해 int 형으로 만들어 준다.
