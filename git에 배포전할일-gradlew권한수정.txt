1. jenkins
사용자 이름: shchoi8347
비밀번호: Impact33&&

1. Git에 배포전에 할 일
- gradlew 권한 수정

$ git ls-tree HEAD
$ git update-index --add --chmod=+x gradlew
./gradlew clean build