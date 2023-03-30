# 송명훈
## 2023.03.30
---
* 현재 Environment 확인 - ls()  
* 삭제 - rm(list<-ls())  
---
```R
> foo<-100
> rm(foo)
> foo<- 100
> bar <- 300
> rm(list = ls())
```

* 1차원 자료 백터, 리스트, 페터
* 2차원 자료 매트릭스, 데이터프레임
```R
> d <- c(1,4,3,7,8)
> 2*d
[1]  2  8  6 14 16

> d-5
[1] -4 -1 -2  2  3

> 3*d+4
[1]  7 16 13 25 28


> x <- c(1,2,3,4)
> y <- c(5,6,7,8)
> x+y
[1]  6  8 10 12

> x*y
[1]  5 12 21 32

> z <- x+y
> z
[1]  6  8 10 12


> m <- c(1,2,3,4,5,6,7,8)
> sum(m)
[1] 36

> mean(m)
[1] 4.5

> length(m)
[1] 8


> d <- 1:9
> d>=5
[1] FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE

> d[d>5]
[1] 6 7 8 9

> sum(d>=5)
[1] 5

> m <- c(TRUE,TRUE,TRUE,TRUE,TRUE)
> sum(m)
[1] 5

> d[d>2 & d<5]
[1] 3 4

> sum(d[d>5])
[1] 30


> espresso <- c(4,5,3,6,5,4,7)
> americano <- c(63,68,64,68,72,89,94)
> latee<-c(61,70,59,71,71,92,88)
> sale.espresso <- 2 * espresso
> sale.americano <- 2.5 * americano
> sale.latee <- 3 * latee
> sale.day <- sale.espresso + sale.americano + sale.latee
> names(sale.day) <- c("월","화","수","목","금","토","일")
> sale.day
   월    화    수    목    금    토    일 
348.5 390.0 343.0 395.0 403.0 506.5 513.0 

> sale.all>350
   월    화    수    목    금    토    일 
FALSE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE 

> sale.all[sale.all>350]
   화    목    금    토    일 
390.0 395.0 403.0 506.5 513.0 


> bt <- c("A","A","B","B","B","AB","O")
> bt.new <- factor(bt)
> bt.new
[1] A  A  B  B  B  AB O 
Levels: A AB B O

> bt.new[1:4]
[1] A A B B

Levels: A AB B O
> as.integer(bt.new)
[1] 1 1 3 3 3 2 4


> h.list <- c("볼링","테니스","스키")
> person <- list(name="톰", age=25, student=TRUE, hobby=h.list)
> person
$name
[1] "톰"

$age
[1] 25

$student
[1] TRUE

$hobby
[1] "볼링"   "테니스" "스키"  

> person[1]
$name
[1] "톰"

> person[[1]]
[1] "톰"

> person$name
[1] "톰"


```
* 메트릭스(matrix) : 2차원배열, 같은 타입값을 갖는다  
```R
> z <- matrix(1:20, nrow = 4, ncol = 5)
> z
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    5    9   13   17
[2,]    2    6   10   14   18
[3,]    3    7   11   15   19
[4,]    4    8   12   16   20

> m1 <- cbind(x,y)
> m1
     x   y   
[1,] "1" "월"
[2,] "2" "화"
[3,] "3" "수"
[4,] "4" "목"

> m2 <- rbind(x,y)
> m2
  [,1] [,2] [,3] [,4]
x "1"  "2"  "3"  "4" 
y "월" "화" "수" "목"

> m3 <- rbind(x,m2)
> m3
  [,1] [,2] [,3] [,4]
x "1"  "2"  "3"  "4" 
x "1"  "2"  "3"  "4" 
y "월" "화" "수" "목"

> m4 <- cbind(z,x)
> m4
                    x
[1,]  1  2  3  4  5 1
[2,]  6  7  8  9 10 2
[3,] 11 12 13 14 15 3
[4,] 16 17 18 19 20 4

> z
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    2    3    4    5
[2,]    6    7    8    9   10
[3,]   11   12   13   14   15
[4,]   16   17   18   19   20

> z[2,3]
[1] 8

> z[2,]
[1]  6  7  8  9 10

> z[,3]
[1]  3  8 13 18

> z[1:2,]
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    2    3    4    5
[2,]    6    7    8    9   10

```

