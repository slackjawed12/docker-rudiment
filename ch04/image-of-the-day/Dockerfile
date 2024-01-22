FROM diamol/maven AS builder

WORKDIR /usr/src/iotd
COPY pom.xml . 
# 의존 모듈 내려받는 인스트럭션. 새로운 의존 모듈이 추가되면 이전의 COPY 인스트럭션에서 변경이 생기므로 RUN도 다시 실행
# 따로 추가되는 의존 모듈이 없으면 이미지 캐시 재사용됨
RUN mvn -B dependency:go-offline

COPY . .
# 빌드 과정에 문제가 생기면 인스트럭션 실패하면서 전체 빌드도 실패한다.
RUN mvn package

# app
FROM diamol/openjdk

WORKDIR /app
COPY --from=builder /usr/src/iotd/target/iotd-service-0.1.0.jar .

EXPOSE 80
# CMD 인스트럭션과 같은 기능
ENTRYPOINT [ "java", "-jar", "/app/iotd-service-0.1.0.jar" ]

# 최종 생성되는 이미지에 빌드 도구는 포함되지 않음
# 도커파일에 정의된 빌드 단계 중 마지막 단계 컨텐츠만 포함됨