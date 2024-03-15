# Linux
리눅스 공부

## virtual Box 설치

## Shell

bash shell : 최초의 유닉스 쉘인 Bourne Shell 과 호환되도록 만들어진 쉘
Csh (cShell) : BDS 계열 유닉스 사용자들이 선호하는 쉘
ksh (kornShell) : unix system 계열 유닉스 사용자들이 선호하는 쉘
tcsh : cShell 과 호환
ash :  Bourne shell 과 호환되는 또 다른 쉘

## BourneShell

$ - dollar sign
"#" - pound sign

root 권한 실행 (sudo) $sudo reboot , $sudo halt

root 사용자로 전환
    sudo su - root
    sudo su - (아무것도 안쓰면 root )
    sudo su (권한만 바뀐)


## 파일 시스템 구조
/
bin     : 바이너리 폴더 실행파일 두는 장소
boot
dev
etc     : registry 프로그램에 사용할 설정파일
home    : C:Users 와 같은 의미
media   : C: , D: 등의 의미
tmp     : 임시로 데이터를 저장
mnt
sbin    : 시스템 빈 어드민이 쓰는 실행파일
sys     : 시스템의 설정
usr
var     : 프로그램이 사용할 값들 데이터

상대경로 ../
절대경로 /

## 파일 경로와 순회
pwd     현재 디렉토리 경로를 출력
ls      디렉토리 목록 나열
cd      디렉토리를 변경

"~" 이 기호는 내(로그인한) 홈 디렉토리
내 홈 디렉토리 가고 싶을때 cd ~

상위로 이동
cd ../

두단계 위로
cd ../../

### ls
man ls  ls 의 도움말
ls      경로의 파일들 보기
ls -l   자세히

hello.java hello1.java hello2.java
있을때
ls hello[12].java 하면
hello1.java , hello2.java 나온다.


## 파일시스템을 위한 명령어들
mkdir   디렉토리 생성
rmdir   디렉토리삭제
touch   빈 파일 생성
mv      파일 이동 / 변경
rm      파일 삭제
cp      파일 복사

### ls -l 입력시 파일과 디렉토리 차이
drwxrwxr-x  workspace : 앞 D 가 디렉토리 의미
-rw-rw-r--  test.txt  : 앞 에 아무것도 없으면 파일

### mv
mv {대상 파일 } { 이동 위치}
mv test.txt workspace/

### rm
rm -r workspace/    :   디렉토리 안쪽의 모든 파일 (recursive)
rm -ri aa           :   상호작용을 추가하여 방어로직

### cp
cp text.txt test.cpy

## 파일 편집 및 관리

## 편집기
vi          :
GNU nano    :   트렌드하게 많이 쓰는것
Emacs       :
ed/ex       :

### vi

쉘 > vi 명령 모드 > 편집 > esc > :

쉘
vi name
vi +n name
vi -r name

vi 명령모드
i   :   *많이 쓴다 insert 모드 (현재 위치)
l
a   :   *현재위치 뒤에
A
o   :   *다음라인에 넣기
yy  :   한 줄 복사
yw  :   단어 복사
yl  :   문자 복사
p   :   붙여넣기


이동키
<- : h
-> : l
위 : k
아래 : j

편집

esc : 편집모드 종료

:명령어
q   :   나가기
w   :   저장
wq  :   저장하고 나가기

### nano
^ : ctrl 키를 의미

nano 파일명
editor 파일명

## 파일 찾기와 파일정보

### 파일 찾기
메뉴얼 = man find
find ./ -name *.java                            :   현재 디렉토리에서 파일 네임이 .java로 끝나는 파일
find . -name *.java -size +1c[옵션있다]          :   현재 디렉토리에서 사이즈가 1바이트 이상 (-1 : 1이하 )
find / -name *.java                             :   루트 디렉토리에서 전체 다 찾아라 -> 권한 수준을 체크하여 노출 없으면 permission denied

### 파일의 정보

