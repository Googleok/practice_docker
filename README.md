#  📚 도커 실습

❗️ 명령 입력 시 permission 관련 오류가 뜨는 환경에서는 각 명령어 앞에 sudo를 붙여주세요.


#### ⭐️ 도커 버전 확인
```shell
docker -v
```  
<br/>

#### 도커 이미지 다운만 받기
```shell
docker pull {이미지명}:{태그}
# 예: docker pull python:3
```  
- 태그는 필수가 아닙니다.

<br/>

#### ⭐️ 컴퓨터 내 도커 이미지들 보기
```shell
docker images
```
<br/>

#### 이미지로 컨테이너 생성하기
```shell
docker create {옵션} {이미지명}:{태그}
# 예: docker create -it python
```
<br/>

#### 만들어진 컨테이너 시작하기 (이미지에 CMD로 지정해놓은 작업 시키기)
```shell
docker start {컨테이너 id 또는 이름}
```
<br/>

#### 컨테이너로 들어가기 (컨테이너 내 CLI 이용하기)
```shell
docker attach {컨테이너 id 또는 이름}
```
<br/>

#### ⭐️ 이미지를 다운받아(없을 시에만) 바로 컨테이너 실행하여 진입하기
```shell
docker run {이미지명}:{태그}
# 예: docker -it run python:3
```
- pull, create, start, attach 를 한꺼번에 실행하는 것과 같습니다.

**옵션**|**설명**
:-----:|:-----:
-d|데몬으로 실행(뒤에서 - 안 보이는 곳(백그라운드)에서 알아서 돌라고 하기)
-it|컨테이너로 들어갔을 때 bash로 CLI 입출력을 사용할 수 있도록 해 줍니다.
--name {이름}|컨테이너 이름 지정
-p {호스트의 포트 번호}:{컨테이너의 포트 번호}|호스트와 컨테이너의 포트를 연결합니다.
--rm|컨테이너가 종료되면{내부에서 돌아가는 작업이 끝나면} 컨테이너를 제거합니다.
-v {호스트의 디렉토리}:{컨테이너의 디렉토리}|호스트와 컨테이너의 디렉토리를 연결합니다.
<br/>

#### 동작중인 컨테이너 재시작
```shell
docker restart {컨테이너 id 또는 이름}
```
<br/>

#### 도커 컨테이너의 내부 쉘에서 빠져나오기 (컨테이너를 종료)
```shell
exit
```
또는 Ctrl + D

도커 컨테이너의 내부 쉘에서 빠져나오기 (컨테이너를 종료하지 않음)

Ctrl + P, Q

<br/>


#### ⭐️ (동작중인) 컨테이너들 보기
```shell
docker ps
```
- 동작중이 아닌 것을 포함한 모든 컨테이너를 보려면 -a 옵션을 뒤에 붙입니다.

<br/>

#### 컨테이너 삭제
```shell
docker rm {컨테이너 id 또는 이름}

# ⭐ 모든 컨테이너 삭제
docker rm `docker ps -a -q`
```

<br/>


#### 이미지 삭제
```shell
docker rmi {옵션} {이미지 id}
```

- 컨테이너가 있을 시 강제삭제: -f 옵션 사용

<br/>


#### ⭐️ 모든 컨테이너와 이미지 등 도커 요소 중지 및 삭제
```shell
# 모든 컨테이너 중지
docker stop $(docker ps -aq)

# 사용되지 않는 모든 도커 요소(컨테이너, 이미지, 네트워크, 볼륨 등) 삭제
docker system prune -a
```

```shell
# 아래를 복붙하여 함께 실행하면 편리합니다.
docker stop $(docker ps -aq)
docker system prune -a
```

- 확인 질문에 y로 답하고 마무리합니다.


<br/>


#### ⭐️ 도커파일로 이미지 생성
```shell
# Dockerfile 파일이 있는 디렉토리 기준. 마지막의 .이 상대주소
docker build -t {이미지명} .
```

<br/>


#### ⭐️ 도커 컴포즈 실행
```shell
# docker-compose 파일이 있는 디렉토리 기준
docker-compose up
```
- 백그라운드에서 데몬으로 돌도록 하려면 -d 옵션을 붙입니다.


출처: https://www.yalco.kr/36_docker/