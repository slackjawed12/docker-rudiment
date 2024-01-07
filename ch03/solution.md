### chapter03 연습문제해결

1. 도커허브 공유 이미지 받기 - docker image pull diamol/ch03-lab
2. docker container run -it --name ch03-lab diamol/ch03-lab
3. 컨테이너에서 텍스트 추가 명령어 실행 및 종료

   ```
   # echo '이름' >> ch03.txt
   # exit
   ```

4. 변경사항 커밋
   - docker container commit ch03-lab ch03-lab:v2
5. 변경사항 반영된 이미지로 새 컨테이너 실행 + 명령어 실행
   - 리눅스 : docker container run ch03-lab:v2 cat ch03.txt
   - 윈도우 : docker container run ch03-lab:v2 cmd /s /c type ch03.txt
