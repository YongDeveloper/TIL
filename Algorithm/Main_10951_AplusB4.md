# 알고리즘

## Java의 EOF(End of FIle) 처리 
- 알고리즘 문제에서 Testcase가 정확하게 주어져 있지 않을때 처리하는 방법
- Scanner에서 처리 방법

```java
Scanner sc= new Scanner(System.in);
while(sc.hasNext()) {
	int num1 = sc.nextInt();
	int num2 = sc.nextInt();
	System.out.println(num1+num2);
}
```


- bufferedReader에서 처리방법

```java
bufferedReader br = new bufferedReader(new InputStreamReader(System.in));
String str = "";

while((str = br.readLine()) !=NULL){

}

```
