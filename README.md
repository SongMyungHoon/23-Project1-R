# 송명훈
## 2023.05.18
* ## 정렬

```R
# 숫자정렬
> v1 <- c(1,7,6,8,4,2,3)
> v1 <- sort(v1) # 오름차순
> v1
[1] 1 2 3 4 6 7 8
> v2 <- sort(v1, decreasing = T) # 내림차순
> v2
[1] 8 7 6 4 3 2 1

# 한글 정렬
> name <- c('정대일', '강재구', '신현석', '홍길동')
> sort(name)
[1] "강재구" "신현석" "정대일" "홍길동"
> sort(name, decreasing = T)
[1] "홍길동" "정대일" "신현석" "강재구"

# 정렬하여 인덱스 값 출력
> order(name)
[1] 2 3 1 4
> order(name, decreasing = T)
[1] 4 1 3 2
> idx <- order(name)
> name[idx]
[1] "강재구" "신현석" "정대일" "홍길동"

```

* ## 특정 열의 값들을 기준으로 행을 재배열하는 방법

```R
> head(iris)
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa

> head(order(iris$Sepal.Length))
[1] 14  9 39 43 42  4

> head(iris[order(iris$Sepal.Length),]) # 오름차순으로 정렬
   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
14          4.3         3.0          1.1         0.1  setosa
9           4.4         2.9          1.4         0.2  setosa
39          4.4         3.0          1.3         0.2  setosa
43          4.4         3.2          1.3         0.2  setosa
42          4.5         2.3          1.3         0.3  setosa
4           4.6         3.1          1.5         0.2  setosa

> head(iris[order(iris$Sepal.Length, decreasing = T),])  # 내일차순으로 정렬
    Sepal.Length Sepal.Width Petal.Length Petal.Width   Species
132          7.9         3.8          6.4         2.0 virginica
118          7.7         3.8          6.7         2.2 virginica
119          7.7         2.6          6.9         2.3 virginica
123          7.7         2.8          6.7         2.0 virginica
136          7.7         3.0          6.1         2.3 virginica
106          7.6         3.0          6.6         2.1 virginica

> iris.new <- iris[order(iris$Sepal.Length),] # 정렬된 데이터를 저장
> head(iris.new)
   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
14          4.3         3.0          1.1         0.1  setosa
9           4.4         2.9          1.4         0.2  setosa
39          4.4         3.0          1.3         0.2  setosa
43          4.4         3.2          1.3         0.2  setosa
42          4.5         2.3          1.3         0.3  setosa
4           4.6         3.1          1.5         0.2  setosa

> # 정렬 기준이 2개인 경우
> head(iris[order(iris$Sepal.Length, decreasing = T, iris$Sepal.Length),])
    Sepal.Length Sepal.Width Petal.Length Petal.Width   Species
132          7.9         3.8          6.4         2.0 virginica
118          7.7         3.8          6.7         2.2 virginica
119          7.7         2.6          6.9         2.3 virginica
123          7.7         2.8          6.7         2.0 virginica
136          7.7         3.0          6.1         2.3 virginica
106          7.6         3.0          6.6         2.1 virginica

```

* ## 샘플링과 조합이란 무엇인가

