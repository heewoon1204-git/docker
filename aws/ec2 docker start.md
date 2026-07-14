# EC2에서 docker 사용하기
터미널을 이용해 ec2 public ip로 ssh 접속해 설치 진행

## docker 설치
### 1. ubuntu 패키지 목록 업데이트
apt : 우분투 패키지 관리자
```bash
sudo apt update
```

### 2. docker 설치 및 확인
apt를 이용해 docker 설치
```bash
# 설치
sudo apt install docker.io -y
# 설치 확인
docker --version
# 서비스 상태 확인
sudo systemctl status docker
```

## docker로 이미지 다운로드
### 1. 이미지 다운로드
- pull  :  이미지를 다운로드하는 것일 뿐 컨테이너가 실행되지 않음
```bash
sudo docker pull nginx
```


