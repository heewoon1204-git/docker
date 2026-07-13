# Homebrew 설치

## 설치 이유

Docker를 설치하기 위해 먼저 Docker 공식 홈페이지에서 설치를 시도했지만, Homebrew를 이용해 설치하는 방법을 알게 되어 Homebrew를 먼저 설치했다.
(추가로, mac 12.6은 홈페이지에서 다운받은 설치 파일로 설치가 불가능했음.)

## 설치 환경
```bash
uname -m
```
칩 : Apple M1 Pro arm64
OS : macOS 12.6


## 1. 설치 
mac 터미널에서 설치

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## 설치 중 확인한 내용
- macOS 12 지원 종료 경고가 출력되었음.
- 설치는 정상적으로 진행됨.


## 2. 설치 확인 

### 2-1. PATH 설정 전
설치 경로가 있으면 설치 성공
```bash
ls /opt/homebrew/bin/brew
```

### 2.2. PATH 설정 후
```bash
brew --version
```

## 3.PATH 설정

### 3-1. 터미널에서 homebrew 사용할 수 있도록 설정파일에 추가
homebrew shellenv 파일에 path 설정이 있기 때문에 path 설정을 직접적으로 하지 않고 shellenv 파일을 실행하도록 함.

- eval : 문자열을 다시 명령어로 실행
- $(명령어) : 명령어 실행 결과를 가져옴
- '>>' : 파일 맨 아래에 추가
- .zprofile : 맥의 쉘이 시작될 때 읽는 설정 파일

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
```

### 3-2. 수정한 설정파일 재실행하여 즉시 적용
.zprofile은 터미널을 새로 열 때만 읽음.
강제 재실행

```bash
source ~/.zprofile
```

## 설치 확인 중 확인한 내용
- PATH를 등록하지 않으면 brew 명령어 사용 불가

## 배운 점

- Homebrew는 macOS에서 프로그램을 쉽게 설치하고 관리하는 패키지 관리자이다.
- `brew install` 명령으로 다양한 개발 도구를 설치할 수 있다.