```R
> x <- 1:100
> sample(x, size = 10, replace = FALSE) # 비복원식 샘플추출
 [1] 97 48 51 67 37 93 60  7 16  9
> sample(x, size = 10, replace = TRUE) # 복원식 샘플추출
 [1] 90 74 32 18 27 55 72 15 28  8


> idx <- sample(1:nrow(iris), size = 50, replace = F)
> iris.50 <- iris[idx,]
> dim(iris.50)
[1] 50  5
> head(iris.50)
    Sepal.Length Sepal.Width Petal.Length Petal.Width    Species
53           6.9         3.1          4.9         1.5 versicolor
14           4.3         3.0          1.1         0.1     setosa
17           5.4         3.9          1.3         0.4     setosa
148          6.5         3.0          5.2         2.0  virginica
71           5.9         3.2          4.8         1.8 versicolor
83           5.8         2.7          3.9         1.2 versicolor

```
* ## 조합
```R
 combn(1:5,3) # 1~5에서 3개를 뽑는 조합
     [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10]
[1,]    1    1    1    1    1    1    2    2    2     3
[2,]    2    2    2    3    3    4    3    3    4     4
[3,]    3    4    5    4    5    5    4    5    5     5
> x <- c("red","green","blue","black","white")
> com <- combn(x,2)
> com
     [,1]    [,2]   [,3]    [,4]    [,5]    [,6]    [,7]    [,8]    [,9]    [,10]  
[1,] "red"   "red"  "red"   "red"   "green" "green" "green" "blue"  "blue"  "black"
[2,] "green" "blue" "black" "white" "blue"  "black" "white" "black" "white" "white"

> for(i in 1:ncol(com)) {
+   cat(com[,i], "\n")
+ }
red green 
red blue 
red black 
red white 
green blue 
green black 
green white 
blue black 
blue white 
black white 

```

* ## 품종별 꽃잎 꽃받침의 폭과 길이의 평균
```R
# aggregate(데이터셋, 열의 값, 평균)
> agg <- aggregate(iris[,-5], by=list(iris$Species), FUN = mean) 
> agg
     Group.1 Sepal.Length Sepal.Width Petal.Length Petal.Width
1     setosa        5.006       3.428        1.462       0.246
2 versicolor        5.936       2.770        4.260       1.326
3  virginica        6.588       2.974        5.552       2.026

> agg <- aggregate(mtcars, by=list(cyl=mtcars$cyl, vs=mtcars$vs), FUN = max)
> agg
  cyl vs  mpg cyl  disp  hp drat    wt  qsec vs am gear carb
1   4  0 26.0   4 120.3  91 4.43 2.140 16.70  0  1    5    2
2   6  0 21.0   6 160.0 175 3.90 2.875 17.02  0  1    5    6
3   8  0 19.2   8 472.0 335 4.22 5.424 18.00  0  1    5    8
4   4  1 33.9   4 146.7 113 4.93 3.190 22.90  1  1    5    2
5   6  1 21.4   6 258.0 123 3.92 3.460 20.22  1  0    4    4

```

* ## 나무지도
```R
install.packages('treemap')
library(treemap)

> data(GNI2014)
> head(GNI2014)
  iso3          country     continent population    GNI
3  BMU          Bermuda North America      67837 106140
4  NOR           Norway        Europe    4676305 103630
5  QAT            Qatar          Asia     833285  92200
6  CHE      Switzerland        Europe    7604467  88120
7  MAC Macao SAR, China          Asia     559846  76270
8  LUX       Luxembourg        Europe     491775  75990

treemap(GNI2014,
        index=c('continent', 'iso3'),
        vSize = 'population',
        vColor = 'GNI',
        type = 'value',
        #bg.labels = 'yellow',
        title = "World's GNI")

```

---
## 2023.05.11
---
* ### 두 변수의 상관관계
```R
# 2개 열의 산점도 1
> # 데이터 확인
> head(pressure)
  temperature pressure
1           0   0.0002
2          20   0.0012
3          40   0.0060
4          60   0.0300
5          80   0.0900
6         100   0.2700
 
> # 산점도 작성
> plot(pressure$temperature,
+      pressure$pressure,
+      main = '온도와 기압',
+      xlab = '온도(화씨)',
+      ylab = '기압'
+ )

# 2개 열 산점도 2
# 데이터 확인
> head(cars)
  speed dist
1     4    2
2     4   10
3     7    4
4     7   22
5     8   16
6     9   10

> # 다중변수의 산점도 작성
> plot(cars$speed,
+      cars$dist,
+      main = '자동차 속도와 제동거리',
+      xlab = '속도',
+      ylab = '제동거리'
+ )

> # 상관계수
> cor(cars$speed, cars$dist)
[1] 0.8068949
```

