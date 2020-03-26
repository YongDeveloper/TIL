# 알고리즘

[백준 2292번:벌집](https://www.acmicpc.net/problem/2292)

```java
public class Main_2292_BeeHouse {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int num = Integer.parseInt(br.readLine());
		int cnt = 0;
		for (int i = 1; i < 19000; i++) {
			if((3*i*i-3*i+2)<=num) {
				continue;
			}if((3*i*i-3*i+2)>num) {
				cnt = i;
				break;
			}
		}
		System.out.println(cnt);
	}//main
}//class

```
- N의 최대값이 1,000,000,000 이므로 넉넉히 최대 19000을 주었다 실제론 (대략 182**.xxx)
- i가 1부터 하나씩 증가시키면서 확인해 주었다
- 일반항은 시작점에 따라 다르지만 3n^2 -3n +2 을 활용했다

