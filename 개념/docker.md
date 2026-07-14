## docker 호출 흐름
- docker.sock : docker cli(명령을 전달하는 클라이언트)와 docker Docker Daemon(dockerd)을 연결하는 통신 통로
                해당 파일의 권한은 srw-rw----
- Docker Daemon(dockerd) : 실제로 Docker Engine의 작업(이미지 관리, 컨테이너 생성)을 수행
- - Docker Hub :  이미지를 가져오는 외부 저장소
```bash
# docker 명령어 사용시 flow
ubuntu 사용자
      |
      | docker 명령어
      ↓
/var/run/docker.sock
      |
      ↓
Docker Daemon (dockerd)ㄴ
      |
      ↓
Docker Hub
```