* ### 백터의 결측값
```R
> z <- c(1,2,3,NA,5,NA,8)
> sum(z)
[1] NA
> is.na(z)
[1] FALSE FALSE FALSE  TRUE FALSE  TRUE FALSE
> sum(is.na(z))
[1] 2
> sum(z, na.rm=TRUE)
[1] 19

> z1 <- c(1,2,3,NA,5,NA,8)
> z2 <- c(5,8,1,NA,3,NA,7)
> z1[is.na(z1)] <- 0     # NA를 0로 치환
> z1
[1] 1 2 3 0 5 0 8
> z3 <- as.vector(na.omit(z2))     # NA를 제거
> z3
[1] 5 8 1 3 7
```

* ### 특정값에 NA 대입
```R
# NA를 포함하는 test 데이터 생성
> x <- iris
> x[1,2] <- NA;
> x[1,3] <- NA;
> x[2,3] <- NA;
> x[3,4] <- NA;
> head(x)
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1          NA           NA         0.2  setosa
2          4.9         3.0           NA         0.2  setosa
3          4.7         3.2          1.3          NA  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
 
```

* ### 매트릭스와 데이터프레임의 결측값
```R
# 열(col)별로 결측값 확인
# for를 이용한 방법
> for(i in 1:ncol(x)){
+   this.na <- is.na(x[,i])
+   cat(colnames(x)[i], '\t',sum(this.na), '\n')
+ }
Sepal.Length     0 
Sepal.Width      1 
Petal.Length     2 
Petal.Width      1 
Species          0 

# apply를 이용한 방법
> col_na <- function(y){
+   return(sum(is.na(y)))
+ }
> na_count <-apply(x,2,FUN=col_na)
> na_count
Sepal.Length  Sepal.Width Petal.Length  Petal.Width      Species 
           0            1            2            1            0 

# 행(row)별로 결측값 확인
> rowSums(is.na(x))
  [1] 2 1 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
 [67] 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
[133] 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
> sum(rowSums(is.na(x)>0))
[1] 4
> sum(is.na(x))
[1] 4

> head(x)
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1          NA           NA         0.2  setosa
2          4.9         3.0           NA         0.2  setosa
3          4.7         3.2          1.3          NA  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
> x[!complete.cases(x),]
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1          NA           NA         0.2  setosa
2          4.9         3.0           NA         0.2  setosa
3          4.7         3.2          1.3          NA  setosa
> y <- x[complete.cases(x),]
> head(y)
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
7          4.6         3.4          1.4         0.3  setosa
8          5.0         3.4          1.5         0.2  setosa
9          4.4         2.9          1.4         0.2  setosa

```
---
## 2023.05.04

* 복수의 선그래프 작성

```R
month = 1:12 # 데이터 입력
late1 = c(5,8,7,9,4,6,12,13,8,6,6,4)
late2 = c(4,6,5,7,8,10,7,8,4,12,5,8)

plot(month,
     late,
     main='지각생 통계',
     type = 'b',
     lty=1,
     col = 'red',
     lwd=1,
     xlab = 'Month',
     ylab = 'Late cnt'
)

lines(month,
      late2,
      type = 'b',
      col = 'blue'
)

```

* 상자그림

```R
> dist <- cars[,2]
> boxplot(dist,mmain='자동차제동거리') #간단한 상자그림 출력

> boxplot.stats(dist)
$stats
[1]  2 26 36 56 93
$n
[1] 50
$conf
[1] 29.29663 42.70337
$out
[1] 120

boxplot(Petal.Length~Species, # 데이터 그룹정보
        data = iris, # 데이터가 저장된 자료구조
        main = '품종별 꽃잎의 길이', # 그래프의 제목
        col = c('green','yellow','blue') # 상자들의 색
) 

```

* 산점도

