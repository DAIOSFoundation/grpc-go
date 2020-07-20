# 해당 프로젝트는 grpc 예제입니다.

## 파일구조

- build : proto 파일을 읽어서 자동 생성된 파일 (수정 필요 하지 않음)
- client : grpc client
- server : grpc server
- simple : grpc proto 파일

## proto 파일 생성
- protoc --go_out=plugins=grpc:. proto/simple.proto


> 특이사항 : simple directory에서 실행 해야됨
>
> protoc : proto compiler
>
> --go_out : proto 파일을 컴파일한 위치, .으로 명시할 경우 현재 경로
>
> --go_out=plugins=grpc : grpc 호환코드를 생성
>
> simple.proto : 어떤 proto 파일을 컴파일 할지 명시

## 설치
``` 
brew install protobuf

protoc --version
실행 결과 > libprotoc 3.7.1 or 3.6.1

go get -u github.com/golang/protobuf/{proto,protoc-gen-go}

protoc --go_out=plugins=grpc:. proto/simple.proto

go mod init

go run server/grpcServerTest.go
go run client/grpcClientTest.go
```

## 실행
### 서버 실행
go run server/grpcServerTest.go

### 클라이언트 실행
go run client/grpcClientTest.go