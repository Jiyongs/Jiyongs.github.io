---
title: "Coding Study #3:hatched_chick:"
date: 2019-05-01 18:50:00 -0400
categories: jekyll update
---

#**<u>Language : Java</u>**

#**Q1. 같은 숫자는 싫어**

> 배열 arr에서 연속적으로 나타나는 숫자는 제거하고 남은 수들을 return 하는 solution 함수 만들기

- **my solution** 

```
import java.util.*;

public class Solution {
			public int[] solution(int []arr) {
                
            // 답을 임시 저장할 ArrayList 생성
	        ArrayList<Integer> list = new ArrayList<>();
                
            // 인자값인 배열 arr만큼 for문 돌림
	        int len = arr.length;
	        for(int i = 0; i < len; i++){
                // list에 중복을 제거한 arr의 값을 넣음
	            if(!list.contains(arr[i])){
	                list.add(arr[i]);
	            } // 중복이지만, 앞 뒤 값이 다를 때도 list에 넣음
                else if(arr[i]!=arr[i-1])
                    list.add(arr[i]);
	        }
	        
            // list에 임시 저장한 답을 answer[]에 넣어주고 return!
	        int len2 = list.size();
	        int[] answer = new int[len2];

	        for(int i = 0; i < len2; i++){
	            answer[i] = list.get(i);
	        }

	        return answer;
		}
}
```



- **other solution**

```
import java.util.*;

public class Solution {
    public int[] solution(int []arr) {
        ArrayList<Integer> tempList = new ArrayList<Integer>();
        
        // arr의 이전 비교값을 저장할 변수 선언
        int preNum = 10;
        
        // preNum과 arr의 값을 비교하며, 앞 뒤 값이 다를 때만 tempList에 add함
        for(int num : arr) {
            if(preNum != num)
                tempList.add(num);
            preNum = num;
        }       
        
        // answer 배열에 tempList값을 넣어 리턴함
        int[] answer = new int[tempList.size()];
        for(int i=0; i<answer.length; i++) {
            answer[i] = tempList.get(i).intValue();
        }
        return answer;
    }
}
```

-------

#**Q2. 나누어 떨어지는 숫자 배열**

> array의 각 element 중 divisor로 나누어 떨어지는 값을 오름차순으로 정렬한 배열을 반환하는 함수, solution 만들기.
divisor로 나누어 떨어지는 element가 하나도 없다면 배열에 -1을 담아 반환하기.

- **my solution** 

```
import java.util.*;

class Solution {
	 public int[] solution(int[] arr, int divisor) {
	      int[] answer;
	      
	      ArrayList<Integer> list = new ArrayList<>();
	      for(int num : arr){
	          if(num % divisor == 0) {
	              list.add(num);
	        }
	      }
         
	      list.sort(null);
	     
         int len2 = list.size();
	      if(len2 == 0){
	    	  answer = new int[1];
	    	  answer[0] = -1;
	          return answer;
	      }
	      
	      answer = new int[len2];
	      for(int i = 0; i < len2; i++){
	          answer[i] = list.get(i);
	      }
	      
	      return answer;
	  }
}
```



- **other solution**

```
import java.util.*;

class Solution {
	 public int[] solution(int[] arr, int divisor) {
        // stream과 람다식을 사용함
	     return Arrays.stream(array).filter(factor -> factor % divisor == 0).toArray();
}

```

-------

#**Q3. 두 정수 사이의 합**

>  두 정수 a, b가 주어졌을 때 a와 b 사이에 속한 모든 정수의 합을 리턴하는 함수 만들기

- **my solution** 

```
class Solution {
  public long solution(int a, int b) {
      
      long answer = 0;
      
      // a < b 인 경우
      if(a<b){
        while(a!=b+1) {
           answer += a++;
         }
       // b < a 인 경우
      } else {
          while(b!=a+1){
              answer += b++;
          }
      }
      
      return answer;
  }
}
```



- **other solution**

```
class Solution {
  public long solution(int a, int b) {
      long answer = 0;
      for (int i = ((a < b) ? a : b); i <= ((a < b) ? b : a); i++) 
          answer += i;

      return answer;
  }
}

```


