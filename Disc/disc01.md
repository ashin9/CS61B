## 1 Our First Java Program

```java
没声明变量类型

[mydog, yourdog, 5, cutiedog] ❎
dogList[2] = 5;
// 5 错误，只能放 dog 类型
dogList[3] = new Dog("Cutie", 8);
// 错误，index 越界

x = 22
false 不执行
```

## 2 Mystery

```
a: 
x = 4
anser = 2
index = 3
arr.len = 5
循环 2 次
arr[3] = 6 < 4? no
index = 4
arr[4] = 3 < 4> yes
x = 3
anser = 4
index = 5

返回 4 ✅
```



```
b
返回数组从 k 索引后面，最小值的索引 ✅
```



```
从小到大排序 ✅

选择排序法（没想到叫什么）
```

### 3 Writing Your First Program

✅

```java
public static int fib(int n){
	if (n == 0){
		return 0;
	}
	else if (n == 1){
		return 1;
	}
	else{
		return fib(n-1) + fib(n-2);
	}
}
```

✅

```java
public static int fib(int n){
	if (n == 0 or n == 1){return n;}
	return fib(n-1) + fib(n-2);
}
```



❎

```java
public static int fib2(int n, int k, int f0, int f1){
	if (n == 0 or n == 1){return n;}
	for(int i = 3; i <= n; i++){
		f0, f1 = f1, f0 + f1;
	}
	return f1;
}
```



⭐️

利用参数记录中间值

k 用来控制边界

```java
public static int fib2(int n, int k, int f0, int f1){
  if (n == k){
    return f0;
  } else {
    return fib2(n, k + 1, f1, f0 + f1)
  }
```

