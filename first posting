---
title: "Coding Study #1"
date: 2019-04-22 20:00:28 -0400
categories: jekyll update
---

Q1. K번째 수
배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하기.
--> 정렬 알고리즘

- my solution
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

- other solution
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

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
