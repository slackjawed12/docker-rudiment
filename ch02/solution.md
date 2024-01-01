### chapter02 연습문제 해결

1. docker container run --detach --publish 8088:80 diamol/ch02-hello-diamol-web 실행
2. (OPTIONAL) ls command로 실제 파일 있는지 확인
   ```
   $ docker container exec "containerID" ls /usr/local/apache2/htdocs
   ```
3. 호스트 컴퓨터에 수정할 index.html 작성
4. docker container cp ./index.html "containerID":/usr/local/apache2/htdocs 실행
