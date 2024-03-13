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

## ls
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

# ls -l 입력시 파일과 디렉토리 차이
drwxrwxr-x  workspace : 앞 D 가 디렉토리 의미
-rw-rw-r--  test.txt  : 앞 에 아무것도 없으면 파일

# mv
mv {대상 파일 } { 이동 위치}
mv test.txt workspace/

# rm
rm -r workspace/    :   디렉토리 안쪽의 모든 파일 (recursive)
rm -ri aa           :   상호작용을 추가하여 방어로직

# cp
cp text.txt test.cpy

## 파일 편집 및 관리

# 편집기
vi          :
GNU nano    :   트렌드하게 많이 쓰는것
Emacs       :
ed/ex       :

# vi

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

# nano
^ : ctrl 키를 의미

nano 파일명
editor 파일명

## 파일 찾기와 파일정보

# 파일 찾기
메뉴얼 = man find
find ./ -name *.java                            :   현재 디렉토리에서 파일 네임이 .java로 끝나는 파일
find . -name *.java -size +1c[옵션있다]          :   현재 디렉토리에서 사이즈가 1바이트 이상 (-1 : 1이하 )
find / -name *.java                             :   루트 디렉토리에서 전체 다 찾아라 -> 권한 수준을 체크하여 노출 없으면 permission denied

# 파일의 정보

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