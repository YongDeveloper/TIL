# 알고리즘

[백준 1316번: 그룹 단어 체커](https://www.acmicpc.net/problem/1316)

```java

public class Main_1316_GroupWord {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int TC = Integer.parseInt(br.readLine());
		int cnt = TC;
		for (int tc = 1; tc <= TC; tc++) {
			boolean [] check = new boolean [26];
			StringTokenizer st = new StringTokenizer(br.readLine());
			String [] str = st.nextToken().split("");
			
			for (int i = 0; i < str.length; i++) {
				int index = str[i].charAt(0)-97;
				if(!check[index]) check[index]=true;
				else {
					if(i==0) continue;
					else {
						if(index==str[i-1].charAt(0)-97) continue;
						else {
							cnt--;
							break;
						}
					}
				}
			}//str.length
		}//tc
		
		System.out.println(cnt);
	}//main
}//class
```
- 문장 갯수 만큼 카운트 해주고 조건에 부합하지 않으면 카운트 감소
- index = str[i].charAt(0)-97 은 소문자를 숫자로 표현해 주는 방법
- 문자가 처음 등장하면 check
- 이미 check 된 문자이면 1. 앞문자와 비교해서 같으면 continue 2. 다르다면 cnt 감소하여 for중단


