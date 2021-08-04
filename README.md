# forkGo:

Fork golang to support Allman/Horstmann style of curly braces 

The google guys don't like allman style, but it's very easy to support allman style, just added only 13 lines of code into golang compiler.

Allman/Horstmann style is for we human, K&R style is for google robots!

![Gopher image](https://avatars.githubusercontent.com/u/86223803)

# Compile forkgo:
```bash
git clone --depth 1 --recursive https://github.com/forkgo-org/go.git
cd ./go/src
./all.bash             #need 50 seconds to build forkgo compiler           
cd ../forkgo-test
../bin/go version      #go version devel go1.17-ed7efd3 ....
../bin/go mod init test
../bin/go build -ldflags="-s -w"
./test

#if everything is ok, we can replace go with forkgo:
sudo cp ../bin/go /usr/local/bin/go
sudo mv /usr/local/go/bin/go /usr/local/go/bin/go.golang
hash -d go
type go        #if it shows "/usr/local/bin/go", we success
```

# forkgo-test/test.go, allman style:

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

    var a="hello"

    {   var b="forkgo"
        fmt.Println(a, b)
    }
}

```

Notes:

1. In this style, the '{' at the beginning of the line needs to be followed by a whitespace or a tab

2. A seperate code block needs a precedent empty line

While forkGo keeps support for golang's K&R style:

```go
package main
import(
    "fmt"
)


func main() {
    if false {
        fmt.Println("jack")
        fmt.Println("forkgo")
    } else {
        fmt.
           Println("hello")
        fmt.Println("forkgo")
    }

    var a="hello"
    {
        var b="forkgo"
        fmt.Println(a, b)
    }
}

```

Note:  the '{' at the beginning of the line should not be followed by a whitespace or a tab
