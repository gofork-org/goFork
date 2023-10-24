# goFork (v1.21.3):

Fork golang to support Allman/Horstmann style of curly braces 

The google guys don't like allman style, but it's very easy to support allman style, just added only 13 lines of code into golang compiler.

Allman/Horstmann style is for we human, K&R style is for google robots!

![Gopher image](https://avatars.githubusercontent.com/u/86223803)

# Compile goFork:
```bash
sudo rm -rf /usr/local/go && wget -qO- https://golang.org/dl/go1.18.1.linux-amd64.tar.gz | sudo tar -xvz -C /usr/local
export -n GOROOT ; hash -d go
sudo mv /usr/local/go /usr/local/go.golang
git clone --depth 1 --recursive https://github.com/gofork-org/go.git
#or: wget https://github.com/gofork-org/go/archive/refs/heads/master.zip && unzip master.zip
cp -r ./go/bin.bootstrap ./go/bin
cd ./go/src
#bootstrap depends on ./pkg/tool/linux_amd64/compile(23MB bin), ./bin/go(15MB bin), can't simply copy them into goFork, will be not compatible with ./src/
export GOROOT_BOOTSTRAP=/usr/local/go.golang
./all.bash             #need 50 seconds to build gofork compiler           

cd ../test-gofork
../bin/go mod init test
../bin/go build -ldflags="-s -w"
./test

#if everything is ok, we can replace golang with gofork:
sudo cp -r ../ /usr/local/go
sudo export PATH=$PATH:/usr/local/go/bin         #or append ":/usr/local/go/bin" into PATH in /etc/environment

#if you have "git pull" again, you should run ./all.bash again to match the ./bin/go with the latest ./src(stdlib)
```

# test-gofork/test.go, Allman/Horstmann style:

```go
package main
import
(   "fmt"
)


func main()
{   if false
    {   fmt.Println("jack")
        fmt.Println("gofork")
    } else
    {   fmt/
           .Println("hello")
        fmt.Println("gofork")
    }

    var a="hello"

    {   var b="gofork"
        fmt.Println(a, b)
    }
}

```

Notes:

1. In this style, the '{' at the beginning of the line needs to be followed by a whitespace or a tab

2. A seperate code block needs a precedent empty line

While gofork keeps support for golang's K&R style:

```go
package main
import(
    "fmt"
)


func main() {
    if false {
        fmt.Println("jack")
        fmt.Println("gofork")
    } else {
        fmt.
           Println("hello")
        fmt.Println("gofork")
    }

    var a="hello"
    {
        var b="gofork"
        fmt.Println(a, b)
    }
}

```

Note:  the '{' at the beginning of the line should not be followed by a whitespace or a tab
