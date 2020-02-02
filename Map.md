### Map

1. key-value
2. key必须是支持==或!=比较运算的类型
3. map查找比线性查找快，但比索引访问要慢
4. 使用make创建
5. make([keyType]valueType,cap),cap表容量，可省略
6. 超出容量自动扩容
7. 使用len()获取元素个数
8. 键值对不存在时自动添加，使用delete()删除某键值对
9. 使用for range对map和slice进行迭代操作

- 定义

```go
func main() {
	var m map[int]string
	//m = map[int]string{}
	m = make(map[int]string)
	m1 := make(map[int]string)
	fmt.Println(m)
	fmt.Println(m1)
}
```

- 多层map

```go

func main() {
	m := make(map[string]map[string]int)
	v, ok := m["广西"]["玉林"]
	if !ok {
		// 多层嵌套注意初始化
		m["广西"] = make(map[string]int)
	}
	m["广西"]["玉林"] = 537400
	v, ok = m["广西"]["玉林"]
	fmt.Println(v,ok)
}
```

- 迭代操作

```go
func main() {
	sliceWithMap := make([]map[string]int,5)
	for index := range sliceWithMap{
		// 要先初始化
		sliceWithMap[index] = make(map[string]int)
		sliceWithMap[index]["年龄"] = 18
	}
	fmt.Println(sliceWithMap)
	//[map[年龄:18] map[年龄:18] map[年龄:18] map[年龄:18] map[年龄:18]]
}
```

- 间接对map的key排序

```go
func main() {
	m := map[int]string{1: "a",2: "b", 3: "c", 4: "e"}
	// 初始化slice
	s := make([]int, len(m))
	count := 0
	for k,_ := range m{
		s[count] = k
		count ++
	}
	sort.Ints(s)
	fmt.Println(m)
	fmt.Println(s)
}
```

- 练习

将map key value对换

```go
func main() {
	m1 := map[int]string{1:"a",2:"b",3:"c"}
	m2 := make(map[string]int,len(m1))
	for k,v := range m1{
		m2[v] = k
	}
	fmt.Println(m1) // map[1:a 2:b 3:c]
	fmt.Println(m2) // map[a:1 b:2 c:3]
}
```

