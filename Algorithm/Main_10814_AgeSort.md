# 알고리즘
[백준 10814번: 나이순 정렬](https://www.acmicpc.net/problem/10814)
```java
public class Main_10814_AgeSort {

	public static class Member implements Comparable <Member>{

		int age;
		String name;
		
		public Member(int age, String name) {
			this.age = age;
			this.name = name;
		}

		public int getAge() {
			return age;
		}

		public String getName() {
			return name;
		}

		public int compareTo(Member o) {
			if(this.age > o.age) return 1;
			else if(this.age < o.age) return -1;
			else return 0;
			// 만약 나이순 정렬 후 이름 오름차순 정렬이라면
			// else return getName().compareTo(o.name);
		}
		
	}
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		
		List<Member> list = new ArrayList<>();
		for (int i = 0; i < N; i++) {
			st = new StringTokenizer(br.readLine());
			list.add(new Member(Integer.parseInt(st.nextToken()),st.nextToken()));
		}
		
		Collections.sort(list);
		
		for (Member member : list) {
			System.out.println(member.age+" "+member.name);
		}
		
	}//main

}//class

```
- 나이와 이름을 List에 담고 Member라는 class를 만들어서 정렬하였다. 
- Comparator를 이용하지 않고 Compareble을 이용하였다.
