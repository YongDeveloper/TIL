# 알고리즘
[백준 11654번:아스키 코드](https://www.acmicpc.net/problem/11654)
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main_11654_ASCI {
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		char str = st.nextToken().charAt(0);
		System.out.println(Integer.valueOf(str));
		
	}//main
}//class

```
- 아스키 코드로 전환하는 방법은 문자를 int형으로 변환시켜주는 것이다
- 출력 시 Integer.valueOf를 처리해준다. (Integer.parseInt는 불가)


