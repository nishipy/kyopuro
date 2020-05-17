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
### Cast String <-> Int
```
var i int
var s string="123"
i, _ = strconv.Atoi(s)
fmt.Println(i) // -> 123
```
```
var i int=321
var s string
s = strconv.Itoa(i)
fmt.Println(s) // -> "123"
```

### Display []int like as string
```
//with buf.Flush()
func printList(list []int) {
	buf := bufio.NewWriter(os.Stdout)
	for _, v := range list {
		buf.Write([]byte(fmt.Sprintf(" %d", v)))
	}
	buf.Write([]byte("\n"))
	buf.Flush()
}

//Or
func arrayAsString(arr []int) string {
	return strings.TrimRight(fmt.Sprintf("%+v", arr)[1:], "]")
}

//Or
for i:= 0; i<len(array); i++ {
	fmt.Printf("%d ", array[i])
}


```

### 2進数に変換
```
b := fmt.Sprintf("%b", 2)
//0埋め4文字
//b := fmt.Sprintf("%04b", 2)
fmt.Println(b)
```

### GCD
```
func gcd(a, b int) int {
    if b == 0 {
        return a
    }
    return gcd(b, a%b)
}
```

### GCD with math/big
```
func gcd(m, n uint64) uint64 {
    x := new(big.Int)
    y := new(big.Int)
    z := new(big.Int)
    a := new(big.Int).SetUint64(m)
    b := new(big.Int).SetUint64(n)
    return z.GCD(x, y, a, b).Uint64()
}
```

## Define and use map
```
func main() {
	sc.Split(bufio.ScanWords)
	n = nextInt()
	m := make(map[string]int, n)
	for i := 0; i < n; i++ {
		s = nextStr()
		//mapにkeyが存在するか判定
		if _, ok := m[s]; ok {
			m[s]++
		} else {
			m[s] = 1
		}
	}
	//fmt.Println(m)
	fmt.Println(len(m))
}
```

## グラフ問題
* 可視化サイト
  * https://hello-world-494ec.firebaseapp.com/
* 幅優先探索
  * 最短距離問題に使う
    * 各節点に隣接する点を入力する
    * 次に訪問する節点を保持するキューを用意する
      * 始点をキューに入れる
      * キューから取り出し、その点について処理する
      * 処理した節点に隣接する点を、キューに入れる
      * キューが空になるまで処理を繰り返す
    * 例
      * [168 D - .. (Double Dots)](./168/D/main.go)
