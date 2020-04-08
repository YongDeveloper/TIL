# 알고리즘
[백주누 1541번:잃어버린 괄호](https://www.acmicpc.net/problem/1541)
```java
public class Main_1541_LostBracket {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String [] strMinus = br.readLine().split("\\-");
		int min = 0;
		
		for (int i = 0; i < strMinus.length; i++) {
			int num = Calc(strMinus[i]);
			
			if(i==0) min += num;
			else min -= num;
		}
		
		System.out.println(min);
		
	}//main
	
	public static int Calc(String str) {
		String [] temp = str.split("\\+");
		int result = 0;
		
		for (String s : temp) {
			result += Integer.parseInt(s);
		}
		
		return result;
	}
	
}//class

```
- 그리디 문제
- 마이너스 기호를 기준으로 split를 해주어 합을 따로 계산해준다
- 0번째는 합을 그대로 더해주고 나머지는 합을 빼준다.
