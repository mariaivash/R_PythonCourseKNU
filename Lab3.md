# Lab3
## Task1
### Функція add2(x, y), яка повертає суму двох чисел.
```r
add2 <- function(x,y){
  x+y
}
add2(2,8)  
[1] 10
```

## Task2
### Функція above(x, n), яка приймає вектор та число n, та повертає всі елементі вектору, більші за n. 
* По замовчуванню n = 10. 
```r
above <- function(x,n=10){
  x[x>n]
}
above(c(5:15))
[1] 11 12 13 14 15

above(c(5:15), 13)
[1] 14 15
```

## Task3
### Функція my_ifelse(x, exp, n), яка приймає вектор x і порівнює всі його елементи за допомогою exp з n, та повертає елементи вектору, які відповідають умові expression. 
* Наприклад, **my_ifelse(x, “>”, 0)** повертає всі елементи *x*, які більші 0. *Exp* може дорівнювати “<”, “>”, “<=”, “>=”, “==”. Якщо *exp* не співпадає ні з одним з цих виразів, повертається вектор *x*. 
```r
my_ifelse <- function(x, exp, n){
  if (exp == "<") {
    x[x<n]
  } else if(exp == "<="){
    x[x<=n]
  } else if (exp == ">"){
    x[x>n]
  } else if (exp == ">="){
    x[x>=n]
  } else if (exp == "=="){
    x[x==n]
  } else {
    x
  }
}
x <- c(1,2,5,9,16,20)
my_ifelse(x, ">=", 9)
[1]  9 16 20

my_ifelse(x, "==", 9)
[1] 9

my_ifelse(x, "<", 16)
[1] 1 2 5 9

my_ifelse(x, "<=", 2)
[1] 1 2

my_ifelse(x, "+", 0)
[1]  1  2  5  9 16 20
```

## Task4
### Функція columnmean(x, removeNA), яка розраховує середнє значення (mean) по кожному стовпцю матриці, або data frame. 
* Логічний параметр **removeNA** вказує, чи видаляти **NA** значення. По замовчуванню він дорівнює **TRUE**. 
```r
columnmean <- function(x, removeNA=TRUE){ 
  colMeans(k, na.rm=removeNA)
  }
k <- matrix(c(1:3, NA, 5, 6, NA, NA, 9, 10), nrow=2, ncol=5)
columnmean(k)
[1] 1.5 3.0 5.5 NaN 9.5

columnmean (k, FALSE)
[1] 1.5  NA 5.5  NA 9.5
```
