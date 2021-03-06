# Regular Expression
## 문법
* 한 글자 매칭
  - `.` : 임의의 한글자 (개행문자(new line) 제외, 개행문자 포함하려면 `s` flag)
  - `\d` : 숫자(digit)
  - `\D` : 숫자 아닌 글자
  - `\s` : 화이트스페이스 (`\p{White_Space}`)
  - `\S` : 화이트스페이스 아님
  - `\w` : 단어 구성문자 (`\p{Alphabetic} + \p{M} + \d + \p{Pc} + \p{Join_Control}`)
  - `\W` : 단어 아님
* 대응되는 문자들
  - `[xyz]` : x, y, z 중 한 글자 (or) 매치
  - `[^xyz]` : x, y, z를 제외한 한 글자
  - `[a-z]` : a부터 z까지 중 한 글자
  - `[[:alpha:]]` : ASCII 문자 중 한 글자 = `[A-Za-z]`
  - `[[:^alpha:]]` : ASCII 문자가 아닌 한 글자
  - `[x[^xyz]]` : y, z를 제외한 한 글자
  - `[a-y&&xyz]` : a부터 y까지 "그리고" x,y,z 중 한글자 - 즉, x 또는 y
  - `[0-9&&[^4]]` : 0부터 9까지 "그리고" 4는 제외
  - `[0-9--4]` : 0부터 9까지, 4는 제외
  - `[a-g~~b-h]` : 'a부터 g까지' 중에서 'b부터 h까지' 차집합
  - `[\[\]]` : [ 또는 ]
* 반복
  - `x*` : 없거나 x의 여러번 반복 (greedy)
  - `x+` : x 한개 또는 여러번 반복
  - `x?` : 없거나 x 한개
  - `x*?` : 없거나 x의 여러번 반복 (lazy)
  - `x+?` : x 한개 또는 여러번 반복 (lazy)
  - `x??` : 없거나 x 한개 (lazy)
  - `x{n}` : x가 정확히 n개 매치
  - `x{n,}` : x가 적어도 n개 (lazy)
  - `x{n,m}` : x가 적어도 n개, 최대 m개 매치 (greedy)
  - `x{n,m}?` : x가 적어도 n개, 최대 m개 (lazy)
  

* empty match
  - `^` : 텍스트의 시작
  - `$` : 텍스트의 끝

* 그룹핑
  - `(exp)` : 열린 괄호에 따라 매겨지는 번호 그룹
  - `(?P<name>exp)` : `name`으로 이름 붙여진 그룹(번호도 매겨짐)
  - `(?:exp)` : 그룹으로 잡지 않음

* 플래그 설정
  - `(?flags)` : 현재 그룹에 플래그들 설정
  - `(?flags:exp)` : `exp`에 플래그들 설정
  - `(?-flags)` : 플래그 설정 해제
  - 모든 플래그는 특별히 지정하지 않으면 해제되어 있음
    - `i` : 대소문자 구분없음
    - `m` : 멀티라인 모드 (^와 $는 라인의 시작과 끝)
    - `s` : `.`에 `\n`도 허용
    - `U` : `x*`와 `x*?`의 의미를 바꿈
    - `u` : 유니코드 지원
    - `x` : 화이트스페이스 무시히고 `#`로 시작하는 라인 코멘트 허용
  
  