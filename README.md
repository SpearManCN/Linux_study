# Linux_study
리눅스 연습

### wsl (ubuntu) 이용해서 linux 연습

#### 설치 및 세팅
#### cmd(윈도우 10이상)에서 wsl --install 입력시 wsl, ubuntu 자동 다운로드
#### ubuntu에서 계정 생성 후 root 계정으로 접속 (sudo su)

### 기본 명령어
ls: 디렉터리 내용 보기<br/>
```bash
ls
new_file3.txt
ls -l
-rwxrwxrwx 1 cn1056 cn1056 57 Apr  9 09:08 new_file3.txt
```
이때의 첫 문자열은 맨 앞 d(디렉토리), -(일반파일), s(특수파일)<br/>
이후 rwx 각 read, write, execute 그리고 소유주, 소유그룹, 그 외유저 순으로 3번 반복<br/>

cd: 디렉터리 변경<br/>
pwd: 현재 작업 중인 디렉터리 출력<br/>
mkdir: 디렉터리 생성<br/>
touch: 빈 파일 생성 또는 파일 수정 시간 업데이트<br/>
cp: 파일 또는 디렉터리 복사<br/>
```bash
ls
new_file.txt
cp new_file.txt new_file2.txt
ls
new_file.txt new_file2.txt
cp new_file.txt file/path
```
cp 파일명 파일명2 하면 해당 디렉토리에 파일이 복사됨.<br/>
cp 파일명 위치 하면 해당 위치로 파일이 복사됨.<br/>

mv: 파일 또는 디렉터리 이동 또는 이름 변경<br/>
```bash
ls
new_file.txt
cp new_file.txt new_file2.txt
ls
new_file.txt new_file2.txt
cp new_file.txt file/path
```
rm: 파일 또는 디렉터리 삭제<br/>
cat: 파일 내용 출력<br/>
less 또는 more: 파일 내용 페이지별로 출력<br/>
grep: 파일 내에서 패턴 검색<br/>
```bash
grep "이 파일은" new_file.txt
이파일은 ubuntu로 만들어본 메모장입니다.
```
문자열 "이 파일은" 이 포함되어있다면 해당 부분이 빨간색으로 출력됨.<br/>

### 권한 관리
chmod: 파일 권한 변경
```bash
ls -l
-rwxrwxrwx 1 cn1056 cn1056 57 Apr  9 09:08 new_file.txt
sudo chmod 700 new_file.txt
ls -l
-rwx------ 1 root root 57 Apr  9 09:08 new_file.txt
```
chmod 뒤에 8진수 3개로 표현할 수 있고 또는 알파벳으로 표현가능 <br/>
r(4)w(2)x(1)의 각 값을 가짐<br/>

chown: 파일 소유자 변경
```bash
ls -l
-rwxrwxrwx 1 cn1056 cn1056 57 Apr  9 09:08 new_file.txt
sudo chown root:root new_file.txt
ls -l
-rwxrwxrwx 1 root root 57 Apr  9 09:08 new_file.txt
```
소유주:소유주그룹 형식이다.<br/>

sudo: 슈퍼 유저 권한으로 명령 실행

### 텍스트 편집
nano : 쉽고 간단한 txt 편집기 <br/>
vi : 심화된 편집기 <br/>
```bash
vi file.txt
```

명령 모드/ 입력 모드/ 콜론 모드 있음 <br/>
```bash
:q = 종료 
:q!= 강제종료
:w = 저장
:wq =저장후 종료
:wq 파일명 = 파일명으로 저장후 종료
x = 커서에 있는 것 삭제
yy = 현재 줄 복사
yw = 커서가 있는 현재 단어 복사
p = 붙어넣기
/문자열 = 문자열 찾기
n = 찾은 문자열들중 다음꺼
N = 찾은 문자열들중 이전꺼
:%s/old/new = 각 행의 처음 나오는 old를 new로 바꿔준다.
:%s/old/new/g = 모든 old를 new로 바꿔준다
:%s/old/new/gc = 모든 old를 new로 바꾸기전 물어본다.
u = undo. 되돌리기
ctrl + r = redo. 되돌린걸 취소
:set nu = 행 번호 출력
:set nonu = 행 번호 숨기기
```

