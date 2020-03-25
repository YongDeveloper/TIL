# 알고리즘

[백준 2941번: 크로아티아 알파벳](https://www.acmicpc.net/problem/2941)

```java
public class Main_2941_Croatia {

	public static void main(String[] args) throws IOException {

		String [] index = {"c=","c-","dz=","d-","lj","nj","s=","z="};
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String str = br.readLine();
		int cnt = 0;
		
		for (int i = 0; i < index.length; i++) {
			if(str.contains(index[i])) {
				str = str.replace(index[i], "*");
			}
		}
		cnt = str.length();
		System.out.println(cnt);
		
	}//main
}//class
```
- 특정 문자열을 한단어로 만드는 방법
- str.replace를 이용하여 특정 문자열을 * 로 치환해 전체 길이를 계산한다. 

