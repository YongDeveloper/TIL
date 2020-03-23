# 알고리즘

[백준 1110번: 더하기 사이클](https://www.acmicpc.net/problem/1110)

- 26부터 시작한다. 2+6 = 8이다. 새로운 수는 68이다. 6+8 = 14이다. 새로운 수는 84이다. 
                8+4 = 12이다. 새로운 수는 42이다. 4+2 = 6이다. 새로운 수는 26이다.

- 위의 예는 4번만에 원래 수로 돌아올 수 있다. 따라서 26의 사이클의 길이는 4이다.


- 각 자리의 수를 이용할땐 나누기 연산자와 퍼센트 연산자를 이용하면 편리하게 코딩할수 있다

```java

public static void main(String[] args) throws NumberFormatException, IOException {

		Scanner sc = new Scanner(System.in);
		int num = sc.nextInt();
		sc.close();
		int newNum = num; int cnt = 0;
		do {
			newNum = (newNum%10)*10 + (newNum/10+newNum%10)%10; 
			cnt++;
		}while(num!=newNum);
		System.out.println(cnt);
		
	}//main

```
