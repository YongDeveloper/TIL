# 알고리즘
[백준 10989번:수 정렬하기3](https://www.acmicpc.net/problem/10989)
```java
public class Main_10989_SortNum3 {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		int N = Integer.parseInt(br.readLine());
		int [] index = new int [10001];
		for (int i = 0; i < N; i++) {
			index[Integer.parseInt(br.readLine())]++;
		}
		
		for (int i = 1; i <= 10000; i++) {
			if(index[i]>0) {
				for (int j = 0; j < index[i]; j++) {
					bw.write(i+"\n");
				}
			}
		}
		br.close();
		bw.close();
		
	}//main

}//class

```
- 카운팅 정렬로 구현
- 출력을 Sysout으로 하면 시간초과
- bufferedreader와 bufferedwriter를 사용하여 통과
