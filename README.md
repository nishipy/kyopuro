# AtCoder_ABC
My solutions for AtCoder Beginner Contest problems.

## Tips - Golang
### Input data
```
package main

import (
	"bufio"
	"fmt"
	"os"
	"strconv"
)

var sc = bufio.NewScanner(os.Stdin)

func nextStr() string {
	sc.Scan()
	return sc.Text()
}

func nextInt() int {
	sc.Scan()
	i, e := strconv.Atoi(sc.Text())
	if e != nil {
		panic(e)
	}
	return i
}

func main() {
	sc.Split(bufio.ScanWords) //スペース区切り
	// sc.Split(bufio.ScanLines) //1行まるごと
	var n int
	n = nextInt()
...
```

### Min(), Max() for int
```
func Max(a, b int) int {
	if a > b {
		return a
	} else {
		return b
	}
}

func Min(a, b int) int {
	if a > b {
		return b
	} else {
		return a
	}
}
```

### Split a string on whitespace
```
l := strings.Split(str, " ")
```


### Join array to a string with whitespace
```
strings.Join(arr, ",")
```
### Cast String -> Int
```
val_int, _ := strconv.Atoi(val_str)
```

### Display array like as string
```
// e.g.) [1, 2, 3, 4, 5] -> 1 2 3 4 5
func arrayAsString(arr []int) string {
	return strings.TrimRight(fmt.Sprintf("%+v", arr)[1:], "]")
}
```