cat
cat [파일이름]

haed
head -n2 [파일이름] : 위에서 두 줄

tail
tail -n2 [파일이름] : 뒤에서 두 줄

grep
grep [찾을 내용] [파일이름]
grep -i "hello" hello.java 대 소문자 무시

cmp : 파일내용 비교 차이나는 라인 출력
cmp hello.java hello2.java

diff : 차이점 소스 노출
diff hello.java hello2.java

file : 파일의 내용을 출력해준다.

## 유용한 명령어
history  : 지금까지 사용한 명령어

history -> 번호 체크 - > "!96" 이렇게 사용하면 해당 번호의 명령어 실행

">"  : 파일로 출력하기
hello.java > test.txt

echo : 화면에 출력하기
echo "hello" > test  : 파일로 출력
echo "okay" >> test : 덮어쓰기가 아니라 이어서 작성

|
cat test | ? : cat test 결과가 ?로 하이픈
cat test | grep he
ls -l | less
cat test | sort -r : 하이픈

;
touch test1 ; echt "okay~" >> test1 ; cat test1

## 파일 압축 관리
tar  : tape Archive

압축하기
tar -cf [파일명.tar] [같이 묶일 파일 a,b,c]
tar -zcf   [파일명.tar.gz] [같이 묶일 파일]
tar -cf test.tar *
tar -cf test.tar *.java

압축 풀기
tar -xvf [파일명.tar]
tar -zxvf [파일명.tar.gz]

-f  :   파일이름 지정
-c  :   파일을 tar로 묶음
-x  :   tar 압축을 푼다.
-v  :   내용을 자세히 출력
-z  :   gzip으로 압축하거나 해제함
-t  :   목록 출력
-p  :   파일 권한을 저장
-c  :   경로를 지정

## JDK 다운로드
웹에서 다운 받을때 "wget"
.tar 받아서 압축풀기

## 링크파일
ls -l 입력시
l.... 으로 시작하면 링크파일 (exe 파일)

링크 파일 만들기
ln [option].. target [...] [linkName[...]]
sybolic Link : option -s 부여하여 생성 파일 타입 l 원본과 다른 크기와 다른 생성일을 가지는 별도의 파일
hardlink: 원본과 똑같은 크기와 똑같은 생성일을 가진다.

ln hello helloln : 하드 링크 파일 생성
Helloln 을 수정하면 원본도 수정된다.
원본을 지워도 링크 파일은 남아있다. (링크 파일을 지워도 원본은 남아있다)

## 링크파일을 이용한 실행파일 리졸빙
$~/download/jdk1.8.0_161/bin/javac -version -> 자바 버전이 나온다
~/download/jdk1.8.0_161/bin/$ javac -version -> 자바 버전이 나오지 않는다(resolving Error)

리눅스는 명령어를 사용하면 실행파일을 찾는 resolving이 일어난다.
현재의 디렉토리에서도 파이을 찾지 않고
$PATH 에 등록된 환경변수의 경로에서 실행 파일을 찾는다
이러한 문제를 해결하기 위해서 링크 파일( 심볼릭)로 해결가능

~/download/jdk1.8.0_161/bin/$ java -version
리졸빙 에러
~/download/jdk1.8.0_161/bin/$ ./java -version
실행 된다.

리졸빙 에러는 echo $PATH 를 치면 나오는 경로에 실행 파일이 있는지 찾아본다.
현재는 없어서 에러

링크파일(심볼릭) 생성으로 해결하기
생성하려는 홈의 bin으로 이동 후 ($PATH 에 홈 디렉토리 bin이 등록되어있어서)
ln -s ~/경로/java java
ls -l 실행시 실행파일의 실제 경로와 파일타입 확인 가능

이후 javac hello.java -> .class 생성 -> java hello.class 등으로 사용가능

# 사용자가 여러명인( 프로필이) 환경에서 글로벌로 등록하기

