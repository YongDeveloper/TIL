# 알고리즘

[백준 5622번:다이얼](https://www.acmicpc.net/problem/5622)

```java

public class Main_5622_Dial {

	public static void main(String[] args) throws IOException {

		String [] index = {"ABC","DEF","GHI","JKL","MNO","PQRS","TUV","WXYZ"};
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String [] str = br.readLine().split("");
		int sum = 0;
		for (int i = 0; i < str.length; i++) {
			for (int j = 0; j < index.length; j++) {
				if(index[j].contains(str[i])) {
					sum += (j+3);
				}
			}
		}
		System.out.print(sum);
	}//main
}//class
```

- index 배열에 해당 문자열 묶음을 지정해 놓는다.
- index[j].contains(str[i]) 를 통해 해당 문자가 문자열에 포함되어있는지 확인.
- A.contains(B) 이면 A ⊃ B 의 포함관계이다.
