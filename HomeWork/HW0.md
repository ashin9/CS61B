## 目的：检验是否适合 CS61B

若做起来很吃力，则不太适合做 CS61B

## A Basic Program

静态类型

`;` 一个语句的结束和下个的开始

## Conditionals

### *[Shewchuk](https://sp21.datastructur.es/materials/hw/hw0/hw0_supplementary_conditionals.txt)*

if boolValue

```java
if (boolValue) {
  statements;
}
```

If-then-else

- nested 嵌套，构建决定树
- Chained 链式，表示多个选择

```java
    if (x > y) {
      if (x > z) {
        maximum = x;
      } else {
        maximum = z;
      }
    } else if (y > z) {
      maximum = y;
    } else {
      maximum = z;
    }
```

switch

- 测试变量是否 equal 某些常量
- break 跳出 switch，若忘记 break 则顺到下个 case 语句
- default，case 都不满足跳到 default

```java
    switch (month) {        |      if (month == 2) {                         
    case 2:                 |        days = 28;                              
      days = 28;            |      } else if ((month == 4) || (month == 6) ||
      break;                |                 (month == 9) || (month == 11)) {
    case 4:                 |        days = 30;                              
    case 6:                 |      } else {                                  
    case 9:                 |        days = 31;                              
    case 11:                |      }                                         
      days = 30;            |
      break;
    default:
      days = 31;
      break;
    }                   //  These two code fragments do exactly the same thing.
```

### Basic Conditionals

### Curly Braces (and Conditionals)

`{}` 括号，分组带阿米

不要写到一行

### Curly Brace Standards

两种风格

```java
if (x > 5) {              if (x > 5)
    x = x + 5;            {
}                            x = x + 5;
                          }
```

## Else

if

else if

else

`>=`

## While

认为代码一行行顺序执行

### *[Shewchuk](https://sp21.datastructur.es/materials/hw/hw0/hw0_supplementary_loops.txt)*

类似 if，不过 body 代码重复执行

```java
    public static boolean isPrime(int n) {
      int divisor = 2;
      while (divisor < n) {         _ <- "divisor < n" is the _loop_condition_.
        if (n % divisor == 0) {      |
          return false;              | These lines inside the braces
        }                            | are called the _loop_body_.  
        divisor++;                  _|
      }
      return true;
    }

```

`_iteration_`

for

- 紧凑的 while

```java
    for (initialize; condition; next) {      |    initialize;   
      statements;                            |    while (condition) {
    }                                        |      statements;
                                             |      next;
                                             |    }
```



```java
    public static void printPrimes(int n) {
      int i;
      for (i = 2; i < n; i++) {        // ERROR!!!  Condition should be i <= n.
        if (isPrime(i)) {
          System.out.print(" " + i);
        }
      }
    }
```



## Doubles and Strings

Double 存储真实值的近似值

String 存储字符串

## Creative Exercise 1a: Drawing a Triangle

```java
public static void main(String[] args){
  for (i = 1 ; i <= 5; i++){
    for (j = 1; j <= i; j++){
      System.out.print('*');
    }
    System.out.println();
  }
}
```

## Defining Functions (a.k.a. Methods)

Java Function 明确的返回类型

void 不返回任何

## Creative Exercise 1b: DrawTriangle

```java
public class drawTriangle{
   public static void drawTriangle(int n){
      for (int i = 1 ; i <= n; i++){
         for (int j = 1; j <= i; j++){
            System.out.print('*');
         }
         System.out.println();
      }  
   }
   public static void main(String[] args){
      drawTriangle(10);
   }
}
```

## Arrays

类似 Py 的 lists 和 Scheme 的 vectors

`.length` 获取长度

### *[Shewchuk](https://sp21.datastructur.es/materials/hw/hw0/hw0_supplementary_arrays.txt)*

```java
                                      0   1   2   3
                           ---      -----------------
                           |.+----->| b | l | u | e |
                           ---      -----------------
                            c
```

```java
    char[] c;           // Reference to an array (of any length) of characters.
    c = new char[4];
    c[0] = 'b';         // Store the character 'b' at index 0.
    c[1] = 'l';
    c[2] = 'u';
    c[3] = 'e';
    c[4] = 's';         // Program stops with ArrayIndexOutOfBoundsException
_run-time_error_
  Java Virtual Machine out-of-range index.
```

不可赋值 c.length，若尝试则编译错误

## Exercise 2

```java
public class printMax {
   public static int max(int[] m) {
      int max = 0;
      for (int i = 0; i < m.length; i++){
         if (m[i] > max) {
            max = m[i];
         }
      }
      return max;
   }
   public static void main(String[] args) {
      int[] numbers = new int[]{9, 2, 15, 2, 22, 10, 6};
      System.out.println(max(numbers));
   }
}
```

## For Loops

whileSum 改 for

```java
for (initialization; termination; increment) {
    statement(s)
}
```

## Exercise 3

2 已经用了 for

## Break and Continue

continue，跳过当前迭代的剩余部分，跳到下个迭代

break，终止循环

do-while

## Optional: Exercise 4

```java
public class BreakContinue {
  public static void windowPosSum(int[] a, int n) {
      for(int i = 0; i < a.length; i++){
         if (a[i] >= 0){
            for(int j = 0; j < n; j++){
               if (i+j+1 >= a.length){
                  break;
               }
               else{
                  a[i] += a[i+j+1];
               }
            }
         }
         else{
            continue;
         }
      }
  }

  public static void main(String[] args) {
    int[] a = {1, 2, -3, 4, 5, 4};
    int n = 3;
    windowPosSum(a, n);

    // Should print 4, 8, -3, 13, 9, 4
    System.out.println(java.util.Arrays.toString(a));
  }
}
```

## The Enhanced For Loop

不用索引迭代数组

```java
String[] a = {"cat", "dog", "laser horse", "ketchup", "horse", "horbse"};
for (String s : a){
  ...
}
```

