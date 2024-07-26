# Quick start Go

1. Make a empty folder on desktop
2. Open it with VScode
3. Make a file named main.go leave it blank for now
4. Run

```
go mod init <name of project> 
```

5. This will make a go.mod file, simple answer it where dependencies live&#x20;
6. To add a dependency

```
go get <package name>
```

\***NOTE**\*

Sometime the dependency do not want to play well so you may need to run this command and save a few times to make all the errors and warnings go away

```
go mod tidy
```

### Basic hello world

7. This to the main.go file&#x20;

```
package main
import (
    "fmt"
)
func main(){      
      fmt.println("Hello world")
}
```

8. Run

```
go run main.go
```





