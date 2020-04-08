# 알고리즘
[백준 2455번:지능형 기차](https://www.acmicpc.net/problem/2455)
```java
public class Main_2455_SmartTrain {

	public static class Train{
		
		int out;
		int in;
		
		public Train(int out, int in) {
			this.out = out;
			this.in = in;
		}
		
	}//train
	
	public static void main(String[] args) throws IOException {
		
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		List<Train> list = new ArrayList<>();

		for (int i = 0; i < 4; i++) {
			StringTokenizer st = new StringTokenizer(br.readLine());
			list.add(new Train(Integer.parseInt(st.nextToken()),
					Integer.parseInt(st.nextToken())));
		}
		int x = list.get(1).in - list.get(1).out;
		System.out.println(Math.max(list.get(3).out,Math.max(list.get(0).in, list.get(0).in+x)));
		
	}//main	

}//class

```
- 시뮬레이션 문제
- in, out를 가진 class를 만들었지만 굳이 그러지 않아도 풀수 있는 문제다.