## 2023.03.27
---
* 깃 clone 연결하기  
  git clone https://github.com/SongMyungHoon/23-Project1-R.git

* 기존 컴퓨터에서 작업진행 시  
  git pull origin main
  
---
## 2023.03.23
---
*    패키지 설치 install.packages('ggplot2')  
     ex) install.packages('ggplot2'), install.packages("cowsay")

*    라이브러리 사용 - 라이브러리 사용 library(라이브러리 이름)  
     ex) library(ggplot2), library(cowsay)

```R
ggplot(data = iris, aes(x = Petal.Length, y = Petal.Width)) + geom_point()
say("Hello world", by = "random") 

Sys.time()

total <- 5050

cat(total)
cat("합계:", total)

a<-10;b<-20;c<-a+b
```

*    백터(vector)의 개념  
     * 일반적인 프로그래밍 용어로는 1차원 배열(array)이라고도 함

```R

> score.1 <- 68; score.2 <- 95; score.3 <- 83; score.4 <- 76; score.5 <- 90
> score.6 <- 80; score.7 <- 85; score.8 <- 91; score.9 <- 82; score.10 <- 70

> total <- score.1 + score.2 + score.3 + score.4 + score.5 + score.6 + score.7 + score.8 + score.9 + score.10
> print(total/10)
  
> score <- c(68, 95, 83, 76, 90, 80, 85, 91, 82, 70)
> mean(score)
```

* 연속적 숫자로 이루어진 백터  
     * v1 <- 50:90
     * v2 <- c(1, 2, 5, 50:90)
     * v3 <- seq(1, 101, 3)
     * v5 <- rep(1, times=5)
     * v6 <- rep(1:5, times=3)
     * v7 <- rep(1,5,9, times=3)
```R
> print(v1)
 [1] 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81
[33] 82 83 84 85 86 87 88 89 90
> print(v2)
 [1]  1  2  5 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78
[33] 79 80 81 82 83 84 85 86 87 88 89 90
> print(v3)
 [1]   1   4   7  10  13  16  19  22  25  28  31  34  37  40  43  46  49  52  55  58  61  64  67  70  73  76  79  82  85  88  91  94  97 100
> print(v5)
[1] 1 1 1 1 1
> print(v6)
 [1] 1 2 3 4 5 1 2 3 4 5 1 2 3 4 5
> print(v7)
[1] 1 1 1 1 1
```

* 백터값의 이름  
```R
> absent <- c(8, 4, 3, 4, 6)
> names(absent) <- c('mon', 'tus', 'wed', 'thu', 'fri')

> print(absent)
mon tus wed thu fri 
  8   4   3   4   6 

> print(absent[5])
fri 
  6 

-- 백터 이름으로 결과 출력
> absent["thu"]
thu 
  4 

> a <- paste(1:12,'월', sep="")
> print(a)
 [1] "1월"  "2월"  "3월"  "4월"  "5월"  "6월"  "7월"  "8월"  "9월"  "10월" "11월" "12월"

> a <- paste(1:12,'', sep="월")
> print(a)
 [1] "1월"  "2월"  "3월"  "4월"  "5월"  "6월"  "7월"  "8월"  "9월"  "10월" "11월" "12월"
```

---
## 2023.03.16
---
* R언어의 특징  
     * 테이터 분석에 특화된 언어
     * 탄탄한 사용자 커뮤니티
     * 다양한 패키지 제공
     * 미적이고 기능적인 통계 그래프 제공
     * 편리한 프로그래밍 환경
     * 무료 사용

* R을 배우는 이유
     * 4차 산업혁명의 중심의 '데이터'

* Rstudio 영역
     * 소스영역,  콘솔영역, 환경영역, 파일영역

---
코드
```R
> 3+(4*5)
[1] 23

> A <- 51:80
> print(A)
[1] 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80

한줄에 여러개 출력
> 3+(4*5); A <- 51:80; print(A)

> 10/3  
[1] 3.333333

> 10%%3
[1] 1
```

---
## 2023.03.09
---
```R


```
