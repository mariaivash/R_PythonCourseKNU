# Lab1
## Task1
### Створити змінні базових (atomic) типів.
* Текстовий
``` gDef <- "gravitational acceleration"
class(gDef)
```
[1] "character"

* Реальне число
``` gVal <- 9.80665
class(gVal)
```
[1] "numeric"

* Ціле число
``` gRound <- 10L
class(gRound)
```
[1] "integer"

* Логічний
``` gLog <- TRUE
class(gLog)
```
[1] "logical"

* Комплексний
``` gCompl <- (9.8+0i)
class(gCompl)
```
[1] "complex"

## Task2
### Створити вектори.
*  Послідовність з 5 до 75
``` v1 <- c(5:75)
v1
```
[1]  5  6  7  8  9 10 11 12 13 14 15 16 17
[14] 18 19 20 21 22 23 24 25 26 27 28 29 30
[27] 31 32 33 34 35 36 37 38 39 40 41 42 43
[40] 44 45 46 47 48 49 50 51 52 53 54 55 56
[53] 57 58 59 60 61 62 63 64 65 66 67 68 69
[66] 70 71 72 73 74 75

* Містить числа 3.14, 2.71, 0, 13.
``` v2 <- c(3.14, 2.71, 0, 13)
v2
```
[1]  3.14  2.71  0.00 13.00

* Містить сто значень **TRUE**.
``` v3 <- c(rep(TRUE, 100))
v3
```
  [1] TRUE TRUE TRUE TRUE TRUE TRUE TRUE
  [8] TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [15] TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [22] TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [29] TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [36] TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [43] TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [50] TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [57] TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [64] TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [71] TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [78] TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [85] TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [92] TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [99] TRUE TRUE
 
## Task3
### Створити задану матрицю
* За допомогою **matrix**.
``` m1 <- matrix(c(0.5, 3.9, 0, 2, 1.3, 131, 2.2, 7, 3.5, 2.8, 4.6, 5.1), nrow = 4, ncol = 3)
m1
```
[,1]  [,2] [,3]
[1,]  0.5   1.3  3.5
[2,]  3.9 131.0  2.8
[3,]  0.0   2.2  4.6
[4,]  2.0   7.0  5.1

* За допомогою **cbind**.
``` m2 <- cbind(c(0.5, 3.9, 0, 2),c(1.3, 131, 2.2, 7), c(3.5, 2.8, 4.6, 5.1))
m2
```
[,1]  [,2] [,3]
[1,]  0.5   1.3  3.5
[2,]  3.9 131.0  2.8
[3,]  0.0   2.2  4.6
[4,]  2.0   7.0  5.1

## Task4
### Створити довільний список (list), в який включити всі базові типи. 
``` g <- list(gVal, gRound, gCompl, gDef, gLog)
print(g)
```
[[1]]
[1] 9.80665

[[2]]
[1] 10

[[3]]
[1] 9.8+0i

[[4]]
[1] "gravitational acceleration"

[[5]]
[1] TRUE

## Task5
### Створити фактор з трьома рівнями: *«baby», «child», «adult»*. 
``` f <- factor(c("child", "adult", "baby", "child", "baby", "adult", "adult", "child"))
f
```
[1] child adult baby  child baby  adult
[7] adult child
Levels: adult baby child

## Task6
### Знайти:
* індекс першого значення NA в заданому векторі;
``` v4 <- c(1:4, NA, 6, 7, NA, 9, NA, 11)
match(NA, v4)
```
[1] 5

* кількість значень NA.
``` sum(is.na(v4))
```
[1] 3

## Task7
### Створити довільний **data frame** та вивести в консоль.
``` spisok <- data.frame(name = c("Ivanov", "Petrov", "Sidorov"), mark=c(4,3,5))
spisok
```
 name mark
1  Ivanov    4
2  Petrov    3
3 Sidorov    5

## Task8
### Змінити імена стовпців цього **data frame**.
``` names(spisok) <- c("Surname", "Result")
spisok
```
  Surname Result
1  Ivanov      4
2  Petrov      3
3 Sidorov      5
