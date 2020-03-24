# 알고리즘
[백준 10809번:알파벳 찾기](https://www.acmicpc.net/problem/10809)


```java
public class Main_10809_AlpabetSearch {

	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		String [] str = br.readLine().split("");
		String [] index = {"a","b","c","d","e","f","g","h","i","j",
		"k","l","m","n","o","p","q","r","s","t","u","v","w","x","y","z"};
		boolean check = false;
		
		for (int i = 0; i < index.length; i++) {
			check = false;
			for (int j = 0; j < str.length; j++) {
				if(index[i].equals(str[j])) {
					System.out.print(j+" ");
					check = true;
					break;
				}
			}
			if(!check) System.out.print("-1 ");
		}
		
	}//main
}//class


```
- 문장에 해당 알파벳이 존재하는지 확인하기 위해서 index 배열에 알파벳 전부를 넣었다.
- 문장의 첫 알파벳부터 하나하나씩 있는지 없는지를 확인 : 완전 탐색.
- 해당 알파벳이 있을경우 boolean check = true 를 이용.

