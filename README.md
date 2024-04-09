# Linux_study
리눅스 연습

### wsl (ubuntu) 이용해서 linux 연습

#### 설치 및 세팅
#### cmd(윈도우 10이상)에서 wsl --install 입력시 wsl, ubuntu 자동 다운로드
#### ubuntu에서 계정 생성 후 root 계정으로 접속 (sudo su)

### 기본 명령어
ls: 디렉터리 내용 보기<br/>
```bash
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
mv: 파일 또는 디렉터리 이동 또는 이름 변경<br/>
rm: 파일 또는 디렉터리 삭제<br/>
cat: 파일 내용 출력<br/>
less 또는 more: 파일 내용 페이지별로 출력<br/>
grep: 파일 내에서 패턴 검색<br/>
chmod: 파일 권한 변경
chown: 파일 소유자 변경
sudo: 슈퍼 유저 권한으로 명령 실행

