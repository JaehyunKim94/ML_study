# Docker TIL

참고: [subicura.com](https://subicura.com/)

### 1. Docker 설치 및 환경 설정

[Docker for Window 10 or upper (64-bit)](https://hub.docker.com/?overlay=onboarding)

- [Hyper-v 설정](https://docs.microsoft.com/ko-kr/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)
  - 관리자 권한으로 cmd 실행
  - `DISM /Online /Enable-Feature /All /FeatureName:Microsoft-Hyper-V`
  - Window >> 앱 및 기능 >> 프로그램 및 기능 >> Windows 기능 켜기/끄기 >> Hyper-v 체크

- Python 환경 설정
  - Docker image pull: 필요한 이미지를 가져온다. 
    - `docker pull dash00/tensorflow-python3-jupyter`



### 2. Docker 명령어

- **`$ docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG ...]`**
  - ex) `$ docker run -it --name lab01 dash00/tensorflow-python3-jupyter /bin/bash `

| Options | Description                                            |
| ------- | ------------------------------------------------------ |
| -d      | detached mode (a.k.a 백그라운드 모드)                  |
| -p      | 호스트와 컨테이너의 포트를 연결(포워딩)                |
| -v      | 호스트와 컨테이너의 디렉토리를 연결(마운트)            |
| -e      | 컨테이너 내에서 사용할 환경변수 설정                   |
| -name   | 컨테이너 이름 설정                                     |
| -rm     | 프로세스 종료시 컨테이너 자동 제거                     |
| -it     | -i와 -t를 동시에 사용한 것으로 터미널 입력을 위한 옵션 |
| -link   | 컨테이너 연결                                          |



- `$ docker ps` : 컨테이너 목록 조회
  - `$ docker ps -a`: 종료된 컨테이너를 포함하여 조회

- `$ docker images`: 다운받은 docker image 확인

- Container 명령어
  - `$ docker start [container name]`: 시작
  - `$ docker restart [container name]`: 재시작
  - `$ docker stop [container name]`: 정지
  - `$ docker attach [container name]`: 실행중인 컨테이너에 접속
  - `$ docker exec [container name] [command]`: 외부에서 컨테이너 안의 명령 실행
  - `$ docker rm [container name]`: 컨테이너 삭제
    - `docker run`명령을 실행시 `--rm` 옵션을 붙일 경우 컨테이너 종료시 컨테이너가 자동 삭제됨