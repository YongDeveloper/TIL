# 알고리즘

[백준 2798번: 블랙잭](https://www.acmicpc.net/problem/2798)

```java
public class Main_2798_BlackJack {
	
	private static int [] arr;
	private static int [] trr;
	private static int sum, M;
	private static int max = Integer.MIN_VALUE;

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		M = Integer.parseInt(st.nextToken());
		
		
		arr = new int [N];
		trr = new int [3];
		sum = 0;
		
		st = new StringTokenizer(br.readLine());
		for (int i = 0; i < N; i++) {
			arr[i] = Integer.parseInt(st.nextToken());
		}
		
		Comb(N,3);
		System.out.println(max);
		
		
	}//main
	
	public static void Comb(int n, int r) {
		if(r==0) {
			//System.out.print(Arrays.toString(trr)+" ");
			for (int i = 0; i < 3; i++) {
				sum += trr[i];
			}
			//System.out.println(sum);
			if(sum<=M && max<sum) max = sum;
			sum = 0;
			
		}
		else if(n<r) return;
		else {
			trr[r-1] = arr[n-1];
			Comb(n-1,r-1);
			Comb(n-1,r);
		}
	}//Comb

}//class
```
- 브루트포스 문제였지만 조합을 이용하여 구현하였다
- Comb 메서드는 자주 나오는 표현이니 익숙해두자.
