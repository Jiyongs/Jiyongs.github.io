---
title: "Coding Study #1:hatched_chick:"
date: 2019-04-22 20:00:28 -0400
categories: jekyll update
---

#**Q1. K번째 수**

> 배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하기
> :*정렬 알고리즘*



- **my solution** 

```
class Solution {
    public int[] solution(int[] array, int[][] commands) {
    int comLen = commands.length;

	int[] answer = new int[comLen]; // 정답 저장 배열 변수

	for (int i = 0; i < comLen; i++) {
		int len = commands[i][1] - commands[i][0] + 1; // commands 값 하나에서, 자른 후의 배열 크기 얻어옴
		int start = commands[i][0] - 1; // 자르기 시작 인덱스
		int end = commands[i][1]; // 자르기 끝 인덱스 + 1

		int[] cut = new int[len]; // 자른 array 저장 배열 변수

		// array를 잘라줌
		for (int j = 0; j < len; j++) {
			cut[j] = array[start];
			start++;
		}
		
		// 오름차순 정렬해줌
		cut = sort(cut);

		answer[i] = cut[commands[i][2] - 1];
	}

	return answer;
}

// 오름차순 정렬 메소드
public int[] sort(int[] array) {
	
	int len = array.length;
	int min_idx, tmp = 0;
	
	// 오름차순 정렬해줌
	for (int i = 0; i < len - 1; i++) {
		min_idx = i;
		for (int j = i + 1; j < len; j++) {
			if (array[j] < array[min_idx]) {
				min_idx = j;
			}
		}
		tmp = array[min_idx];
		array[min_idx] = array[i];
		array[i] = tmp;
	}
	return array;
}

}
```



- **other solution**

```
import java.util.Arrays;
class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];

    for(int i=0; i<commands.length; i++){
        int[] temp = Arrays.copyOfRange(array, commands[i][0]-1, commands[i][1]);
        Arrays.sort(temp);
        answer[i] = temp[commands[i][2]-1];
    }

    return answer;
}

}
```

-------

#**Q2. 가운데 글자 가져오기**

> 단어 s의 가운데 글자를 반환하는 함수 만들기



- **my solution** 

```
class Solution {
  public String solution(String s) {
      String answer = "";
      int len = s.length();
      if(len%2==0){
          answer += s.charAt(len/2-1);
          answer += s.charAt(len/2);
      } else {
          answer += s.charAt(len/2);
      }
      return answer;
  }
}
```



- **other solution**

```
class StringExercise{
    String getMiddle(String word){
        return word.substring((word.length()-1) / 2, word.length()/2 + 1);    
    }
}
```

-------

#**Q3. 윤년 2016년 요일 구하기**

>  두 수 a ,b를 입력받아 2016년 a월 b일이 무슨 요일인지 리턴하는 함수 만들기



- **my solution** 

```
class Solution {
  public String solution(int a, int b) {
		String answer = "";

		String[] week = { "SUN", "MON", "TUE", "WED", "THU", "FRI", "SAT" };

		int days = 0;
		for (int i = 1; i < a; i++) {
			if (i % 2 != 0) { // 홀수 월
				days += 31;
			} else if (i == 2) { // 2월
				days += 29;
			} else { // 2월 제외한 짝수 월
				days += 30;
			}
		}

		days += b;

		int yo = days / 7 / 7;
		answer = week[yo];

		return answer;
  }
}
```



- **other solution**

```
class TryHelloWorld
{
    public String getDayName(int a, int b)
    {
     String answer = " ";
        int[] monthDay={31,29,31,30,31,30,31,31,30,31,30,31};
        for (int i = 1; i < a; i++) {
            b+=monthDay[i-1];
        }
        switch(b%7){
        case 3:answer="SUN";break;
        case 4:answer="MON";break;
        case 5:answer="TUE";break;
        case 6:answer="WED";break;
        case 0:answer="THU";break;
        case 1:answer="FRI";break;
        case 2:answer="SAT";break;
        }
```


