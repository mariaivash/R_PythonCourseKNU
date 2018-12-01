# Lab5
## Task1
### Написати функцію pmean, яка обчислює середнє значення (mean) забруднення сульфатами або нітратами серед заданого переліка моніторів.
*  Ця функція приймає три аргументи: «directory», «pollutant», «id». Directory – папка, в якій розміщені дані, pollutant – вид забруднення,id – перелік моніторів. Аргумент id має значення за замовчуванням 1:332. Функція повинна ігнорувати NA значення. 
```{r}
#Створюємо функцію
pmean <- function(pollutant, id = 1:332, directory="C:/Users/Mary/Documents/specdata") {
#Зчитуємо файл, задаємо забруднювач
  data1 = lapply(id, function(i) read.csv(paste(directory, "/", formatC(i,width = 3, flag = "0"), ".csv", sep=""))[[pollutant]])
  return (mean(unlist(data1), na.rm = TRUE))
  }

pmean("sulfate", 15)
[1] 1.098687
```
```{r}
pmean("nitrate", 88:100)
[1] 2.253701
```

## Task2
### Написати функцію complete, яка виводить кількість повних спостережень для кожного файлу. 
*  Функція приймає два аргументи: «Directory» та «id» та повертає data frame, в якому перший стовпчик – ім’я файлу, а другий – кількість повних спостережень. 
```{r}
#Створюємо функцію
complete <- function(id= 1:332, directory="C:/Users/Mary/Documents/specdata"){
  numrow <- numeric()
  #Зчитуємо файл, підраховуємо кількість рядків
    for (i in id) { 
      data2 <- read.csv(paste(directory, "/", formatC(i, width = 3, flag = "0"),  ".csv", sep = ""))
       numrow <- c(numrow,sum(complete.cases(data2)))
    }
return(data.frame(id, numrow))
  }
complete (c(2, 4, 8, 10,12))
  id numrow
1  2   1041
2  4    474
3  8    192
4 10    148
5 12     96
```

```{r}
complete (12:21)
 id numrow
1  12     96
2  13     46
3  14     96
4  15     83
5  16     60
6  17    927
7  18     84
8  19    353
9  20    124
10 21    426
```

## Task3
### Написати функцію corr, яка приймає два аргументи: directory (папка, де знаходяться файли спостережень) та threshold (порогове значення, за замовчуванням дорівнює 0) та обчислює кореляцію між сульфатами та нітратами для моніторів, кількість повних спостережень для яких більше порогового значення. 
* Функція повинна повернути вектор значень кореляцій. Якщо ні один монітор не перевищує порогового значення, функція повинна повернути numeric вектор довжиною 0. Для обчислення кореляції між сульфатами та нітратами використовуйте вбудовану функцію  «cor» з параметрами за замовчуванням.
```{r}
#Створюємо функцію
corr <- function(threshold = 0, directory="C:/Users/Mary/Documents/specdata") {
    corv <- NULL
#Зчитуємо файл, прописуємо умови кореляції
    for (i in 1:332) {
    data3 <- read.csv(paste(directory, "/", formatC(i, width = 3, flag = "0"),".csv", sep = ""))
       res <- data3[complete.cases(data3), ]
        if (nrow(res) > threshold)
        corv <- c(corv, cor(res[,"sulfate"], res[, "nitrate"]))
    }
    if(length(corv) > 0)
    return (corv)
    return (as.numeric(c()))
}
head(corr())
[1] -0.22255256 -0.01895754 -0.14051254
[4] -0.04389737 -0.06815956 -0.12350667
```

```{r}
head(corr(150))
[1] -0.01895754 -0.14051254 -0.04389737
[4] -0.06815956 -0.12350667 -0.07588814
```

```{r}
summary(corr())
 Min.  1st Qu.   Median     Mean    3rd Qu.     Max.
-1.00000 -0.05282  0.10718  0.13684  0.27831  1.00000 
```
