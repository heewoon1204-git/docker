# PATH 개념

## 정리하는 이유
설치할 때 PATH 설정을 해야 명령어 사용 가능함.
왜 설정하는지 알고 넘어가야 언젠가 문제 생겼을 때 도움이 될거 같아서 정리.

## 1. PATH 란?
한마디로, 프로그램을 찾는 주소록.
PATH에 등록된 디렉토리 기준으로 명령어를 입력했을 때 찾아나가면서 동작함.
따라서, 동일명의 프로그램이 있을 시 어디에 설치되어 있는지 혹은 path 순서가 어떻게 되어있는지에 따라 실행되는게 달라짐

```bash
# 등록된 PATH 찾기
echo $PATH

# : 로 구분뒤어 한줄로 조회
# 앞에 있을 수록 우선순위가 높음
/opt/homebrew/bin:/opt/homebrew/sbin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
```
1. /opt/homebrew/bin : homebrew로 설치한 대부분의 프로그램이 여기에 들어감
2. /opt/homebrew/sbin : system binary -> 일반 프로그램보다 서버, 데몬, 관리자용 프로그램이 들어감.
                       ex) nginx, httpd, dnsmasq...
3. /usr/local/bin : 사용자 설치 프로그램 위치
                   intel mac은 homebrew가 여기 설치됐었다고함.
4. /usr/bin : macos가 기본 제공하는 명령어
             ex) ls, cat, cp ...

```bash
brew --version
```

명령어 입력 시 1번, 2번, 3번 순서로 등록된 디렉토리 순서대로 찾아서 실행
당연히, 찾는 순간 아래는 더 보지 않음.

## 2. PATH 순서 이슈
PATH는 등록된 디렉토리 순서대로 찾으며, 동일한 이름의 프로그램이 여러 디렉토리에 있을 시 디렉토리 상 가장 위에 있는 프로그램을 실행함.

1. /opt/homebrew/bin/homebrew
3. /usr/local/bin/homebrew

이렇게 설치되어있다고 가정하면, "brew --version" 명령어 실행 시 1번 디렉토리에 있는 homebrew의 버전이 나올것.

## 3.PATH 순서 변경

### 3-1. 현재 터미널에서 임시 변경
터미널을 끄기 전까지만 유지
PATH 문제인지 확인상 테스트할 때 사용하면 될거 같음.

- export : 환경 변수를 설정해서 현재 쉘과 그 자식 프로세스에서 사용할 수 있게 하는 명령어
- PATH= : path 변수에 새로운 값을 넣음
- $PATH : 기존 PATH를 그대로 가져옴

```bash
# /usr/bin을 PATH 가장 앞으로 두고 싶을 때, 기존 PATH를 가지고 와서 내가 원하는 디렉토리를 그 앞에 설정함
export PATH="/usr/bin:$PATH"

# 결과값
# 동일 디렉토리가 뒤에 있어도 상관 없음.
/usr/bin:/opt/homebrew/bin:/opt/homebrew/sbin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
```

### 3-2. 영구적으로 변경

```bash
# 1. 쉘 실행 시 읽는 설정 파일 열기
~/.zprofile

# 2. 파일 열기
nano ~/.zprofile

# 3. 파일 수정
# 터미널이 실행될 때 PATH를 설정하게 함
export PATH="/Users/heewoon/bin:$PATH"

# 4. 파일 재실행
source ~/.zprofile
```