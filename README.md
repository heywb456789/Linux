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