1. 사용자 추가하기
    useradd : 사용자 추가
        useradd dragon : dragon 사용자 추가
    usermod : 사용자 변경
    userdel : 사용자 삭제

    사용자는 루트 환경의 설정파일을 저장하는 etc 디렉토리에서 확인가능
    cat /etc/psswd 또는 tail -n2 /etc/passwd

    비밀번호 추가
    sudo passwd dragon
    
    **
    tail -n3 /etc/passwd ->
    dragon:x:1001:1001::  id :: group 이다.

    이 상태로 로그인시 홈 디렉토리가 없기 때문에 경로가 안잡힌다
    sudo mkdir /home/dragon 사용자 별로 디렉토리를 만들어준다.
    소유자와 소유그룹을 지정해줘야 dragon으로 작업이 가능
                 소유자    그룹
    -rw-rw-r-- 1 root     root     9717760 Jan  1  2024 test.tar

    소유자 변경
    sudo chown [소유자] [디렉토리경로]
    sudo chown dragon  /home/testuser
    sudo chown [소유자:그룹] [디렉토리경로]
    sudo chown dragon:dragon  /home/testuser

2. 사용자를 추가하는 스크립트 파일 생성하여 쉽게 처리하기
    ~bin/adduser

    >useradd testuser
    tail -n2 /etc/passwd
    mkdir /home/testuser
    chown testuser:testuser /home/testuser
    echo "testuser user added"

    파일 생성후 실행 권한을 부여하여 실행파일로 만든다
    chmod [option] mode[mode] file
    -rwxr-xr-x text.txt
    "-" 파일의 타입
    3비트씩 끊어서 다음에 대한 정보를 표현
    rwx 소유자의 권한
    r-x 소유그룹의 권한
    r-x other의 권한

    r(100) : read , w(010) : write , x(001) : execute
    ex) 소유자에게 모든 권한, 그룹에 모든 권한, other에 모든 권한
    chmod 777 test.txt
    chmod [대상] [+-권한]
    대상 : u :user , g : group , o : other , a : all
    모두에게 rwx
    chmod a+rwx text.txt

3. 인자를 이용한 스크립트 파일로 변경
    ~bin/adduser

    useradd $1
    tail -n2 /etc/passwd
    mkdir /home/$1
    chown $1:$1 /home/$1
    echo "$1 user added"

    adduser test2user  -> adduser param1($1) param2($2) param3($3)

    *whereis adduser : adduser 가 있는곳
    which adduser : 실행되는 adduser , sudo which adduser : sudo 권한으로 실행되는 adduser

3.1. 향상된 사용자 추가 명령어
리눅스 에서 제공하는 스크립트
adduser , deluser

## 사용자 프롬프트 설정하기
ps1="$"
ps1="\d$" : 날짜 포함
ps1="\t$" : 시 포함

## 색상 변경
LS_COLORS = "di=0;33"

di = directory
fi = file
in = symbolic link
pi = fifo file
so = socket file
bd = block special file

텍스트 형식
0 = default color
1 = bold
4 = underline
5= flashing text
7 = reverse

텍스트 색상표
33 = orange 1= red .... 검색해보자

## 명령어 별칭
type ll : ls -alF의 별칭

alias 추가
alias ls = 'ls -l'

기본적으로 프로필에 적용한것이 아니기 때문에 로그아웃하고 들어오면 초기화 된다.

## 컴퓨터 켜고 끄기와 Run Level
초기화 스크립트 작성 위치
1) BIOS
2) Master Boot Record (MBR)
3) LILO or GRUB : 운영체제 선택기
4) Kernel
5) init: process number 1(PID = 1)
    -/linuxrc : load modules / initialize devices / exits
    -/sbin/init
        -/etc/inittab : run boot scripts
            -/etc/init.d/rcS
                -/etc/rcS.d/S* scripts
                -/ect/rc.boot/*
6) Run Levels
    /etc/rc0.d rc1.d...... 등이 있다.

34강 10분 