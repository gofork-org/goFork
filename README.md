# forkGo:

Fork golang to support allman style of curly braces 

The google guys don't like allman style, but it's very easy to support allman style, just added only 12 lines of code.

![Gopher image](https://avatars.githubusercontent.com/u/86223803)

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


func main()
{   if false
    {   fmt.Println("jack")
        fmt.Println("forkgo")
    } else
    {   fmt/
           .Println("hello")
        fmt.Println("forkgo")
    }
}

```

Note: in this style, the '{' at the beginning of the line needs to be followed by a space
