# Compile forkgo:
```bash
git clone --depth 1 --recursive https://github.com/forkgo-org/go.git
cd ./go/src
./all.bash             #need 50 seconds to build forkgo compiler
cd ../bin
./go version           #go version devel go1.17-ed7efd3 ....
cd ../forkgo-test
../bin/go mod init test
../bin/go build -ldflags="-s -w"
./test
```

# forkgo-test/test.go file:

```go
package main
import
(   "fmt"
)


func main()/
{   if false/
    {   fmt.Println("jack")
        fmt.Println("forkgo")
    } else/
    {   fmt/
           .Println("hello")
        fmt.Println("forkgo")
    }
}

```

# The Go Programming Language

Go is an open source programming language that makes it easy to build simple,
reliable, and efficient software.

![Gopher image](https://avatars.githubusercontent.com/u/86223803)
