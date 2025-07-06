```bash
Re-install go
https://go.dev/doc/install
sudo  rm -rf /usr/local/go && sudo tar -C /usr/local -xzf go1.24.4.linux-amd64.tar.gz

--install protoc compiler:
# Ubuntu/Debian
sudo apt install protobuf-compiler

# macOS
brew install protobuf

# Or download from https://github.com/protocolbuffers/protobuf/releases
wget https://github.com/protocolbuffers/protobuf/releases/download/v31.1/protoc-31.1-linux-x86_64.zip
sudo unzip protoc-31.1-linux-x86_64.zip  -d /usr/local/protobuf

install plugin
go install google.golang.org/protobuf/cmd/protoc-gen-go@latest
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest

export PATH="$PATH:$(go env GOPATH)/bin"

#verify protoc buf install
protoc --version
protoc-gen-go --version

# initialize project
go mod init your-project-name
go mod tidy

#add dependency
go get google.golang.org/protobuf/reflect/protoreflect
go get google.golang.org/protobuf/runtime/protoimpl
go get google.golang.org/grpc

# compile - generate .proto files
protoc --go_out=. --go_opt=paths=source_relative --proto_path=. api/v1/*.proto

protoc --go_out=. --go_opt=paths=source_relative --proto_path=. api/v1/*.proto
protoc --go_out=paths=source_relative:. --proto_path=. api/v1/*.proto
protoc --go_out=. --go_opt=paths=source_relative \
       --go-grpc_out=. --go-grpc_opt=paths=source_relative \
       --proto_path=. api/v1/*.proto

```