```R
wt <- mtcars$wt # 중량 데이터
mpg <- mtcars$mpg #연비 데이터
plot(wt,mpg,
     main = '중량-연비 그래프',
     xlab = '중량',
     ylab = '연비',
     col = 'red',
     pch = 19
)

# 멀티 산점도
  vars <- c('mpg','disp','drat','wt') # 대상 변수
  target <- mtcars[,vars] # 대상 데이터 생성
  plot(target,
       main = 'multi plots', # 대상 데이터
)

```

* 여러 변수들 간의 산점도

```R
group <- as.numeric(iris$Species)
group

iris.2 <- iris[,3:4]
color <- c('red','green','blue')

plot(iris.2,
     main = 'Iris plot',
     pch = group,
     col = color[group]
)

legend(x = 'bottomright',
     legend = levels(iris$Species),
     col = c('red','green','blue'),
     pch = c(1:3)
)

```

* 단일변수 데이터를 분석

```R

install.packages('carData')
library(carData)

#W (1) 데이터 준비
room.class <- TitanicSurvival$passengerClass
room.class

# (2) 도수분포 계산
tbl <- table(room.class)
tbl
sum(tbl)

# (3) 막대그래프 작성
barplot(tbl,
        main = '선실별 탑승객',
        xlab = '선실 등급',
        ylab = '탑승객수',
        col = c('blue','green', 'yellow')
)

```

---
## 2023.04.27

* 막대그래프 작성의 기초

```R
# 도수분포표 계산하기
> favorite <- c('winter','summer','spring','summer','summer','fall','fall','fall','summer','spring','spring')

> favorite
 [1] "winter" "summer" "spring" "summer" "summer" "fall"   "fall"   "fall"  
 [9] "summer" "spring" "spring"

> table(favorite)
favorite
  fall spring summer winter 
     3      3      4      1 

# 막대그래프 작성의 기초
> ds <- table(favorite)
> ds
favorite
  fall spring summer winter 
     3      3      4      1 
# 막대그래프로 조회 함수 # barplot(테이블, main = 테이블타이틀, col = 색상, , 
> barplot(ds, main = 'Favorite Season') 
> barplot(ds, main = 'Favorite Season', col = c('#ffffff','red','blue','green')
          , xlab = '계절'                         # xlab/ylab xy명
          , ylab = '빈도수'
          , horiz=TRUE                            # horiz = 가로막대
          , names = c('가을','봄','여름','겨울')   # names = 막대이름 
          , las=2)                                # las = 0/1/2/3 - 정상/수평/축기준수직/수직
```

```R
# 랜덤색상 
> rainbow(4)
[1] "#FF0000" "#80FF00" "#00FFFF" "#8000FF"

```

* 중첩 그룸의 막대그래프

```R
> age.A <- c(13709, 10974, 7979, 5000, 4250)
> age.B <- c(17540, 29701, 36209, 33947, 24487)
> age.C <- c(991, 2195, 5366, 12980, 19007)

> ds <- rbind(age.A, age.B, age.C)
> colnames(ds) <- c('1970','1990','2010','2030','2050')
> ds
       1970  1990  2010  2030  2050
age.A 13709 10974  7979  5000  4250
age.B 17540 29701 36209 33947 24487
age.C   991  2195  5366 12980 19007

> # 중첩 그래프 작성 
> barplot(ds, main = '인구 추정'
          , col = rainbow(3)  # col = 색상
          , beside = TRUE     # beside = 중첩아닌형태
          # legend.text = T   # 색인설명 legend.text = T(색인)
          , legend.text = c('0~14세','15~64세','65세이상')  #text 이름변경
          # args.legend(x 출력 위치 왼쪽/오른쪽,테두리선(n/o), inset x,y축이동)
          , args.legend = list(x='topright',bty='n',inset=c(-0.25,0))
          )

```

* 히스토그램을 작성

