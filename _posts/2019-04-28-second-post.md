---
title: "Coding Study #2:hatched_chick:"
date: 2019-04-28 18:50:00 -0400
categories: jekyll update
---

#**<u>Language : Java</u>**

#**Q1. 완주하지 못한 선수**

> 배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하기
> :*정렬 알고리즘*

- **my solution** 

```
import java.util.*;

class Solution {
	public String solution(String[] participant, String[] completion) {
		String answer = "";
        // Arrays클래스의 sort()메소드로 오름차순 정렬
		    Arrays.sort(participant);
        Arrays.sort(completion);
        
        // 완주한 선수의 수만큼 반복문 실행
        int len = completion.length;
        for(int i = 0; i < len; i++){
            // participant와 completion의 인덱스가 같은데 값이 다를 때, 그 선수를 리턴
            if(!participant[i].equals(completion[i])){
                answer = participant[i];
                return answer;
            }
        }
        
        // for문에서 빠져나올 시, 마지막 참가자를 리턴
        answer = participant[len];
        return answer;
        
	}
}
```



- **other solution**

```
import java.util.HashMap;

class Solution {
    public String solution(String[] participant, String[] completion) {
        String answer = "";
        HashMap<String, Integer> hm = new HashMap<>();
        for (String player : participant) hm.put(player, hm.getOrDefault(player, 0) + 1);
        for (String player : completion) hm.put(player, hm.get(player) - 1);

        for (String key : hm.keySet()) {
            if (hm.get(key) != 0){
                answer = key;
            }
        }
        return answer;
    }
}
```

-------

#**Q2. 모의고사**

> 1번 문제부터 마지막 문제까지의 정답이 순서대로 들은 배열 answers가 주어졌을 때, 가장 많은 문제를 맞힌 사람이 누구인지 배열에 담아 return 하도록 solution 함수 만들기
> :*완전탐색 알고리즘*

`**완전탐색 알고리즘**`
> 컴퓨터의 빠른 계산 능력을 이용해 가능한 경우의 수를 일일이 나열하면서 답을 찾는 방법

- **my solution** 

```
import java.util.*;

class Solution {
    
    // 채점 메소드
public int getScore(int answers[], int patterns[]){
    int score = 0;
    int ansLen = answers.length;
    int patLen = patterns.length;
    
    for(int i = 0; i < ansLen; i++){
        if(answers[i] == patterns[i%patLen]){
            score++;
        }
    }
    return score;
}
    
    public int[] solution(int[] answers) {
        // 찍는 패턴별 배열 선언
        int[] supoOne = {1, 2, 3, 4, 5};
        int[] supoTwo = {2, 1, 2, 3, 2, 4, 2, 5};
        int[] supoThree = {3, 3, 1, 1, 2, 2, 4, 4, 5, 5};
        
        // 점수를 담음
        int[] score = new int[3];
        score[0] = getScore(answers, supoOne);
        score[1] = getScore(answers, supoTwo);
        score[2] = getScore(answers, supoThree);
        
        // 최고점을 구함
        int maxScore = score[0];
        
        if(maxScore<score[1])
            maxScore = score[1];
        if(maxScore<score[2])
            maxScore = score[2];
        
        // 최고점을 맞은 사람 번호를 구함
        Vector<Integer> bestSupo = new Vector<Integer>();
        
        for(int i = 0; i < 3; i++){
            if(maxScore==score[i]){
                bestSupo.addElement(i+1);
            }
        }
        
        // 최고점을 맞은 사람을 저장
        int answer[] = new int[bestSupo.size()];
        for(int i =0; i<answer.length; i++){
            answer[i] = bestSupo.get(i);
        }
        return answer;
    }
}
```



- **other solution**

```
import java.util.*;

class Solution {
    public int[] solution(int[] answers) {
        int[] arr = new int[3];
        int[] a = {5,1,2,3,4};
        int[] b = {5,2,1,2,3,2,4,2};
        int[] c = {5,3,3,1,1,2,2,4,4,5};

        for(int i = 0; i < answers.length; i++){
            if(answers[i] == a[(i+1)%5]) arr[0]++;
            if(answers[i] == b[(i+1)%8]) arr[1]++;
            if(answers[i] == c[(i+1)%10]) arr[2]++;
        }

        int max = arr[0];

        if(max < arr[1]) max = arr[1];
        if(max < arr[2]) max = arr[2];

        if(max == arr[0] && max == arr[1] && max == arr[2]) return new int[]{1,2,3};
        else if(max == arr[0] && max == arr[1]) return new int[]{1,2};
        else if(max == arr[0] && max == arr[2]) return new int[]{1,3};
        else if(max == arr[1] && max == arr[2]) return new int[]{2,3};
        else if(max == arr[0]) return new int[]{1};
        else if(max == arr[1]) return new int[]{2};

        return new int[]{3};
    }
}
```

-------

#**Q3. 체육복**

>  전체 학생의 수 n, 체육복을 도난당한 학생들의 번호가 담긴 배열 lost, 여벌의 체육복을 가져온 학생들의 번호가 담긴 배열 reserve가 매개변수로 주어질 때, 체육수업을 들을 수 있는 학생의 최댓값을 return 하도록 solution 함수 만들기
> :*탐욕법(Greedy) / 탐욕 알고리즘*

`**탐욕 알고리즘**`
> 매순간 최적이라고 생각되는 것을 선택해 나가는 방식

- **my solution** 

```
...
```



- **other solution**

```
class Solution {
    public int solution(int n, int[] lost, int[] reserve) {
        int answer = 0;
        answer = n;

        for(int i = 0; i < lost.length; i++) {
            boolean rent = false;
            int j = 0;
            while(!rent) {
                if(j == reserve.length)                   break;
                if(lost[i] == reserve[j])                {reserve[j] = -1; rent=true;}
                else if(lost[i] - reserve[j] == 1 )      {reserve[j] = -1; rent=true;}
                else if(lost[i] - reserve[j] == -1)      {reserve[j] = -1; rent=true;}
                else                                     {j++;                      }
            }
            if(!rent) answer--;
        }
        return answer;
    }
}
```


