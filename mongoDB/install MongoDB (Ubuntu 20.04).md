## Ubuntu version check
```bash
$ lsb_release -dc
```
![CleanShot 2025-03-31 at 09 59 58](https://github.com/user-attachments/assets/bd61f1c8-bb2a-495c-9aca-c3706301a021)

터미널에서 ```lsb_release -dc``` 명령어를 사용해 ```Description``` 부분을 보면 현재 사용 중인 Ubuntu version을 확인 할 수 있다.

## Install MongoDB on Ubuntu
1. MongoDB public GPG key를 https://www.mongodb.org/static/pgp/server-4.4.asc 에서 가져온다.
```bash
wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
```
![CleanShot 2025-03-31 at 10 04 35](https://github.com/user-attachments/assets/ccb49471-5dc4-4446-bef2-a4c36d92efc9)

암호 입력이 필요하면 Ubuntu 패스워드를 입력해주면 된다.
처리가 완료 되었다면 터미널에 OK가 반환된다.

2. MongoDB List 파일 생성
작업의 핵심은 MongoDB 패키지를 설치할 수 있도록, 우분투의 패키지 관리자(apt)가 MongoDB 공식 저장소(repository)를 인식하게 만드는 것이다.

🔍 왜 이 작업이 필요한가?
우분투의 apt는 소프트웨어를 설치할 때 패키지의 출처(저장소)를 /etc/apt/sources.list 또는 /etc/apt/sources.list.d/ 아래의 .list 파일들에서 찾는다.
하지만 기본 우분투 저장소에는 MongoDB가 포함되어 있지 않거나, 최신 버전이 없을 수 있기 때문에 MongoDB 공식 저장소를 따로 등록해야 apt install mongodb-org 같은 명령어가 제대로 동작한다.

🔧 무슨 일을 하는 명령어인가?
```bash
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
```
1. echo로 MongoDB 저장소 주소를 출력하고
2. tee를 이용해 그 내용을 /etc/apt/sources.list.d/mongodb-org-4.4.list라는 파일로 저장한다.

왜 focal이라는 단어가 있지?
focal은 Ubuntu 20.04의 코드네임이다.
이 저장소는 Ubuntu 20.04(focal)에서 동작하도록 만들어진 MongoDB 4.4 버전을 제공한다. Ubuntu 22.04는 jammy, Ubuntu 18.04는 bionic이라는 이름을 사용한다.
따라서 우분투 버전에 맞는 저장소 URL을 사용해야한다.

3. Ubuntu 로컬 패키지 데이터베이스 불러오기
```bash
sudo apt-get update
```

🔍 sudo apt-get update는 무슨 일을 하는가?

이 명령어는 우분투의 패키지 관리 시스템이 알고 있는 소프트웨어 목록을 최신 상태로 갱신하는 것이다.
	•	우분투는 /etc/apt/sources.list와 /etc/apt/sources.list.d/*.list에 있는 저장소 목록을 기반으로,
	•	그 저장소들에 접속해서 패키지 이름, 버전, 의존성 정보 등을 가져와서 로컬에 저장한다.
	•	이게 바로 “로컬 패키지 데이터베이스”이다.

즉, 이전 단계에서 우리가 추가한 MongoDB 저장소의 정보를 apt가 인식하려면, apt-get update를 통해 최신 목록을 불러와야 해.


💡 왜 이게 필요한가?
만약 이걸 생략하면,
	•	apt install mongodb-org 같은 명령어를 쳐도 apt는 MongoDB 패키지가 뭔지 모른다.
	•	“패키지를 찾을 수 없습니다”라는 에러가 뜰 가능성이 높다.

이 업데이트는 패키지를 설치하기 전에 항상 실행하는 게 좋고, 특히 새로운 저장소를 추가한 직후엔 필수 작업이다.

4. MongoDB 패키지 설치
```bash
sudo apt-get install -y mongodb-org
```


