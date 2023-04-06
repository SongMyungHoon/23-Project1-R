# 송명훈
## 2023.04.06
---

* 매트릭스 사용

```R
> sore <- matrix(c(90,85,69,78,85,96,49,95,90,80,70,60), nrow = 4)
> sore
     [,1] [,2] [,3]
[1,]   90   85   90
[2,]   85   96   80
[3,]   69   49   70
[4,]   78   95   60

> rownames(sore) <- c('John','Tom','Mare','Jane')
> colnames(sore) <- c('English','Math','Science')
> sore
     English Math Science
John      90   85      90
Tom       85   96      80
Mare      69   49      70
Jane      78   95      60

View(sore) -- 뷰로 확인

> sore['John','Math']
[1] 85

> sore['Mare',]
English    Math Science 
     69      49      70 

> sore[,'English']
John  Tom Mare Jane 
  90   85   69   78 

```

* 데이터프레임 사용

```R
> city <- c("Seoul","Tokyo","Washington")
> rank <- c(1,3,2)
> city.info <- data.frame(city, rank)
> city.info
        city rank
1      Seoul    1
2      Tokyo    3
3 Washington    2

> iris[,c(1:2)]
    Sepal.Length Sepal.Width
1            5.1         3.5
2            4.9         3.0
3            4.7         3.2
4            4.6         3.1
5            5.0         3.6
# ~    ~    ~    ~    ~    ~    ~
149          6.2         3.4
150          5.9         3.0

> iris[1:5,c(1,3)]
  Sepal.Length Petal.Length
1          5.1          1.4
2          4.9          1.4
3          4.7          1.3
4          4.6          1.5
5          5.0          1.4
 
> dim(iris)     # 행과 열의 개수 보이기
[1] 150   5
> nrow(iris)    # 행의 개수 보이기
[1] 150
> colnames(iris)# 열 이름 보이기, name() 함수와 결과 동일
[1] "Sepal.Length" "Sepal.Width"  "Petal.Length" "Petal.Width"  "Species"    

> head(iris)
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
> tail(iris)
    Sepal.Length Sepal.Width Petal.Length Petal.Width   Species
145          6.7         3.3          5.7         2.5 virginica
146          6.7         3.0          5.2         2.3 virginica
147          6.3         2.5          5.0         1.9 virginica
148          6.5         3.0          5.2         2.0 virginica
149          6.2         3.4          5.4         2.3 virginica
150          5.9         3.0          5.1         1.8 virginica

> str(iris)
'data.frame':	150 obs. of  5 variables:
 $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
 $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
 $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
 $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...
 $ Species     : Factor w/ 3 levels "setosa","versicolor",..: 1 1 1 1 1 1 1 1 1 1 ...

> iris[,5]
  [1] setosa     setosa     setosa     setosa     setosa     setosa     setosa     setosa     setosa    
# ~    ~    ~    ~    ~    ~    ~    ~    ~    ~    ~    ~    ~    ~   
 [37] setosa     setosa     setosa     setosa     setosa     setosa     setosa     setosa     setosa    
 [46] setosa     setosa     setosa     setosa     setosa     versicolor versicolor versicolor versicolor
 [55] versicolor versicolor versicolor versicolor versicolor versicolor versicolor versicolor versicolor
# ~    ~    ~    ~    ~    ~    ~    ~    ~    ~    ~    ~    ~    ~
[145] virginica  virginica  virginica  virginica  virginica  virginica 
Levels: setosa versicolor virginica

> levels(iris[,5])
[1] "setosa"     "versicolor" "virginica" 
> table(iris[,"Species"])
    setosa versicolor  virginica 

> head(iris[,-5])
  Sepal.Length Sepal.Width Petal.Length Petal.Width
1          5.1         3.5          1.4         0.2
2          4.9         3.0          1.4         0.2
3          4.7         3.2          1.3         0.2
4          4.6         3.1          1.5         0.2
5          5.0         3.6          1.4         0.2
6          5.4         3.9          1.7         0.4

> head(iris[,-5])
  Sepal.Length Sepal.Width Petal.Length Petal.Width
1          5.1         3.5          1.4         0.2
2          4.9         3.0          1.4         0.2
3          4.7         3.2          1.3         0.2
4          4.6         3.1          1.5         0.2
5          5.0         3.6          1.4         0.2
6          5.4         3.9          1.7         0.4

> colSums(iris[,c(-1,-5)])
 Sepal.Width Petal.Length  Petal.Width 
       458.6        563.7        179.9 
> 

> z<- matrix(1:20, nrow = 4,ncol = 5)
> z
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    5    9   13   17
[2,]    2    6   10   14   18
[3,]    3    7   11   15   19
[4,]    4    8   12   16   20

> t(z) # 행렬을 역으로 조회
     [,1] [,2] [,3] [,4]
[1,]    1    2    3    4
[2,]    5    6    7    8
[3,]    9   10   11   12
[4,]   13   14   15   16
[5,]   17   18   19   20

> IR.1 <- subset(iris, Species == "setosa") # setosa 값만 추출
> head(IR.1)
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
> tail(IR.1)
   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
45          5.1         3.8          1.9         0.4  setosa
46          4.8         3.0          1.4         0.3  setosa
47          5.1         3.8          1.6         0.2  setosa
48          4.6         3.2          1.4         0.2  setosa
49          5.3         3.7          1.5         0.2  setosa
50          5.0         3.3          1.4         0.2  setosa

```

* 매트릭스 데이터프라임에 함수 적용

