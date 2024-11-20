# 1D-Number-Puzzle
요구 사항 : 간단한 숫자 퍼즐 출력

## 프로그램 구성

### int[] puzzle과 int turn을 관리
- puzzle이 오름차순인지 검사
  - 오름차순으로 정렬되면 "축하합니다! n턴만에 퍼즐을 완성하셨습니다!" 출력 후 프로그램 종료
  - 오름차순이 아니면 교환할 두 숫자를 입력받음
    - 입력받은 두 숫자의 위치를 바꿈
    - 위치를 교환한 후 turn과 함께 현재 상태 출력
- 숫자의 위치를 바꿀 때마다 turn을 1씩 증가

### 교환할 두 숫자를 입력받음
- 두 숫자를 입력받아서 형태가 올바른지 검사
  - 올바르지 않으면 "잘못 입력하셨습니다. 다시 입력해 주세요." 출력 후 다시 입력받음
  - 올바르지 않은 입력 예시
    - 입력이 숫자 하나  
    - 입력이 1 미만, 8 초과
    - 입력 시작에 공백
    - 문자로 입력 등등
  - 두 숫자의 형태가 올바르면 숫자 배열 형태로 반환

### 두 숫자의 위치를 교환
- 교환할 두 숫자를 가진 배열과, 교환할 대상인 배열(puzzle)을 받음
- puzzle 속에서 교환할 두 숫자의 위치를 바꿈
- 교환이 완료된 puzzle 배열을 반환


## 겪은 문제상황

### 교환할 두 숫자 사이의 스페이스 한 칸 가능
- split(",|, ")을 이용해서 두 숫자를 구분하려고 코드 작성
- "5, 6" 처럼 쉼표 뒤에 스페이스 한 칸 있으면 예외 발생
  - 해결 : 구분자의 순서를 바꿔서 해결 - split(", |,")

### 시작에 공백이 있는 경우 예외 발생
- " 5,6" 처럼 공백으로 시작하는 경우 예외가 발생해야 하는데 정상 처리됨
  - 원인 : next()를 사용했더니 입력 시 빈 칸을 자동으로 제거
  - 해결 : nextLine()를 사용해서 빈 칸을 포함한 한 줄 전체를 입력받음

### 범위를 초과하는 입력을 한 뒤에 정상적인 입력을 했을 때 예외 발생
- 교환할 두 숫자를 받는 메서드와, 받은 두 숫자를 검증하는 메서드를 작성함
- 검증하는 메서드에서 검증 실패 시, 두 숫자를 받는 메서드를 다시 실행하도록 작성함 -> 재귀 발생
  - 해결 : 재귀 호출을 없애고 교환할 두 숫자를 받는 메서드에 while 반복문을 설치