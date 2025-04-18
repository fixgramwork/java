# 📚 문자열 앞의 n글자 자르기 문제 풀이 정리

## 🤗 문제 설명
문자열 `my_string`과 정수 `n`이 매개변수로 주어질 때, `my_string`의 **앞의 n글자로 이루어진 문자열**을 반환하는 `solution` 함수를 작성하세요.

---

## 💬 문제 조건
- `my_string`은 숫자와 알파벳으로 이루어져 있습니다.
- 1 ≤ `my_string`의 길이 ≤ 1,000
- 1 ≤ `n` ≤ `my_string`의 길이

---

## 💬 입출력 예
  입력: ProgrammerS123, 11  
  출력: ProgrammerS

 입력: He110W0r1d, 5  
 출력: He110  

---

## 📚 문제 풀이

### 풀이 1 — for문과 charAt() 사용  
```java
class Solution {
    public String solution(String my_string, int n) {
        String answer = "";
        // for문을 이용해 문자열을 한 글자씩 가져와서 answer에 추가
        for (int i = 0; i < n; i++) {
            answer += my_string.charAt(i);  // charAt으로 한 글자씩 가져오기
        }
        return answer;
    }
}
```

### 풀이 2 — substring() 사용  
```java
class Solution {
    public String solution(String my_string, int n) {
        // substring(0, n)으로 앞의 n글자를 바로 잘라서 반환
        return my_string.substring(0, n);
    }
}
```

### 풀이 3 — StringBuilder 사용  
```java
class Solution {
    public String solution(String my_string, int n) {
        String answer = "";
        StringBuilder sb = new StringBuilder();
        String[] arr = my_string.split("");  // 문자열을 한 글자씩 배열로 쪼갬

        for (int i = 0; i < n; i++) {
            sb.append(arr[i]);  // StringBuilder에 추가
        }

        answer = sb.toString();  // String으로 변환
        return answer;
    }
}
```

### 풀이 4 — split() 사용  
```java
class Solution {
    public String solution(String my_string, int n) {
        String answer = "";
        String[] str = my_string.split("");  // 문자열을 배열로 쪼개기

        for (int i = 0; i < n; i++) {
            answer += str[i];  // 배열에서 앞의 n개를 answer에 추가
        }

        return answer;
    }
}
```

### 풀이 5 — Pattern과 Matcher 사용  
```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;

class Solution {
    public String solution(String my_string, int n) {
        // 정규식을 통해 my_string이 알파벳/숫자로 이루어졌는지 확인
        Matcher matcher = Pattern.compile("[A-Za-z0-9]").matcher(my_string);
        if (1 <= n && n <= my_string.length() && matcher.find()) {
            // 조건 만족 시 substring으로 자르기
            return my_string.substring(0, n);
        }
        // 조건 불만족 시 원본 반환 (사실 문제 조건상 의미 없음)
        return my_string;
    }
}
```

---

## 🧐 추가 설명
### 정리
 - [풀이 1] : 비효율적 ❌
 - [풀이 2] : 가장 빠르고 깔끔, 추천 ✅
 - [풀이 3] : 빠르긴 하지만 조금 길어짐 ✅
 - [풀이 4] : 비효율적 ❌
 - [풀이 5] : 문제 조건상 불필요 ❌

---

## 📢 결론

 가장 추천하는 방법 → [풀이 2]
 - 코드 짧고, 가독성 좋고, 속도도 빠르다!