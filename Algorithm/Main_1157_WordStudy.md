# 알고리즘

[백준 1157번: 단어 공부](https://www.acmicpc.net/problem/1157)

```java
public class Main_1157_WordStudy {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		String str = st.nextToken().toUpperCase();
		int [] cnt = new int [26]; char result = '?';
		int max = Integer.MIN_VALUE;
		
		for (int i = 0; i < str.length(); i++) {
			cnt[str.charAt(i)-65]++;
			if(max < cnt[str.charAt(i)-65]) {
				max = cnt[str.charAt(i)-65];
				result = str.charAt(i);
			}
			else if (max == cnt[str.charAt(i)-65]) result = '?';
		}
		System.out.println(result);
    
	}//main
}//class
```

- 알파벳 대/소문자를 구분없게 하려면 String.toUpperCase() 혹은 String.toLowerCase() 를 이용
- 알파벳을 count 하려면 str.charAt()-65 를 해주어서 숫자로 표현해준다. -65는 아스키코드 대문자 이기 때문 

