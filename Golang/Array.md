[[GOLANG]]
```
package main

import "fmt"

func main() {
    original := [5]int{1, 2, 3, 4, 5}
    copy := original

    copy[0] = 999

    fmt.Println("original:", original)
    fmt.Println("copy:    ", copy)
}
```
original: [1 2 3 4 5]
copy:     [999 2 3 4 5]