```R

> a <- matrix(1:20,4,5)
> a
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    5    9   13   17
[2,]    2    6   10   14   18
[3,]    3    7   11   15   19
[4,]    4    8   12   16   20
> 2*a          # a에 값에 산술만 적용해서 조회만함(오버라이트 X)
     [,1] [,2] [,3] [,4] [,5]
[1,]    2   10   18   26   34
[2,]    4   12   20   28   36
[3,]    6   14   22   30   38
[4,]    8   16   24   32   40
> a
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    5    9   13   17
[2,]    2    6   10   14   18
[3,]    3    7   11   15   19
[4,]    4    8   12   16   20
> a <- a*3     # a에 산술값을 덮어씀(오버라이트 O)
> a
     [,1] [,2] [,3] [,4] [,5]
[1,]    3   15   27   39   51
[2,]    6   18   30   42   54
[3,]    9   21   33   45   57
[4,]   12   24   36   48   60

```
* 데이터 판별
```R
 > class(iris) # iris 데이터셋의 자료구조 확인
[1] "data.frame"
> class(state.x77) # state.x77 데이터셋의 자료구조 확인
[1] "matrix" "array" 
> is.matrix(iris) # 데이터셋이 매트릭스인지 확인하는 함수
[1] FALSE
> is.data.frame(iris) # 데이터셋이 데이터프레임인지 확인하는 함수
[1] TRUE
> is.matrix(state.x77)
[1] TRUE
> is.data.frame(state.x77)
[1] FALSE

 ```

* 데이터 변환

```R
> # 매트릭스를 데이터프레임으로 변환
> st <- data.frame(state.x77)
> head(st)
           Population Income Illiteracy Life.Exp Murder HS.Grad Frost   Area
Alabama          3615   3624        2.1    69.05   15.1    41.3    20  50708
Alaska            365   6315        1.5    69.31   11.3    66.7   152 566432
Arizona          2212   4530        1.8    70.55    7.8    58.1    15 113417
Arkansas         2110   3378        1.9    70.66   10.1    39.9    65  51945
California      21198   5114        1.1    71.71   10.3    62.6    20 156361
Colorado         2541   4884        0.7    72.06    6.8    63.9   166 103766
> class(st)
[1] "data.frame"

> # 데이터프레임을 매트릭스으로 변환
> iris.m <- as.matrix(state.x77)
> head(iris.m)
           Population Income Illiteracy Life Exp Murder HS Grad Frost   Area
Alabama          3615   3624        2.1    69.05   15.1    41.3    20  50708
Alaska            365   6315        1.5    69.31   11.3    66.7   152 566432
Arizona          2212   4530        1.8    70.55    7.8    58.1    15 113417
Arkansas         2110   3378        1.9    70.66   10.1    39.9    65  51945
California      21198   5114        1.1    71.71   10.3    62.6    20 156361
Colorado         2541   4884        0.7    72.06    6.8    63.9   166 103766
> class(iris.m)
[1] "matrix" "array" 

```
* 데이터의 입력과 출력
```R
> # 데이터입력
> age <- c(28, 17, 35, 46, 23, 67, 30, 50)
> age
[1] 28 17 35 46 23 67 30 50

> # 정보 추출
> young <- min(age)
> old <- max(age)

> # 처리 결과 출력
> cat('가장 젋은 사람의 나이는', young,'이고,',
      '가장 나이든 사람의 나이는', old, '입니다.\n')
가장 젋은 사람의 나이는 17 이고, 가장 나이든 사람의 나이는 67 입니다.

```
* 화면에서 데이터 입력박기
```R
# 페키지 설치 및 사용
install.packages('svDialogs') # 따음표 사용
library(svDialogs) # 따음표 사용X

# 화면에서 입력 값 받아 가공해 보여주기
> user.input <- dlgInput('Input income')$res
> user.input
[1] "500"
> income <- as.numeric(user.input)
> income
[1] 500
> tax <- income * 0.05
> cat('세금:', tax)
세금: 25

```

* print()와 cat() 비교

```R
> x <- 26
> y <- '입니다'
> z <- c(10,20,30,40)
> print(x) # 하나의 값 출력 cat도 같음
[1] 26
> print(y) # 하나의 값 출력 cat도 같음
[1] "입니다"
> print(z) # 백터 출력 cat도 같음
[1] 10 20 30 40

> print(iris[1:5,]) # 데이터프레임 출력
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
> cat(iris[1:5],'\n') # 데이터프레임 출력(에러 발생)
# > Error 발생

> cat(x,y,'\n') # 두 값을 연결하여 출력
26 입니다 
> print(x,y) # 두개의 값 출력(에러 발생)
# > Error 발생

```

* 작업폴더 설정

```R
getwd() # 작업 폴더 확인하기
setwd('D:/602377108_SMH') # 작업 폴더 변경하기

```

* csv 파일에서 데이터 읽기

```R
> air <- read.csv('airquality.csv', header=T)
> head(air)
  Ozone Solar.R Wind Temp Month Day
1    41     190  7.4   67     5   1
2    36     118  8.0   72     5   2
3    12     149 12.6   74     5   3
4    18     313 11.5   62     5   4
5    NA      NA 14.3   56     5   5
6    28      NA 14.9   66     5   6
> class(air)
[1] "data.frame"

```

* csv 파일일 생성
```R
# 데이터 추출
> my.iris <- subset(iris, Species == 'setosa')
> head(my.iris)
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa

# csv파일로 생성
> write.csv(my.iris, 'my_iris.csv', row.names = F)

```

---
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
