# 0329
# 메모리
- 컴퓨터의 메모리는 데이터를 보관하는 장소
- 8 bits단위로 주소가 지정됨.
- 4byte = 32bits
# 포인터
- 포인터는 메모리 주소값을 가지는 변수이다.
- 메모리주소를 저장하는 변수!
- `&` 는 그 변수(포인터)의 주소를 추출하는 연산자 이다.
- `*`
    1. 포인터 형식을 선언할때
    2. 포인터의 주소가 가르치는 값을 의미
# 포인터와 배열
- ``배열의 이름``은 ``배열의 시작 주소``를 저장하는 ``포인터 변수``이다(단 그값을 변경할 수 없음)

# 포인터 arithmetic
- `*a`와 `a[0]`는 동일한 의미이다. (첫번째 값을 의미하기 때문)
- `*(a+1)`은 `a[1]`과 동일하다.
- `*(array + i)` = `array[i]`

# 동적 메모리 할당
- 변수를 선언하는 대신!, 프로그램의 요청으로 메모리를 할당 하는것
- `malloc`함수를 호출하여 동적메모리 할당을 요청하면, 요구하는 메모리를 할당 해 준다.

# `malloc`함수
```c
int * p;
p = (int *)malloc(40);
// int *: malloc이 반환하는 주소는 타입이 없는 주소 (* void)이다. 정수들을 저장하기 위해서 이것을 int *로 변환다.
// malloc(40): 할당받을 메모리의 크기를 byte단위로 지정한다. 여기서는 10개의 정수를 저장하기 위해 40byte를 요청했다.
if (p==NULL) {
  // 동적 메모리 할당 실패   
}
```
```
p[0] = 12;
p[1] = 24;
* (p+2) = 36;

```
- malloc으로 할당 받은 메모리는 보통의 배열처럼 사용할 수 있다.

# 배열키우기
- 동적으로 할당된 배열은 공간이 부족할 경우 더 큰 배열을 할당하여 사용할 수 있다.
- 새로운 공간을 할당 받고 -> 이사를 시킨다. (그럼 원래 있던 메모리는 어떻게 되는가? `garbage`)
- `garbage`문제는 나중에 다시 다루어 봅시다.
- `array = tmp` (tmp가 가지고 있는 주소를 array에 준다. )
## 그냥 배열에 공간을 지정해서 선언 했을 경우. `array[4]`
- `array = tmp` (배열을 키울 수 없다.) 왜냐하면 ``배열의 이름``은 ``배열의 시작 주소``를 저장하는 ``포인터 변수``이다(**단 그값을 변경할 수 없음**)
- 따라서 공간을 주고 싶으면 `int * p = (int *)malloc(4*sizeof(int))`과 같이 포인터 형식으로 지정해 주어야 한다. 왜냐하면 포인터이름 즉 배열의 시작수소는 변경할 수 있기 때문이다.

# 문자열
- c언어에서 문자열을 저장하는 방법은 문자배열을 만들어서 한칸마다 한글자식 저장 하는 것이다.
## string literal
- `char *str = "hello";` -> 이렇게 정의된 문자열은 수정이 불가능 하다.
- 전혀다른 문자를 가르키게 할 수 는 있다.

# string.h 라이브러리 함수
- `strcpy` : 복사
- `strlen` : 길이
- `strcat` : 합치기
- `stccmp` : 비교

# 문자열들의 저장
- `char buffer; scanf("%s", buffer);` :문자열에 입력값을 받을 때는 `&buffer`라고 입력하지 않는다. 정수일때는 `&`를 통해 해당 변수의 주소를 참조 시켜주어야 하나, 배열은 배열 이름자체가 시작값의 주소이기때문에 필요가 없다.
- `char *words[100]` -> `words`라는 배열을 만드는데, 이 배열에 저장되는 각각의 type은  ``포인터``이고, 이 포인터가 가르키는 값의 ``타입``은 `char`이다.  

# 파일로부터 읽기
- `FILE *  `

# 연습문제 1. scanf -> gets
- scanf는 여러가지 문제가 있다. 변수에 10byte만 할당하더라도, 20byte를 (혹은 더 많이) 입력 받을 수 있다.
- 따라서 `fgets` 를 사용한다. `fgets`는 엔터키 까지 인식한다.

```c
int read_line(char str[], int n){
  int ch, i = 0;
  while ((ch = getchar()) != `\n`)
    if (i < n) {
      str[i++] = ch;     
    }
  str[i] = '\0';
  return i;
}
```

# 연습문제 2. 압축하기
- 공백문자인 경우 직전에 복사한 문자가 공백이 아니라면 공백을 복사하고, 공백이라면 복사하지 않는다.
```c
int read_line_with_copression (char str[], int n){
  int ch, pre = '\0', i = 0;

  while((ch = getchar()) == " ");
  while (ch != '\n'){
    if(i < n-1 && !(prev==' ') && ch == '  ')
      str[i++] = ch;
    prev = ch;
    ch = getchar();
  }
  if (i>0 && str[i-1]==''){
    str[i-1] = '\0';
    return i-1;
  }
  str[i] = '\0';
  return i;
}
```

# 전화번호부 v1.0
## 자료구조
- 프로그래밍을 만들때 제일 먼저 생각해야 할것은 ``자료구조`` 이다.
`char * names[100]; char * number[100]` : **문자형 포인터**

## strdup와 strcpy
### strdup
- `strdup`: string.h 라이브러리가 제공한다.
- `strdup(복제)` 메모리 길이가 같은 새로운 배열을 하나 만들고, 원래 문자열을 새로운 배열에 집어 넣고, 새로운 배열의 주소를 반환한다.  