```R
> head(cars)
  speed dist
1     4    2
2     4   10
3     7    4
4     7   22
5     8   16
6     9   10

> dist <- cars[,2]
> dist
 [1]   2  10   4  22  16  10  18  26  34  17  28  14  20  24  28  26  34  34  46  26  36  60  80  20  26  54  32  40  32  40  50
[32]  42  56  76  84  36  46  68  32  48  52  56  64  66  54  70  92  93 120  85

# 히스토그램 작성
> hist(dist,
+      main = 'Histogram for 제동거리', #제목
+      xlab = '제동거리',     # x축 레이블
+      ylab = '빈도수',       # y축 레이블
+      border = 'blue',       # 막대의 테두리색
+      col = 'green',         # 막대의 색상
+      las=2,
+      breaks=5)

> result <- hist(dist, main = 'histogram for 제동거리', breaks=5)
> result
$breaks
[1]   0  20  40  60  80 100 120

$counts
[1] 10 18 11  6  4  1

$density
[1] 0.010 0.018 0.011 0.006 0.004 0.001

$mids
[1]  10  30  50  70  90 110

$xname
[1] "dist"

$equidist
[1] TRUE

attr(,"class")
[1] "histogram"

```

* 다중 그래프
```R
par(mfrow=c(2,2),mar=c(3,3,4,2)) #화면 분할 2x2

hist(iris$Sepal.Length, # 그래프1
     main = 'Sepal.Length',
     col ='orange')

barplot(table(mtcars$cyl), # 그래프2
        main = 'mtcars',
        col=c('red','green','blue'))

barplot(table(mtcars$gear), # 그래프3
        main = 'mtcars',
        col=rainbow(3),
        horiz=TRUE)

pie(table(mtcars$cyl), # 그래프4
    main = 'mtcars',
    col=topo.colors(3),
    radius=2)

par(mfrow=c(1,1),mar=c(5,4,4,2)+.1) #화면 분할 취소

```
* 원그래프와 선그래프

```R
#데이터 입력
> favorite <- c('winter','summer','spring','summer','summer','fall','fall','fall','summer','spring','spring')
> favorite
 [1] "winter" "summer" "spring" "summer" "summer" "fall"   "fall"   "fall"   "summer" "spring" "spring"

> table(favorite)
favorite
  fall spring summer winter 
     3      3      4      1 

> ds <- table(favorite)
> ds
favorite
  fall spring summer winter 
     3      3      4      1 

# 원그래프 출력
> pie(ds, main='선호 계절',
+     radius = 1)

# 패키지 사용하여 3D원그래프 출력
install.packages('plotrix')
library(plotrix)
# 3D원 출력
pie3D(ds, main='선호 계절',
    col = rainbow(5),
    radius = 1)

```

* 꺽은선 그래프

```R
month <- 1:12
late <- c(5, 8, 7, 9, 4, 6, 12, 13, 8, 6, 6, 4)
plot(month,
     late,
     main='지각생 통계',
     type = 'l', # l 선, b/o 선위에 점, s 꺽인선
     lty=1,
     lwd=1,
     xlab = 'Month',
     ylab = 'Late cnt')
     
```

---
## 2023.04.13

* 실행 결과를 파일로 출력

```R
sink('resul.txt', append=T) # 파일로 출력 시작 / append=T 파일 이어쓰기
cat('a+b=', a+b, '\n')
sink()  # 파일로 출력 종료

sink('resul.txt', append=F) # 파일로 출력 시작 / append=F 파일 새로만들기
cat("Hello world\n") 
sink()  # 파일로 출력 종료

```

* if-else문

```R
> job.type <- 'A'
> if (job.type == 'B'){
+   bonus <- 200
+ }else{
+   bonus <- 100
+ }

> print(bonus)
[1] 100

```

* ifelse문

```R
> a <- 10
> b <- 20

> ifelse(a>b,c <- a,c <- b)
[1] 20
> print(c)
[1] 20

```

* for문

