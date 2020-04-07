# 알고리즘
[백준 1931번:회의실배정](https://www.acmicpc.net/problem/1931)
```java
public class Main_1931_MeetingRoom {

	public static class Member implements Comparable<Member>{

		int start_point;
		int finish_point;
		
		public Member(int start_point, int finish_point) {
			this.start_point = start_point;
			this.finish_point = finish_point;
		}
		
		@Override
		public String toString() {
			return start_point + " " + finish_point;
		}

		@Override
		public int compareTo(Member o) {
			if(this.finish_point > o.finish_point) return 1;
			else if(this.finish_point < o.finish_point) return -1;
			else return Integer.compare(start_point, finish_point);
		}
	}
	
	public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		
		List<Member> list = new ArrayList<>(); 
		int cnt = 1;
		
		for (int i = 0; i < N; i++) {
			st = new StringTokenizer(br.readLine());
			list.add(new Member(Integer.parseInt(st.nextToken()),
						Integer.parseInt(st.nextToken())));
		}
		Collections.sort(list);
		
		int end = list.get(0).finish_point;
		//System.out.println(list.get(0).toString());
		
		for (int i = 1; i < list.size(); i++) {
			if(end <= list.get(i).start_point ) {
				cnt++;
				//System.out.println(list.get(i).toString());
				end = list.get(i).finish_point;
			}
		}
		
		System.out.println(cnt);
		
	}//main

}//class

```
- 그리디 문제 : 
- 회의 시작 시간과 끝나는 시간을 Member 클래스를 만들어 list에 담는다.
- 끝나는 시간을 기준으로 정렬을 실행한다.
- 첫번째 끝나는 시간보다 큰 회의 시작 시간을 카운트하여 답을 도출한다. 