### 파일 시스템 관리
ln = 링크 생성 (하드링크, 심볼릭 링크) 
```bash
ln file.txt linkName1
위는 하드링크 아래는 심볼릭 링크
ln -s file.txt linkName2
```
find = 파일, 디렉토리 찾기 * grep은 파일내에서 찾는것, find는 파일자체를 찾는
```bash
find Directory
-> Directory라는 이름을 가진 폴더의 하위 내용들 가져옴
find file.txt
-> 현재 디렉토리에서 file.txt을 찾음
find . -name "file.txt"
-> 현재 dir 및 모든 하위에서 file.txt를 찾음
find . -name "*nameAAA*"
-> 현재 dir 및 모든 하위에서 이름에 nameAAA가 들어가는 파일 및 dir을 찾
```
df = 리눅스 시스템 전체의 (마운트 된) 디스크 사용량을 확인 <br/>
du = 현재 Dir의 디스크 사용량 확인.<br/>
둘다 df -h, du -h 식으로 -h를 붙이면 가시성 좋아짐<br/>

### 압축
tar = linux에서 쓰이는 압축 형태
```bash
tar -cvf aaa.tar abc
abc폴더를 aaa.tar로 압축한다.
tar -xvf aaa.tar
aaa.tar를 압축해제한다.
tar -zcvf aaa.tar.gz abc
abc라는 폴더를 aaa.tar.gz로 압축한다.
tar -zxvf aaa.tar.gz
aaa.tar.gz를 압축해제한다.
```
zip = 압축
unzip = 압축해제
```bash
zip zipFile1.zip file1.txt file2.txt file3.txt
파일 세개를 압축한다.
zip -r zipFile2.zip directory
-r 을 사용해야 재귀적으로 하위 폴더들 까지 포함하여 압축한다.
unzip zipFile1.zip
unzip -d directory zipFile2.zip
각각 현재 위치, directory 위치에 압축해제
```
### 프로세스 관리

ps = 현재 프로세스 확인 <br/>
ps -e, ps -f = 모두보기, 좀더 자세히 보기 <br/>
kill = 프로세스 종료
```bash
kill -15 pid
kill -9 pid
위는 정상종료, 아래는 강제종료
```
top = 시스템의 실시간 프로세스 및 시스템 리소스 사용률 확인 (ps는 그 순간, top은 실시간) <br/>
htop = top의 향상된 텍스트기반 명령어 <br/>
killall = 한번에 여러 프로세스를 종료
```bash
killall processName
위는 processName이 들어간 모든 프로세스를 종료함
killall -i processName
같지만 종료전 물어봄

```

### 네트워크 관리
ping = 특정 호스트에 요청을 보내 네트워크가 정상적으로 작동하는지 확인하는 명령어
```bash
ping www.google.com
ping 8.8.8.8
위 처럼 호스트주소를 적어서 해당 서버와의 네트워크 상태를 확인할 수 있다.
```
ip addr(ifconfig) = 네트워크 인터페이스의 설정을 확인하고 변경하는 명령어 <br/>
netstat = 네트워크 연결 및 라우팅 테이블을 확인. 현재 시스템에서 열려 있는 포트, 연결된 주소 및 포트, 라우팅 정보 등을 확인 (net_tools를 다운받아야만 사용가능) <br/>
traceroute = 목적지 호스트로 가는 경로를 추적하고 각 중간 라우터까지의 지연 시간을 확인하는 데 사용 (traceroute 다운 받아야 사용가능) <br/>
ssh = 리눅스에서 사용하는 ssh 연결 명령어 (putty같은 기능, openssh-server를 설치해야함) <br/>
wget, curl = url 에서 파일 다운로드
```bash
wget [옵션] [url]
curl [옵션] [url]
```