```R
> for(i in 1:5){
+   print('*')
+ }
[1] "*"
[1] "*"
[1] "*"
[1] "*"
[1] "*"

```

* while 문

```R
> sum <- 0
> i <- 1
> while(i <= 100){
+   sum <- sum + i
+   i <- i + 1
+ }
> print(sum)
[1] 5050

```

* apply() 계열 함수 - 행/열 1/2

```R
> apply(iris[,1:4], 1, mean) # 행 방향으로 함수 적용
  [1] 2.550 2.375 2.350 2.350 2.550 2.850 2.425 2.525 2.225 2.400 2.700 2.500 2.325 2.125 2.800 3.000
 [17] 2.750 2.575 2.875 2.675 2.675 2.675 2.350 2.650 2.575 2.450 2.600 2.600 2.550 2.425 2.425 2.675
 [33] 2.725 2.825 2.425 2.400 2.625 2.500 2.225 2.550 2.525 2.100 2.275 2.675 2.800 2.375 2.675 2.350
 [49] 2.675 2.475 4.075 3.900 4.100 3.275 3.850 3.575 3.975 2.900 3.850 3.300 2.875 3.650 3.300 3.775
 [65] 3.350 3.900 3.650 3.400 3.600 3.275 3.925 3.550 3.800 3.700 3.725 3.850 3.950 4.100 3.725 3.200
 [81] 3.200 3.150 3.400 3.850 3.600 3.875 4.000 3.575 3.500 3.325 3.425 3.775 3.400 2.900 3.450 3.525
 [97] 3.525 3.675 2.925 3.475 4.525 3.875 4.525 4.150 4.375 4.825 3.400 4.575 4.200 4.850 4.200 4.075
[113] 4.350 3.800 4.025 4.300 4.200 5.100 4.875 3.675 4.525 3.825 4.800 3.925 4.450 4.550 3.900 3.950
[129] 4.225 4.400 4.550 5.025 4.250 3.925 3.925 4.775 4.425 4.200 3.900 4.375 4.450 4.350 3.875 4.550
[145] 4.550 4.300 3.925 4.175 4.325 3.950

> apply(iris[,1:4], 2, mean) # 열 방향으로 함수 적용
Sepal.Length  Sepal.Width Petal.Length  Petal.Width 
    5.843333     3.057333     3.758000     1.199333 

```

* 사용자 정의 함수

```R
> # 큰값 구하기
> mymax <- function(x, y=0){
+   if(x>y){
+     return(x)
+   }else{
+     return(y)
+   }
+ }

> mymax(1,5)
[1] 5

> mymax(1)
[1] 1
```

* 사용자 정의 함수의 저장과 재실행

```R
# mydiv.R 코드 / 파일경로 'D:/602377108_SMH'
mydiv <-function(x,y){
  return (x+y)
}

# 사용자 정의 함수의 저장과 재실행 코드
> setwd('D:/602377108_SMH') # 파일 경로 지정
> source('mydiv.R')
> # 함수 사용
> a <- mydiv(10,20)
> b <- mydiv(20,30)

> a+b
[1] 80

> mydiv(mydiv(20,2),5)
[1] 27

```

* 조건에 맞는 데이터의 위치를 찾아보기

```R
> score <- c(76, 84, 69, 50, 95, 60, 82, 71, 88, 84)
> which(score ==69)
[1] 3
> which(score >= 85)
[1] 5 9
> max(score)
[1] 95
> min(score)
[1] 50
> which.min(score)
[1] 4

> idx <- which(score<=60)
> score[idx] <- 61
> score
 [1] 76 84 69 61 95 61 82 71 88 84

```

---
## 2023.04.06

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

---
## 2023.03.27

* 깃 clone 연결하기  
  git clone https://github.com/SongMyungHoon/23-Project1-R.git

* 기존 컴퓨터에서 작업진행 시  
  git pull origin main
  
---
## 2023.03.23

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

```R


```
