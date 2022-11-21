<head>
<style>
@font-face {
  font-family: 'Pretendard-Regular';
  src: url('https://cdn.jsdelivr.net/gh/Project-Noonnu/noonfonts_2107@1.1/Pretendard-Regular.woff')
    format('woff');
  font-weight: 400;
  font-style: normal;
}

body {
font-family: 'Pretendard-Regular';
}
</style>

</head>

# Scanner EOP / Buffer EOP

- ✍🏻 **Recorded Date** : 2022년 11월 07일 오후 09:00
- 🔖 **Notion** : [Notion에서 보기](https://6suk.notion.site/Scanner-EOP-Buffer-EOP-2942e04f1f7148d69f80b2c543b7d208)
  <br>
  <br>

## 🔸 EOP(End Of File)

- 데이터 소스로부터 더 이상 읽을 수 있는 데이터가 없을때
- Scanner / BufferedReader의 EOF 처리 방법
- 참고 코드

  ```java
  import java.io.*;
  import java.util.*;

  public class Main_10951 {

  	public static void main(String[] args) throws IOException {
  		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
  		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
  		StringTokenizer st;
  		String str = "";

  		while ((str = br.readLine()) != null && !str.isEmpty()) {
  			st = new StringTokenizer(str, " ");
  			int a = Integer.parseInt(st.nextToken());
  			int b = Integer.parseInt(st.nextToken());

  			bw.write((a + b) + "\n");
  			bw.flush();
  		}

  		br.close();
  		bw.close();
  	}

  }
  ```

<br><br>

## ◽ Scanner

```java
Scanner sc = new Scanner(System.in);

while(sc.hasNextLine()){
	sc.nextLine();
}

while(sc.hasNext()){
	sc.next();
}
```

<br><br>

## ◽ BufferedReader

```java
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
String input = "";

//1
while ((input = br.readLine())!= null){...} br.close();

//2 (권장)
while ((input = br.readLine())!= null && input.isEmpty()){...} br.close();

//3
while (!(input = br.readLine()).equls("")){...} br.close();
```

- `1번` 코드는 입력 자체가 파일로 들어온다면 `EOF`를 정상적으로 처리 가능하다. 하지만 IntelliJ같은 IDE에서는 입력의 끝을 알 수 없다. (EOF를 찾지 못해 프로그램이 끝나지 않는다.)
- `2번` 코드는 입력의 끝에 `Enter`를 한번 더 입력하면 그 입력을 `EOF`로 판별하여 처리한다.
- `3번` 코드는 역으로 IDE에서는 `Enter`로 `EOF`를 찾을 수 있지만, 입력 자체가 `파일`이라면 `RuntimeErroro`가 뜬다.
- `isEmpty()` : 문자열의 길이가 0인 경우에, true를 리턴

</span>