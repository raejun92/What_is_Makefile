타켓 : 의존관계
   명령어
타켓을 만드는데 의존관계(타켓을 만들기 위한 재료)를 사용하여 명령어를 수행

Phony Targets(포니 타겟)
포니 타겟은 실제 파일 이름을 나타내는 타겟 이름이 아니다. 
이것은 명백하게 make 요청을 하는 경우에 실행되는 명령을 위한 목적으로 사용된다. 
포니 타겟을 사용하는 이유는 두가지가 있는데, 첫번째는 동일한 이름의 파일을 사용한 충돌을 피하기 위함이고, 
두번째는 make 성능향상을 위함이다.

CC: 컴파일러
CFLAGS: 컴파일 옵션
OBJS: 중간 산물 Object 파일 목록
NAME(Target): 빌드 대상(실행 파일) 이름

$@: 현재 Target 이름
$^: 현재 Target이 의존하는 대상들의 전체 목록

OBJS = $(FILES:.c=.o)
CC = gcc
CFLAGS = -Wall -Wextra -Werror
FILES = ft_printf.c

OBJS = $(FILES:.c=.o) 매크로의 의미 
- Object 파일 목록 = FILSE에 입력된 .c파일을 .o(목적파일)로 바꿈
- .c에서 .o로 바뀔때 내장변수인 CC CFLAG가 동작

ar rc $@ $^
ar rc: 아카이브 파일을 생성(파일을 하나로 묶음)
Reading the manual for ar helps but I will explain it in more detail. 
ar -rcs is the most likely command you would use when using a Makefile to compile a library. 
r means that if the library already exists, replace the old files within the library with your new files. 
c means create the library if it did not exist. s can be seen to mean 'sort' (create a sorted index of) the library, 
so that it will be indexed and faster to access the functions in the library. Therefore, rcs can be seen to mean replace, create, sort.
