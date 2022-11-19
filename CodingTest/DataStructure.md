# Stack

https://gmlwjd9405.github.io/2018/08/03/data-structure-stack.html

`한 쪽 끝에서만 자료를 넣고 뺄 수 있는 LIFO(Last In First Out) 형식의 자료 구조`

**스택(Stack)의 구현**
문제의 종류에 따라 배열보다 스택에 데이터를 저장하는 것이 더 적합한 방법일 수 있다.

- 배열과 달리 스택은 상수 시간에 i번째 항목에 접근할 수 없다.
- 하지만 스택에서 데이터를 추가하거나 삭제하는 연산은 상수 시간에 가능하다.
- 배열처럼 원소들을 하나씩 옆으로 밀어 줄 필요가 없다.

**스택(Stack)의 사용 사례**

재귀 알고리즘

- 재귀적으로 함수를 호출해야 하는 경우에 임시 데이터를 스택에 넣어준다.
- 재귀함수를 빠져 나와 퇴각 검색(backtrack)을 할 때는 스택에 넣어 두었던 임시 데이터를 빼 줘야 한다.
- 스택은 이런 일련의 행위를 직관적으로 가능하게 해 준다.
- 또한 스택은 재귀 알고리즘을 반복적 형태(iterative)를 통해서 구현할 수 있게 해준다.
- 웹 브라우저 방문기록 (뒤로가기)
- 실행 취소 (undo)
- 역순 문자열 만들기
- 수식의 괄호 검사 (연산자 우선순위 표현을 위한 괄호 검사)
  Ex) 올바른 괄호 문자열(VPS, Valid Parenthesis String) 판단하기
- 후위 표기법 계산

BOJ
https://www.acmicpc.net/problem/1406
https://www.acmicpc.net/problem/1918

# Queue

https://gmlwjd9405.github.io/2018/08/02/data-structure-queue.html

`컴퓨터의 기본적인 자료 구조의 한가지로, 먼저 집어 넣은 데이터가 먼저 나오는 FIFO(First In First Out)구조로 저장하는 형식`

**큐(Queue)의 사용 사례**
데이터가 입력된 시간 순서대로 처리해야 할 필요가 있는 상황에 이용한다.

- 너비 우선 탐색(BFS, Breadth-First Search) 구현
  처리해야 할 노드의 리스트를 저장하는 용도로 큐(Queue)를 사용한다.
  노드를 하나 처리할 때마다 해당 노드와 인접한 노드들을 큐에 다시 저장한다.
  노드를 접근한 순서대로 처리할 수 있다.
- 캐시(Cache) 구현
- 우선순위가 같은 작업 예약 (인쇄 대기열)
- 선입선출이 필요한 대기열 (티켓 카운터)
- 콜센터 고객 대기시간
- 프린터의 출력 처리
- 윈도 시스템의 메시지 처리기
- 프로세스 관리

BOJ
https://www.acmicpc.net/problem/1158

# Deck

덱(deque, "deck"과 발음이 같음 ← double-ended queue)은 양쪽 끝에서 삽입과 삭제가 모두 가능한 자료 구조의 한 형태이다.

두 개의 포인터를 사용하여, 양쪽에서 삭제와 삽입을 발생시킬 수 있다. 큐와 스택을 합친 형태로 생각할 수 있다.

**Deck의 사용사례**

이 자료구조를 이용하면 A1,A2,...,AN이 주어질 때 임의의 상수 B에 대해 Ai−B ~ Ai 의 최대, 최소 같이 데이터를 가진 정보들을 특정한 기준에 따라 나열할 때 가장 우선순위가 높은 값을 모든 i에 대해 시간 복잡도 O(N)으로 찾아줄 수 있다.

BOJ
https://www.acmicpc.net/problem/11003

https://kimtaehyun98.tistory.com/82

<!-- 모노톤 큐 -->

https://stonejjun.tistory.com/126
