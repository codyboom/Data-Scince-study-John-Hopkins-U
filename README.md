  a<- available.packages(3)
  install.packages(sladify)
install.packages("ggplot2")  
library(ggplot2)  
search()
install.packages("devtools")
library(devtools)
find_rtools()
?search
search()

#Hi there, I am Kirill and I have Rstudio
x <- 4L
x
class(x)
x <- c(4, "a", TRUE)
class(x)
x <- c(1,3, 5);y <- c(3, 2, 10)
cbind(x,y)
x <- list(2, "a", "b", TRUE)

x[[2]]
x <- 1:4;y <- 2
x+y
x <- c(3, 5, 1, 10, 12, 6)
x[x < 6] = 0
x
x<-data.frame(hw1)
x
x[152:153,]
x[47,"Ozone"]
anyNA(x)
sum(is.na(x))

mean(x[,"Temp"], na.rm = T)
good<-complete.cases(hw1)
y<-hw1[good, ][,c("Ozone","Temp","Solar.R","Month")]
m<-subset(y,Month==5)
m
which(m==max(m[,"Ozone"]))
x<-data.frame(hw1)
u<-subset(x,Month==5)
which(u==max(u[,"Ozone"]))

i<-subset(x,Month==5)
max(i[,"Ozone"], na.rm =T)
i
?max
sum(is.na(x[,"Ozone"]))
install.packages("swirl")
library("swirl")
swirl()
Kiril
Kirill
swirl(
)
install_from_swirl("R Programming")
1
install_from_swirl("R Programming")
swirl()

#Loops

if(x>3) {
  y<-10
} esle {
    y<-0
}
x<-2

for(b in 1:10){
  print(b)
}

## "for" function
x<-c("a","b","c","d")
for(i in 1:4){
  print(x[i])
}

for(i in seq_along(x)){
  print(x[i])
}

for(letter in x){
  print(letter)
}

#Nested for loops

x<-matrix(1:6, 2,3)
for(i in seq_len(nrow(x))){
  for(j in seq_len(ncol(x))){
    print(x[i,j])
  }
}
}
#While loop
  
count<-0
  while (count>10){
    print(count)
    count<-count+11
      print(count)
  }

z<-5

while(z >=3 && z <=10){
  print(z)
  coin <-rbinom(1,1,0.5)
  if(coin==1){
    z<-z+1
  }else{
    z<-z-1
  }
}
# Conrol structures: repeat, next, break
##Repeat
###Repeat initiates an Infinite loop.
x0<-1
tol<- 1e-8
repeat{
  x1<- computeEstimate()
  if(abs(x1-))
}
  for (i in 1:100){
    if( i>=20)
      next
  }
  }
  # 19.04 TEST week2
  
  getwd("~/Specdata")
  setwd("C:/Users/Dell/Documents/R/specdata")
  getwd()
  ls()
  dir()
  
  pollutantmean <- function(directory, pollutant, id = 1:332) {
    file.names <- list.files(directory)
    file.numbers <- as.numeric(sub('\\.csv$','', file.names))
    selected.files <- na.omit(file.names[match(id, file.numbers)])
    selected.dfs <- lapply(file.path(directory,selected.files), read.csv)
    mean(c(sapply(selected.dfs, function(x) x[ ,pollutant])), na.rm=TRUE)
  }
  
  pollutantmean("specdata", "sulfate", 1:10)
  
  
  pollutantmean <- function(directory, pollutant, id = 1:332) {
    #set the path
    path = "C:/Users/Dell/Documents/R/specdata"
    
    #get the file List in that directory
    fileList = list.files(path)
    
    #extract the file names and store as numeric for comparison
    file.names = as.numeric(sub("\\.csv$","",fileList))
    
    #select files to be imported based on the user input or default
    selected.files = fileList[match(id,file.names)]
    
    #import data
    Data = lapply(file.path(path,selected.files),read.csv)
    
    #convert into data frame
    Data = do.call(rbind.data.frame,Data)
    
    #calculate mean
    mean(Data[,pollutant],na.rm=TRUE)
    
  }
  pollutantmean("specdata", "sulfate", 1:10)
  
  pollutantmean("specdata", "nitrate", 70:72)
  pollutantmean("specdata", "sulfate", 34)
  pollutantmean("specdata", "nitrate")
  
  
  
  
  #2nd Polutanmean function type
  pollutantmean <- function(directory, pollutant, id = 1:332) {
    files <- list.files(directory, full.names=TRUE)
    dat <- data.frame()
    
    for(i in id){
      dat <- rbind(dat, read.csv(files[i]))
    }
    
    mean_data <- mean(dat[,pollutant], na.rm = TRUE)
  }
  
  
  pollutantmean("specdata", "sulfate", 1:10)
  
  
  
  
  
  
  
  ##############
  etwd("C:/Users/Dell/Documents/R/specdata")
  complete <- function(directory, id = 1:332) {
    
    if(grep("specdata", directory) == 1) {
      directory <- ("./specdata/")
    }
    
    id_len <- length(id)
    complete_data <- rep(0, id_len)
    
    all_files <- as.character( list.files(directory) )
    file_paths <- paste(directory, all_files, sep="")
    j <- 1 
    for (i in id) {
      current_file <- read.csv(file_paths[i], header=T, sep=",")
      complete_data[j] <- sum(complete.cases(current_file))
      j <- j + 1
    }
    result <- data.frame(id = id, nobs = complete_data)
    return(result)
  } 
  
  complete("specdata", 30:25)
  
  
  ######
  
  complete <- function(directory, id = 1:332) {
    files <- list.files(directory, full.names = TRUE)
    monitor_data <- lapply(files[id], function(x) read.csv(x, header = TRUE))
    nobs <- sapply(monitor_data, function(x) sum(complete.cases(x)))
    data.frame('id' = id, 'nobs' = nobs)
  }
  
  specdata<- getwd()
  complete(specdata, 1)
  
  cc <- complete(specdata, c(6, 10, 20, 34, 100, 200, 310))
  print(cc$nobs)
  
  cc <- complete(specdata, 54)
  print(cc$nobs)
  
  set.seed(42)
  cc <- complete(specdata, 332:1)
  use <- sample(332, 10)
  print(cc[use, "nobs"])
  
  
  
  
  corr <- function(directory, threshold = 0) {
    ## 'directory' is a character vector of length 1 indicating
    ## the location of the CSV files
    
    ## 'threshold' is a numeric vector of length 1 indicating the
    ## number of completely observed observations (on all
    ## variables) required to compute the correlation between
    ## nitrate and sulfate; the default is 0
    
    ## Return a numeric vector of correlations
    
    # note: NULL, NA, NaN are all place holders only and cannot be compared using logical operators.
    # note: numeric(0) cannot be compared either, use length(numeric(0)) instead.
    # note: when coercing a data frame into matrix, consider it's data class/type.
    # note: for lists, pay attention to the difference between '[' &'[[' when subsetting!
    # note: to return a certain value, just type the variable name at the end in the function.
    # note: complete.cases() returns a logical vector.
    # note: lapply(x, FUN, ...), the '...' can pass in the variables following the function.
    
    files <- list.files(directory, full.names = TRUE)
    #     data <- lapply(files, function(x) read.csv(x, header = TRUE))
    data <- lapply(files, read.csv, header = TRUE)
    # Store all the data to the list 'data'
    valid_data <- lapply(data, function(x) x[complete.cases(x),])
    #     valid_data <- lapply(data, function(x) x[!is.na(x$Date) & !is.na(x$sulfate) & !is.na(x$nitrate) & !is.na(x$ID),])
    #     Store all complete cases in valid_data
    if (is.null(valid_data) == TRUE){
      numeric(0)
    }
    else {
      correlations <- numeric(0)
      # Initialize the data set that pass the threshold requirement
      for (i in seq_along(valid_data)){
        if (nrow(valid_data[[i]]) >= threshold){
          correlations <- c(correlations, cor(valid_data[[i]]$sulfate, valid_data[[i]]$nitrate))
        }
        
      }
      # Select the data frames which pass the threshold requirement
      correlations
    }
    
  }
  
  cr <- corr(specdata)                
  cr <- sort(cr)                
  set.seed(868)                
  out <- round(cr[sample(length(cr), 5)], 4)
  print(out)
  

  
  ##Background terms
  
  
  #Типы данных в R:
    # num(числовой)
    # char(символьный)
    # complex(комплексный) 
    # logical(логический)
    # integer (целочисленный)
    # double (вещественный)
    # raw (двоичные данные)
  
  # Длина - общее количество элементов объекта
  
  # Виды объектов
    # vector (вектор) – являются основополагающей струтурой данных языка R, пред-
      # ставляющей собой некоторое количество однотипных элементов непрерыв-
      # но расположенных в памяти
      # Например:
  x<- c(2,3,4,5) #- сам вектор, в который входит в данном случае 4 элемента
  length(x)  #- определяет длинну вектора
  #[1] 2 3 4 5
  # > length(x)
  #[1] 4
  
  # factor (фактор) – категорийная переменная
    # array (массив) – таблица с k измерениями
    # matrix (матрица) – частный случай массива с k = 2. У массива и
    #матрицы все элементы одного и того же типа.
    # Data.frame – таблица состоящая из нескольких векторов одинаковой
    # длины, но возможно различных типов. 
    # Ts – набор данных временного ряда, содержащий дополнительные
    # атрибуты, такие как: частота и дата.
  
  # Переменная с индексом – это переменная, имеющая одно и то же имя, 
  #но которая может иметь не единственное значение, а множество разных 
  #значений. Под одним именем переменной с индексом скрывается целый 
  #массив данных. Каждое отдельное значение этого массива отличается от 
  #остальных значений массива своим уникальным индексом.
  #Ex: Индексы в языках программирования обычно указывают в круглых 
  #скобках сразу после имени переменной, например, A(1), A(2), 
  #A(3), B(1), B(2), B(3) и т.д.
  
  #Что такое массив в программировании?
  #Переменные с индексами, независимо от количества индексов, 
  #называют массивами, это даже как-то проще и короче звучит.
  
  
  # 20.04.2017 Week 3. Loop function lapply

# APPLY FUNCTIONS
  #Lapply function - takes 3 args: (1) list - x, (2) a function (on f's name),
  #other args via its args. If x is not a list, it will be coereced to a 
  #list using as.list
  # It always returns a list
  #EX:
  x<- list(a=1:5, b=rnorm(10))
  x
  lapply(x,mean)
  $a
  [1] 3
  
  $b
  [1] 0.4247865
  
  x<-1:2
  lapply(x,runif, min=0,max=10) #runif generates random variables. The following function gives
  # random numbers of No1 and No2 (if x<- 1:5 then No1,No2,No3,No4,No5)
  [[1]]
  [1] 0.259125
  
  [[2]]
  [1] 5.270865 8.387076
  
  #lapply and friends make heavy use of anonymous functions (functions 
  #that do not have names )
  #EX:
  x<-list(a=matrix(1:4,2,2), b=matrix(1:6,3,2))
  x  
  
  $a
  [,1] [,2]
  [1,]    1    3
  [2,]    2    4
  
  $b
  [,1] [,2]
  [1,]    1    4
  [2,]    2    5
  [3,]    3    6
  
  #AN ANONYMOUS function for extracting the 1st column of each matrix
  lapply(x, function(elt) elt[,1]) #this function does not exists except the 
  #content of "lapply". Function fininished after lapply is done.
  
  
  #SAPPLY function
  # It simplify the resulp of lapplay if possible and gives the result as a
  # vector instead of list
  #EX:
  #If lapply gives
  x<-list(a=1:4, b=rnorm(10), c=rnorm(2), d=rnorm(12))
  lapply(x, mean)
  $a
  [1] 2.5
  
  $b
  [1] 0.08556237
  
  $c
  [1] -0.9654998
  
  $d
  [1] 0.1042083
  
  #then sapply gives:
  sapply(x, mean)
  a           b           c           d 
  2.50000000  0.08556237 -0.96549977  0.10420827 
  
  
  ##APPLY function
  str(apply)
  function (X, MARGIN, FUN, ...) 
  #X- array
  #Margin - integer vector indicating which margins should be retained
  # FUN - is function to be applied
  #Ex:
    x<-matrix(rnorm(200),20,10)  #20 - is 1st dimension and has 20 rows, 2nd 20colums
    apply(x,2,mean) # here is 2nd dimension - thus return of 20 rows' value
    apply(x, 1, sum)
  #For calcculating col sums&means there quik functions excist:
    #rowSums = apply(x,1,sum)
    #...
    #colMeans = apply(x,2, means)
    
  #Other way for APPLY function
   #Ex:
    x<-matrix(1:10,2,5, byrow = T) #byrow - распределяет значения по строкам
    x
    rownames(x)<-c("Jack", "Burry") #таким образом пишем названия к rows
    colnames(x)<-c("A","B","C","D","E")
    dim(x) # Функция dim() очень полезна. Она позволяет проверить размерность
    # (кол-во строк и стобцов)
    dim(x)
    [1] 2 5
    t(x) #меняет строки и столбцы между собой местами
    apply(x, 1,quantile,probs= c(0.24,0.75))
    # In this function there is a function called "quantile", which provides with 
    #the possibility to know the persentage value of a row (in prtcl case). In 
    # "probs" you determine the persentage 
    
              [,1] [,2]
    25%    3    4 #1st number is 25perc value out of sum of 1st row, 2nd is same of 2nd row
    75%    7    8
    
#Матрица (matrix) представляет собой двумерную совокупность числовых, 
#логических или текстовых величин. В свою очередь массив (array) – это 
#совокупность некоторых однотипных элементов, обладающая размерностью больше 
#двух. Подробнее: http://r-analytics.blogspot.fi/2011/07/r_10.html

  a<-array(c(2*2*8), c(2,2,10))
  apply(a,c(1,2),mean)  
  rowMeans(a, dims=2)

  
b<-array(c(1:4,7:20), c(5,4,2))
row.names(b)<-c("a","c","s","cc","vb")
colnames(b)<-c("a1","c1","s1","cc1")
b
apply(b,c(1,2), mean)
rowMeans(b, dims=2)
  
  # mapply function

  # Функция mapply() - используется в случаях, когда необходимо поэлементно 
  # применить какую-либо функцию одновременно к нескольким объектам (например, 
  # получить сумму первых элементов векторов, затему сумму вторых элементов 
  # векторов, и т.д.). Результат возвращается в виде вектора или массива другой 
  # размерности (см. примеры для sapply() выше). Буква "m" в названии mapply 
  # означает multivariate - "многомерный" (имеется в виду одновременное выполнение
  # вычислений над элементами нескольких объектов).

  #Ex: Example shows that both vectors return the same value, however mapply is to
  #write faster.
  list(rep(1,4),rep(2,3),rep(3,2), rep(4,1))
  mapply(rep, 1:4,4:1)
  [[1]]
  [1] 1 1 1 1
  
  [[2]]
  [1] 2 2 2
  
  [[3]]
  [1] 3 3
  
  [[4]]
  [1] 4
  
  #tapply function
  
  #Функция tapply() принадлежит к важному "apply-семейству" R-функций. 
  #Эти функции позволяют выполнять математические вычисления над определенными 
  #элементами таблиц данных, матриц, или массивов (например, быстро вычислять 
  #среднее значение для каждого столбца или строки таблицы, и т.п.).
  
  x<-c(rnorm(10), runif(10), rnorm(10,1))
  x
  f<-gl(3,10) #функция, генерирующая факторы в соответствии с кол-вом уровней. 
  #В данном примере f = значение, состоящее из 3 уровней с повторением каждого 
  #10 раз
  f
  [1] 1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2 2 2 3 3 3 3 3 3 3 3 3 3
  Levels: 1 2 3
  
  tapply(x,f,mean) 
  1          2          3 
  0.00693866 0.36625618 0.97636040
  
  #Пример проще и содержит описание
  
  y<-c(1.5,3.2,4,5,8,9)# Обычная переменная состоящая из 6 аргументов 
  length(y)
  z<-gl(2,3) # функция, генерирующая факторы в соответствии с кол-вом уровней. 
  #В данном примере z = значение, состоящее из 2 уровней с повторением каждого 
  #3 раза. 
  y;z
  tapply(y,z,mean) # Функция высчитывает среднее значение для каждого уровня
  1        2       # Для 1ого уровня ср.значение формула (1.5+3.2+4)/3 для 2ого (4+5)/2
  2.900000 7.333333 
  
  tapply(y,z,mean, simplify = FALSE) # При simplify=False возврат в виде list
  $`1`
  [1] 2.9
  
  $`2`
  [1] 7.333333
  
  
    tapply(y,z,range) - # range - высчитывает макс. и мин. значение для каждого 
     #уровня

  
  # split funtion
      # развбивает все по группам и всегда возвращает List. По сути tapply делает
      # тоже самое, что и split
      x<-c(rnorm(10), runif(10), rnorm(10,1))
      x
      f<-gl(3,10)
      g<-split(x,f)
      $`1`
      [1]  0.78785111  0.24443273 -0.10068114 -2.46445341 -0.07924978 -0.09109371
      [7] -0.95510558  0.42533180  0.38680311  0.60369935
      
      $`2`
      [1] 0.27186575 0.76190648 0.67877434 0.03861648 0.55832287 0.45124555 0.32234904
      [8] 0.22631977 0.52194750 0.78345272
      
      $`3`
      [1]  1.7309235  0.9951511  0.1180962  0.6199194  0.5092312  1.5723729  0.4687543
      [8]  1.6783034  1.8788395 -0.2480635
      
      # После группирование информации за счет функции split, можно использовать 
      # lapply или sapply... функции и тогда return будет упорядочен
      lapply(g,mean)
      $`1`
      [1] -0.1242466
      
      $`2`
      [1] 0.4614801
      
      $`3`
      [1] 0.9323528
      
      # Еще одно использование split. За счет функции в таблице ниже разобьем данные
      # в соответствии с каждым типом месяца
     library(datasets)
      head(airquality)
      Ozone Solar.R Wind Temp Month Day
      1    41     190  7.4   67     5   1
      2    36     118  8.0   72     5   2
      3    12     149 12.6   74     5   3
      4    18     313 11.5   62     5   4
      5    NA      NA 14.3   56     5   5
      6    28      NA 14.9   66     5   6
      
      s<-split(airquality, airquality$Month)
      lapply(s, function(x) colMeans(x[, c("Ozone","Solar.R", "Wind")], na.rm =))
      
      $`5`
      Ozone  Solar.R     Wind 
      NA       NA 11.62258 
      
      $`6`
      Ozone   Solar.R      Wind 
      NA 190.16667  10.26667 
      ...
      
      sapply (s, function(x) colMeans(x[, c("Ozone","Solar.R", "Wind")]))
      # упрощает вид вывода данных и выводит matrix вместо list
      
                    5         6          7        8        9
      Ozone         NA        NA         NA       NA       NA
      Solar.R       NA 190.16667 216.483871       NA 167.4333
      Wind    11.62258  10.26667   8.941935 8.793548  10.1800
      
      
      
      sapply (s, function(x) colMeans(x[, c("Ozone","Solar.R", "Wind")], na.rm = T))
      #Убираем NA values
      5         6          7          8         9
      Ozone    23.61538  29.44444  59.115385  59.961538  31.44828
      Solar.R 181.29630 190.16667 216.483871 171.857143 167.43333
      Wind     11.62258  10.26667   8.941935   8.793548  10.18000
      
      x<-rnorm(10)
      f1<- gl(2,5)
      f2<- gl(5,2)
      f1
      f2
      interaction(f1,f2)
  str(split(x, list(f1,f2)))    
  List of 10
  $ 1.1: num [1:6] 0.788 0.244 0.272 0.762 1.731 ...
  $ 2.1: num(0) 
  $ 1.2: num [1:6] -0.1007 -2.4645 0.6788 0.0386 0.1181 ...
  $ 2.2: num(0) 
  $ 1.3: num [1:3] -0.0792 0.5583 0.5092
  $ 2.3: num [1:3] -0.0911 0.4512 1.5724
  $ 1.4: num(0) 
  $ 2.4: num [1:6] -0.955 0.425 0.322 0.226 0.469 ...
  $ 1.5: num(0) 
  $ 2.5: num [1:6] 0.387 0.604 0.522 0.783 1.879 ...
  
  
  str(split(x, list(f1,f2), drop = T)) #drop убирает все векторы с 
  #пустыми значениями
  List of 6
  $ 1.1: num [1:6] 0.788 0.244 0.272 0.762 1.731 ...
  $ 1.2: num [1:6] -0.1007 -2.4645 0.6788 0.0386 0.1181 ...
  $ 1.3: num [1:3] -0.0792 0.5583 0.5092
  $ 2.3: num [1:3] -0.0911 0.4512 1.5724
  $ 2.4: num [1:6] -0.955 0.425 0.322 0.226 0.469 ...
  $ 2.5: num [1:6] 0.387 0.604 0.522 0.783 1.879 ...
  
  
  #Debugging Functions
    # Traceback - says in which line there is a fault. Traceback 
      #gives the most recent erro, thus there is a need to call it immediatly after 
      # erro ocurs.
      #Ex:
      mean(irn)
      #Error in mean(irn) : object 'irn' not found
      traceback()
      1: mean(irn)
    
    #Debug - first it prints the whole function body code
      debug(lm)
      lm(x~y)
      #ret.x <- x
      #ret.y <- y
      #cl <- match.call()
      ...
      #if (!qr) 
      #  z$qr <- NULL
      #z
      #}
      #Browse[2]> Q
      #for checking debug, in browser there is a need to write "n"
    #Recover
      
      
# WEEK 4 
  #"Str" function
    #Данная функция служит для подачи краткой и полезной информации об объекте 
    #Так же есть еще пару функций которые дают краткую информацию об объекте,
    #немного в ином формате:
      # - Head()
      # - str ()
      # - summary()
      # Примеры:
      
      > head(airquality)
      Ozone Solar.R Wind Temp Month Day
      1    41     190  7.4   67     5   1
      2    36     118  8.0   72     5   2
      3    12     149 12.6   74     5   3
      ...
      
    summary(airquality)
    > summary(airquality)
    Ozone           Solar.R           Wind             Temp           Month      
    Min.   :  1.00   Min.   :  7.0   Min.   : 1.700   Min.   :56.00   Min.   :5.000  
    1st Qu.: 18.00   1st Qu.:115.8   1st Qu.: 7.400   1st Qu.:72.00   1st Qu.:6.000  
    Median : 31.50   Median :205.0   Median : 9.700   Median :79.00   Median :7.000  
     ...
     
     str(airquality)
     'data.frame':	153 obs. of  6 variables:
       $ Ozone  : int  41 36 12 18 NA 28 23 19 8 NA ...
     $ Solar.R: int  190 118 149 313 NA NA 299 99 19 194 ...
     $ Wind   : num  7.4 8 12.6 11.5 14.3 14.9 8.6 13.8 20.1 8.6 ...
     ...
     
     # в данном примере мы разбиваем предыдущую таблицу по месяцам и снова
     #вызываем srt. Теперь инф. выводится по каждой группе. 
     
     s<-split(airquality, airquality$Month)
     str(s)
     
     List of 5
     $ 5:'data.frame':	31 obs. of  6 variables:
       ..$ Ozone  : int [1:31] 41 36 12 18 NA 28 23 19 8 NA ...
     ..$ Solar.R: int [1:31] 190 118 149 313 NA NA 299 99 19 194 ...
     ..$ Wind   : num [1:31] 7.4 8 12.6 11.5 14.3 14.9 8.6 13.8 20.1 8.6 ...
     ..$ Temp   : int [1:31] 67 72 74 62 56 66 65 59 61 69 ...
     ..$ Month  : int [1:31] 5 5 5 5 5 5 5 5 5 5 ...
     ..$ Day    : int [1:31] 1 2 3 4 5 6 7 8 9 10 ...
     $ 6:'data.frame':	30 obs. of  6 variables:
       ..$ Ozone  : int [1:30] NA NA NA NA NA NA 29 NA 71 39 ...
     ..$ Solar.R: int [1:30] 286 287 242 186 220 264 127 273 291 323 ...
     ..$ Wind   : num [1:30] 8.6 9.7 16.1 9.2 8.6 14.3 9.7 6.9 13.8 11.5 ...
     ..$ Temp   : int [1:30] 78 74 67 84 85 79 82 87 90 87 ...
     ...
     
     
    #Simulation
     # Функции для распределение вероятностей в R
     
     # - rnorm
     # служит для случайной генерации совокупностей нормально распределенных 
     # чисел
     # - dnorm
     #  позволяет рассчитать значение функции плотности вероятности для 
     #заданного значения
     # - pnorm
     #Кумулятивная функция распределения (или просто "функция распределения") 
     #описывает вероятность того, что вещественнозначная случайная переменная 
     #X примет какое-либо значение, не превышающее либо равное x
     # - rpois
     #Распределе??ние Пуассо??на — вероятностное распределени дискретнго  типа,
     #моделирует случайную величину, представляющую собой число событий, 
     #произошедших за фиксированное время, при условии, что данные события 
     #происходят с некоторой фиксированной средней интенсивностью и независимо
     #друг от друга.
     rpois(-1)
     
     # - d (от "density", плотность): функции плотности вероятности 
     # ("функция распределения масс" для дискретных величин);
     # - p (от "probability", вероятность): кумулятивные функции распределения 
     # вероятностей;
     # - q (от "quantile", квантиль): функции для нахождения квантилей того или 
     #иного распределения;
     # - r (от "random", случайный): функции для генерации случайных чисел в 
     #соответствии с параметрами того или иного закона распределения вероятностей.
     
     #set.seed - (от set - задать, установить, и seed - начальное число)
     #исользуется для получения идентичных чисел при использовании функций 
     # вероятного распределения
     
     set.seed(1.5)
     rnorm(1:3)
     
     #> set.seed(1.5)
     #>      rnorm(1:3)
     #[1] -0.6264538  0.1836433 -0.8356286
     #> set.seed(1.5)
     #>      rnorm(1:3)
     #[1] -0.6264538  0.1836433 -0.8356286
     
     set.seed(10)
     x<- rnorm (100,2,5)
     e<-rpois(10,1)
     y<- 0.5 +3*x+e
     summary(y)
     
     plot(x,y)
    
    #sample - извлекает возможные числа из предложенных. Колличество цифр зависит
    # от заданного значения
     
        

  #Profiler 
  #позволяет понять как ведет себя весь код или его часть
    #System.time
       #Позволяет посмотреть сколько времени требуется на обработку кода
        system.time(readLines("https://ru.wikipedia.org/wiki/%D0%A6%D0%B5%D0%BD%D1%82%D1%80%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%B9_%D0%BF%D1%80%D0%BE%D1%86%D0%B5%D1%81%D1%81%D0%BE%D1%80"))
     #Rprof
        

#12
#Looking at data
ls()
> ls()
[1] "a"           "anorex.1"    "anorexia"    "b"           "buttoms"    
[6] "cachemean"   "clotting"    "cls_list"    "cls_vect"    "cnames"     
[11] "counts"      "cube"        "cyl4"        "cyl8"        "d.AD"       
[16] "datestring"  "e"           "example"     "f"           "f1"         
....

class(plants)
[1] "data.frame"

dim(plants)
  [1] 5166   10 #number of rows and columns
nrow(plants)
ncol(plants)

object.size(plants)
  644232 bytes
names(plants)
  [1] "Scientific_Name"      "Duration"             "Active_Growth_Period"
  [4] "Foliage_Color"        "pH_Min"               "pH_Max"              
  [7] "Precip_Min"           "Precip_Max"           "Shade_Tolerance"     
  [10] "Temp_Min_F"  

head(plants) # shows the first rows
tail(plants,15) #shows the last rows (in that case last 15 rows)

summary(plants)
table(plants$Active_Growth_Period)

  Fall, Winter and Spring                  Spring         Spring and Fall 
  15                     144                      10 
  Spring and Summer    Spring, Summer, Fall                  Summer 
  447                      95                      92 
  Summer and Fall              Year Round 
  24                       5 
  
  
  str(plants)
  
  
  setwd("C:/Users/Dell/Documents/R")
  getwd()
 dir()
 head("hospital-data.csv")  
 
 str(hosda)
  head(caremes)
  hosda["SC", "heart attack"]
  head(caremes("SC", "heart attack"),1)
  
  
#Plot графика
  plot(x = cars$dist, y = cars$dspeed)
  plot(cars) # создает график определенной таблицы
  plot(x = cars$speed, y = cars$dist) # можно задать какая переменная x, а какая y
  plot(x = cars$speed, y = cars$dist, xlab = "Speed") #x(y)lab - название 
  #переменных на графике
  plot(x = cars$speed, y = cars$dist,xlab = "Speed", ylab = "Stopping Distance")
  plot(x = cars$speed, y = cars$dist,xlab = "Speed", ylab = "Stopping Distance"
       , main = "My Plot") # main аргумент загаловка графика
  plot(cars, sub = "My Plot Subtitle")
  ?par.
  plot(cars, col.lab = "red") #меняет цвет названий
  plot(cars, col = 2) # изменяте цвет графика (цифра - название цвета,
  # можно писать латиницей (нап: "red))
  ?par() #Дает информацию об общепринятых аргументах в функция по графике.
  plot(cars, xlim = c(10, 15)) # ограничивает выдачу колонки (в данном случае в 
  # диапозоне от 10 до 15)
  (?points) # так же справка о визуальных эффектах
  plot(cars, pch = 2) # меняет форму кружочков на треугольники
  
  
  
  data(mtcars)
  play()
  head(mtcars)
  str(mtcars)
  summary(mtcars)
  dim(mtcars)
  plot(mtcars)
  nxt()
  
  
boxplot(mtcars, mpg ~ cyl)
boxplot(formula = mpg ~ cyl, data = mtcars)  
hist(mtcars$mpg) # удобно для отображения одной переменной в таблице 
(http://www.ling.upenn.edu/~joseff/rstudy/week4.html) # много чего о графике


#Assignment 3:Quiz
dir()
getwd()
setwd("C:/Users/Dell/Documents/R/assigment week 4/")
getwd()
str(outcome_of_care_measures)
rankhospital("WA", "heart attack", 7)
 outcome <- read.csv("outcome-of-care-measures.csv", colClasses = "character")
 head(outcome)
ncol(outcome)
dim(outcome)
names(outcome) # предоставляетт именя колонок в таблице

outcome[, 11] <- as.numeric(outcome[, 11])

hist(outcome[, 11])

#TX heart attack min

best<-function(state){
out1<-outcome_of_care_measures[,c(2,7,11,17,23)]
names(out1)
out1$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`<-as.numeric(as.character(
  out1$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`)) 

out2<-out1[which(out1$State == state),]

out3<-out2[which(out2$`Hospital 30-Day Death (Mortality) Rates from Heart Attack` == 
             min(out2$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`, na.rm = T)),]
return(out3$`Hospital Name`)}

best("TX")
best("MD")

names(out1)



########
g<-data.frame(0:10,10:20,20:30,30:40,40:50)
colnames(g)<-c("a","b","c","d","e")
g
class(g)

g[which(g$a>3 & g$b > 15 & g$c == max(g$c) ),]



########





best<-function(state1, outcome2){
  out1<-outcome_of_care_measures[,c(2,7,11,17,23)]
  names(out1)
  out1$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`<-as.numeric(as.character(
    out1$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`))
  out1$`Hospital 30-Day Death (Mortality) Rates from Heart Failure`<-as.numeric(as.character(
    out1$`Hospital 30-Day Death (Mortality) Rates from Heart Failure`))
  out1$`Hospital 30-Day Death (Mortality) Rates from Pneumonia`<-as.numeric(as.character(
    out1$`Hospital 30-Day Death (Mortality) Rates from Pneumonia`))
if(outcome2 == "heart attack"){
  
out2<-out1[which(out1$State== "TX" & 
    out1$`Hospital 30-Day Death (Mortality) Rates from Heart Attack` 
    == min( out1$ `Hospital 30-Day Death (Mortality) Rates from Heart Attack`, 
    na.rm = T))]
else
print(out2)

}}

##else if(outcome2 == "heart failure"){
#   out2<-out1[which(out1$State==state1 & 
#    out1$`Hospital 30-Day Death (Mortality) Rates from Heart Failure` 
#    == min( out1$`Hospital 30-Day Death (Mortality) Rates from Heart Failure`, 
#                            na.rm = T))]
#   return(out2$`Hospital Name`)
#} else if (outcome2 == "pneumonia"){
#  out2<-out1[which(out1$State==state1 & 
#          out1$`Hospital 30-Day Death (Mortality) Rates from Pneumonia`
#          == min( out1$`Hospital 30-Day Death (Mortality) Rates from Pneumonia`, 
#                na.rm = T))]
#  return(out2$`Hospital Name`)
#}}

best("TX", "heart attack")









setwd("C:/Users/Dell/Documents/R/assigment week 4")



######
Best4<-function(state){  
  out1<-outcome_of_care_measures[,c(2,7,11,17,23)]
  out1$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`<-as.numeric(as.character(
    out1$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`)) 
  
  out2<-out1[which(out1$State == state & out1$`Hospital 30-Day Death (Mortality) Rates from Heart Attack` == 
                     min(out1$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`, na.rm = T)),]
  
  return(out2$`Hospital Name`)}
Best4("TX")

best5<-function(state){
  out1<-outcome_of_care_measures[,c(2,7,11,17,23)]
  names(out1)
  out1$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`<-as.numeric(as.character(
    out1$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`)) 
  
  out2<-out1[which(out1$State == state),]
  
  out3<-out2[which(out2$`Hospital 30-Day Death (Mortality) Rates from Heart Attack` == 
                     min(out2$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`, na.rm = T)),]
  good<- complete.cases(out3)
  return(out3[good,][,"Hospital Name"])}
best5("TX")

####
best7<-function(state, outcome){
  out1<-outcome_of_care_measures[,c(2,7,11,17,23)]
 if(outcome == "heart attack"){
    out1$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`<-as.numeric(as.character(
    out1$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`)) 
  
  out2<-out1[which(out1$State == state),]
  
  out3<-out2[which(out2$`Hospital 30-Day Death (Mortality) Rates from Heart Attack` == 
                     min(out2$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`, na.rm = T)),]
  return(out3$`Hospital Name`)
 } else if (outcome == "heart failure"){
   out1$`Hospital 30-Day Death (Mortality) Rates from Heart Failure`<- as.numeric(as.character(
     out1$`Hospital 30-Day Death (Mortality) Rates from Heart Failure`)) 
   
   out2<-out1[which(out1$State == state),]
   
   out3<-out2[which(out2$`Hospital 30-Day Death (Mortality) Rates from Heart Failure` == 
                      min(out2$`Hospital 30-Day Death (Mortality) Rates from Heart Failure`, na.rm = T)),]
   return(out3$`Hospital Name`)
 } else if (outcome ==  "pneumonia"){
   out1$`Hospital 30-Day Death (Mortality) Rates from Pneumonia`<- as.numeric(as.character(
     out1$`Hospital 30-Day Death (Mortality) Rates from Pneumonia`)) 
   
   out2<-out1[which(out1$State == state),]
   
   out3<-out2[which(out2$`Hospital 30-Day Death (Mortality) Rates from Pneumonia` == 
                      min(out2$`Hospital 30-Day Death (Mortality) Rates from Pneumonia`, na.rm = T)),]
   return(out3$`Hospital Name`)
 }else if ( state %in% out1$State ==FALSE){stop("Invalid state")
 }else if (outcome  == FALSE){
      stop("invalid outcome")
    }

  }

best7("AK", "pneumonia")

#### 3 Rankhospitals
# tools to use with example
t<-data.frame(rnorm(0:20),rnorm(20:0))
colnames(t)<-c("x","y")
t["rank"]<- rank(t$y) # creating new column with value of "rank" func.
t[with(t,order(rank, decreasing = T)),] #filter all data frame by "rank" column


rankhospital<-function(state, outcome, num){
  out1<-outcome_of_care_measures[,c(2,7,11,17,23)]
  if(outcome == "heart attack"){
    out1$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`<-as.numeric(as.character(
      out1$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`)) 
    
    out2<-out1[which(out1$State == "state"),]
    
    out3<-out2[which(out2$`Hospital 30-Day Death (Mortality) Rates from Heart Attack` == 
                       min(out2$`Hospital 30-Day Death (Mortality) Rates from Heart Attack`, na.rm = T)),]
   } else if (outcome == "heart failure"){
    out1$`Hospital 30-Day Death (Mortality) Rates from Heart Failure`<- as.numeric(as.character(
      out1$`Hospital 30-Day Death (Mortality) Rates from Heart Failure`)) 
    
    out2<-out1[which(out1$State == "state"),]
    
    out3<-out2[which(out2$`Hospital 30-Day Death (Mortality) Rates from Heart Failure` == 
                       min(out2$`Hospital 30-Day Death (Mortality) Rates from Heart Failure`, na.rm = T)),]
  } else if (outcome ==  "pneumonia"){
    out1$`Hospital 30-Day Death (Mortality) Rates from Pneumonia`<- as.numeric(as.character(
      out1$`Hospital 30-Day Death (Mortality) Rates from Pneumonia`)) 
    
    out2<-out1[which(out1$State == "state"),]
    
    out3<-out2[which(out2$`Hospital 30-Day Death (Mortality) Rates from Pneumonia` == 
                       min(out2$`Hospital 30-Day Death (Mortality) Rates from Pneumonia`, na.rm = T)),]
  }else if ( state %in% out1$State ==FALSE){stop("Invalid state")
  }else if (outcome  == FALSE){
    stop("invalid outcome")
  } 
      out3["rank"]<-rank(out3$outcome)
    num1<-out3[with(out3,order(out3$rank, decreasing = F))]
        if (num == "worst"){
      num2<-num1[which(num1$rank == max(num1$rank)),]
      return(num2$`Hospital Name`)
    }else if(num == "worst"){
      num2<-num1[which(num1$rank == min(num1$rank)),]
      return(num2$`Hospital Name`)
          }
      
  }  

rankhospital("NC", "heart attack", "worst")



#####  NOT MY SOLUTION BUT WORKS
rankhospital <- function(outcome, rank = "best"){
  ## Read outcome data
  data <- read.csv("outcome-of-care-measures.csv", colClasses = "character")
  fd   <- as.data.frame(cbind(data[, 2],  # hospital
                              data[, 7],  # state
                              data[, 11],  # heart attack
                              data[, 17],  # heart failure
                              data[, 23]), # pneumonia
                        stringsAsFactors = FALSE)
  colnames(fd) <- c("hospital", "state", "heart attack", "heart failure", "pneumonia")
  
  ## Check that state and outcome are valid
  if (!state %in% fd[, "state"]) {
    stop('invalid state')
  } else if (!outcome %in% c("heart attack", "heart failure", "pneumonia")){
    stop('invalid outcome')
  } else if (is.numeric(rank)) {
    si <- which(fd[, "state"] == state)
    ts <- fd[si, ]                     # extracting dataframe for the called state
    ts[, eval(outcome)] <- as.numeric(ts[, eval(outcome)])
    ts <- ts[order(ts[, eval(outcome)], ts[, "hospital"]), ]
    output <- ts[, "hospital"][rank]
  } else if (!is.numeric(rank)){
    if (rank == "best") {
      output <- best(state, outcome)
    } else if (rank == "worst") {
      si <- which(fd[, "state"] == state)
      ts <- fd[si, ]    
      ts[, eval(outcome)] <- as.numeric(ts[, eval(outcome)])
      ts <- ts[order(ts[, eval(outcome)], ts[, "hospital"], decreasing = TRUE), ]
      output <- ts[, "hospital"][1]
    } else {
      stop('invalid rank')
    }
  }
  return(output)
}

rankhospital("NY", "heart attack", 7)




rankall <- function(outcome, num = "best"){
  ## Read outcome data
  data <- read.csv("outcome-of-care-measures.csv", colClasses = "character")
  fd   <- as.data.frame(cbind(data[, 2],  # hospital
                              data[, 7],  # state
                              data[, 11],  # heart attack
                              data[, 17],  # heart failure
                              data[, 23]), # pneumonia
                        stringsAsFactors = FALSE)
  colnames(fd) <- c("hospital", "state", "heart attack", "heart failure", "pneumonia")
  fd[, eval(outcome)] <- as.numeric(fd[, eval(outcome)])
  
  ## Check that state and outcome are valid
  
  if (!outcome %in% c("heart attack", "heart failure", "pneumonia")){
    stop('invalid outcome')
  } else if (is.numeric(num)) {
    by_state <- with(fd, split(fd, state))
    ordered  <- list()
    for (i in seq_along(by_state)){
      by_state[[i]] <- by_state[[i]][order(by_state[[i]][, eval(outcome)], 
                                           by_state[[i]][, "hospital"]), ]
      ordered[[i]]  <- c(by_state[[i]][num, "hospital"], by_state[[i]][, "state"][1])
    }
    result <- do.call(rbind, ordered)
    output <- as.data.frame(result, row.names = result[, 2], stringsAsFactors = FALSE)
    names(output) <- c("hospital", "state")
  } else if (!is.numeric(num)) {
    if (num == "best") {
      by_state <- with(fd, split(fd, state))
      ordered  <- list()
      for (i in seq_along(by_state)){
        by_state[[i]] <- by_state[[i]][order(by_state[[i]][, eval(outcome)], 
                                             by_state[[i]][, "hospital"]), ]
        ordered[[i]]  <- c(by_state[[i]][1, c("hospital", "state")])
      }
      result <- do.call(rbind, ordered)
      output <- as.data.frame(result, stringsAsFactors = FALSE)
      rownames(output) <- output[, 2]
    } else if (num == "worst") {
      by_state <- with(fd, split(fd, state))
      ordered  <- list()
      for (i in seq_along(by_state)){
        by_state[[i]] <- by_state[[i]][order(by_state[[i]][, eval(outcome)], 
                                             by_state[[i]][, "hospital"], 
                                             decreasing = TRUE), ]
        ordered[[i]]  <- c(by_state[[i]][1, c("hospital", "state")])
      }
      result <- do.call(rbind, ordered)
      output <- as.data.frame(result, stringsAsFactors = FALSE)
      rownames(output) <- output[, 2]
    } else {
      stop('invalid num')
    }
  }
  return(output)
}


r <- rankall("heart attack", 4)
as.character(subset(r, state == "HI")$hospital)

r <- rankall("heart failure", 10)
as.character(subset(r, state == "NV")$hospital)

# Collecting and cleaning the data
  #Downloading files from the Internet
  getwd()
  setwd("R")
  getwd()
    #Creating new directory by function
    if(!file.exists("data")){
      dir.create("data")}
  getwd()
dir()  
setwd("R/data/")
    #DOWNLOAD process frow web
    urlfile<-"https://data.baltimorecity.gov/api/views/dz54-2aru/rows.csv?accessType=DOWNLOAD"
    download.file(urlfile, destfile = "C:/Users/Dell/Documents/R/data/cameras.csv", method = "wininet")
    

    date()# give info about when file was downloaded
    [1] "Thu May 11 19:28:24 2017"
    
    #READING FILES
    cameraData<-read.table("C:/Users/Dell/Documents/R/data/cameras.csv", sep=",", header = TRUE)
    
    
    setwd("C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/data/")
dir()
f<-read.csv(file = "cameras.csv")

urlfile2<-"https://data.baltimorecity.gov/api/views/dz54-2aru/rows.csv?accessType=DOWNLOAD"
download.file(urlfile2, destfile = "C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/data/cameras.xlsx")
destfile<- "C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/data/cameras.xlsx"
dir()

head(read.table(file = "cameras.xlsx", sep = ","), 3)
r
install.packages("readxl")
library("readxl")
date()
read_xlsx(destfile, 
          sheet=1, col_names = T)
dir()
install.packages("XLConnect")
library("XLConnect")
#XML files
## Типы тэгов в XML файлах:
## начальный тэг <section>
## конечный тэг </section>
## пустой тэг <line break/>
install.packages("XML")
library("XML")




library("XML")
install.packages("RCurl")
library("bitops")
library("RCurl")
curlVersion()$features
curlVersion()$protocol
# Открытие xml файла в R
fileurl<- getURL("https://www.w3schools.com/xml/simple.xml", ssl.verifypeer = FALSE)
doc<-xmlTreeParse(fileurl, useInternal=  TRUE)
rootNode<- xmlRoot(doc)
xmlName(rootNode)
  #[1] "breakfast_menu"
names(rootNode)
  #food   food   food   food   food 
  #"food" "food" "food" "food" "food" 
rootNode[[2]] #открытие куска документа
  #<food>
   # <name>Strawberry Belgian Waffles</name>
    #<price>$7.95</price>
    #<description>Light Belgian waffles covered with strawberries and whipped cream</description>
    #<calories>900</calories>
    #</food> 
rootNode[[2]][[2]] #выдает информацию по конкретному кускуб конкретную строку
  #<price>$7.95</price> 
xmlSApply(rootNode[[1]], xmlValue) # возвращает значение по каждой части. Можно так же указать 
# номер части при желании.
       # name 
       # "Belgian Waffles" 
       # price 
        #"$5.95" 
        #description 
        #"Two of our famous Belgian Waffles with plenty of real maple syrup" 
        #calories 
        #"650"

xpathSApply(rootNode,"//name", xmlValue) #получение информации по каждой части по конкретному имени
   #[1] "Belgian Waffles"             "Strawberry Belgian Waffles"  "Berry-Berry Belgian Waffles"
   #[4] "French Toast"                "Homestyle Breakfast"        
xpathSApply(rootNode,"//price", xmlValue)
#[1] "$5.95" "$7.95" "$8.95" "$4.50" "$6.95"

#Более сложный случай

fileurl<- "http://www.espn.com/nfl/team/_/name/bal/baltimore-ravens"
doc<- htmlTreeParse(fileurl, useInternal=TRUE)
scores<- xpathSApply(doc, "//li[@class='score']", xmlValue)
teams<- xpathSApply(doc, "//li[@class='sports menu-nba']", xmlValue)

teams; scores #не работатет в связи с изменением дизайна сайта - должно быть дополнено

install.packages("jsonlite")
library("jsonlite")
jsondata<-fromJSON("https://api.github.com/users/jtleek/repos")
names(jsondata)
names(jsondata$owner) # дает названия переменных в конкретной подгруппе
jsondata$owner$id # дает значение по конкретному названию подподгруппы

head(iris)
summary(iris)
myjson<- toJSON(iris, pretty = T)# функция перевод файл в формат JSON, а "pretty" вид вывода информации

iris2<-fromJSON(myjson)# перевовид файл обратно в формат dtata frame из JSON
head(iris2)

# data.table функционал
library("data.table")

DF<- data.frame(x=rnorm(9), y=rep(c("a","b","c"), each=3),z=rnorm(9) )
head(DF,3)

DT<- data.table(x=rnorm(9), y=rep(c("a","b","c"), each=3),z=rnorm(9) )
head(DT,3)
tables() # функция дает информацию по data.table
    #   NAME NROW NCOL MB COLS  KEY
    #[1,] DT      9    3  1 x,y,z    
    #Total: 1MB
DT[2,]
    #x y          z
    #1: 0.4726166 a -0.6669887
DT[c(2,3,5),1]
    #1: 0.4726166
    #2: 1.0235661
    #3: 0.9789739
DT[,list(mean(x),sum(z))]
    #V1        V2
    #1: -0.01523741 -1.360256
DT[,table(y)]
    #y
    #a b c 
    #3 3 3 
DT[,w:=z*2] #добавление новой колонки
DT[,m:={tmp=x+z;log2(tmp+5)}]# добавление новой колонки при этом с новой колонкой производится 2 операции последовательно
DT[,xtrue:=x>0]
DT

set.seed(123)
DT2<- data.table(x = sample(letters[1:4],20, T))
DT2[,.N, by=x] # считает количество каждого символа по колонке x
    #x N
    #1: c 5
    #2: d 7
    #3: b 7
    #4: a 1


DT3<-data.table(x = sample(letters[1:4],20, T), y= rnorm(20))
setkey(DT3,x) # после операции, возвращает значение, которое введено ниже
DT3['a']
    #x           y
    #1: a  0.32895045
    #2: a  1.88677324
    #3: a  0.04948785
    #4: a -1.25008210
    #5: a  1.75288692
  ## соединение таблиц Join
  DT5<- data.table(x = c('a','b','c','dd'), y= 1:4)
  DT6<- data.table(x = c('a','b','c2','dd3'), z= 6:9)
  setkey(DT5,x); setkey(DT6, x)
  merge(DT5,DT6)
      #x y z
      #1: a 1 6
      #2: b 2 7
  
  #practical-r-exercises-in-swirl-part-1
  library(swirl)
  install_from_swirl("Getting and Cleaning Data")
swirl()  
k

#Quiz 1
#Q1
fileurlq1<-"https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv"
download.file(fileurlq1,"C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/UScs.csv")
USd<- read.csv("UScs.csv")
dir()
setwd("C:/Users/Dell/Documents/R/Course 3 cleaning and getting data")
head(USd)
names(USd)
colnames(USd)
usddt<-data.table(USd)
setkey(usddt,"VAL")
usddt['24']
usddt$VAL
bad<- is.na(usddt$VAL)
x<-usddt$FES
Priceusddt<-data.table(x)
xx<-Priceusddt[,.N,by=x]
xx
x

#Q3
fileurlq3<-"https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FDATA.gov_NGAP.xlsx"
download(fileurlq3,"C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/Natural Gas Aquisition Program.xlsx", mode = "wb")
dat<-read.xlsx("C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/Natural Gas Aquisition Program.xlsx", sheetIndex =  1, rowIndex = (18:23), colIndex= (7:15))
sum(dat$Zip*dat$Ext,na.rm=T)

#Q4
library (RCurl)
library (XML)
curlVersion()$features
curlVersion()$protocol

urlBalt<- ("https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Frestaurants.xml")
download.file(urlBalt, "C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/Baltimore restaurants.xml", mode = "wb")
BR<-"C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/Baltimore restaurants.xml"
Balres<-xmlTreeParse(BR, useInternalNodes = T)
balroot<-xmlRoot(Balres)
names(balroot)
balroot[[1]]
bdt<-data.table(x = xpathSApply(balroot,"//zipcode",xmlValue))
bdt2<-bdt[,.N,by=x]
setkey(bdt2,x)
bdt2['21231']

#Q5
USurl<-"https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06pid.csv"
download.file(USurl,"C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/The American Community Survey.csv", mode = "wb")
USsurvey<-"C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/The American Community Survey.csv"
DT<- fread(input=USsurvey, sep=",")
dim(DT)

system.time(DT[,mean(pwgtp15),by=SEX])
system.time(mean(DT[DT$SEX==1,]$pwgtp15))+system.time(mean(DT[DT$SEX==2,]$pwgtp15))
system.time(sapply(split(DT$pwgtp15,DT$SEX),mean))
system.time(mean(DT$pwgtp15,by=DT$SEX))
system.time(tapply(DT$pwgtp15,DT$SEX,mean))
system.time(rowMeans(DT)[DT$SEX==1])+system.time(rowMeans(DT)[DT$SEX==2])



#Week 2 In data cleaning
  ##Reading from Mysql
    ###Installing MySQL
      R.home()
      setwd("C:/PROGRA~1/R/R-33~1.3/etc")
      getwd()
      dir()
      file.create("Renviron.site")
      cat("Renviron.site", fill = T, labels = "MYSQL_HOME=C:/PROGRA~1/MySQL/MYSQLS~1.0/")
      
      install.packages('RMySQL',type='source')
      library('DBI')
      library('RMySQL')
      install.packages("dbConnect")
      library(gWidgets)
      library(dbConnect)
      install.packages("gWidgets")
                  install.packages("DBI")
    ###Connecting and listing databases
      ucscDb <- dbConnect(MySQL(), user="genome",
                          host="genome-mysql.cse.ucsc.edu") 
                    #dbConnect - соединается с БД
                    #MySQL - БД с которой нужно соеденится
                    #user и host место расположение сервера и его логин
      result <- dbGetQuery(ucscDb,"show databases;")
                    #dbGetQuery - функция получение ответа на запроса к БД
                    #"show databases;" это команда не R, а Mysql, которая отправляется
                    #через функцию dbGetQuery
      dbDisconnect(ucscDb) # После отправки запроса нужно разъеденить соединение с БД
      head(result)
      
      #Data are structured in databases, and then the databases, within 
      #each database, there's a series of tables. And then within the 
      #tables, there a series of fields, which called "records"
      
      #So remember, on a server, there might be multiple databases 
      #and within the database, they'll be multiple tables. Each 
      #table corresponding to what you might think of as a data frame.
      
      ucscDb <- dbConnect(MySQL(), user="genome", db = "hg19",
                          host="genome-mysql.cse.ucsc.edu") 
      result <- dbGetQuery(ucscDb,"show databases;")
      dbDisconnect(ucscDb)
      allTables<- dbListTables(hg19)
      length(allTables)
      
      #Does not work, will be updated latter. Link on Q: https://www.coursera.org/learn/data-cleaning/discussions/weeks/2/threads/KwVXhTsdEeewQg63RcQI7A
      
      dbListFields(hg19, "affyU133Plus2") # gives the names of columns
      dbGetQuery(hg19, "select count(*) from affyU133Plus2")# function counts all recoreds (rows) in a table
      
      affyData<- dbReadTable(hg19,"affyU133Plus2" ) #Gets out particular table from particular Db
      head(affyData)
      
      
      query<- dbSendQuery(hg19, "select * from affyU133Plus2 
                          where misMatches between 1 and 3") # subseting
                          # db. selecting all records where mismatch
                          #is 1 and 3 in part. table
      affy<- fetch(query); quantile(affy$misMatches)#fetch - kind of print func
      
      affyMisSmall<- fetch(query, n=10); dbClearResult(query)# in this "fetch" there is
                          #n=10 - show only first 10 records. dbClearResult - stoping and closing
                          #query.
      dbDisconnect(hg19)#closing the connection
  #Reading from HDF5
      #www.hdfgroup.org
      # Installing HDF5
      source("http://bioconductor.org/biocLite.R")
      biocLite("rhdf5")
      library("rhdf5")
      library("stringi")
      #Creating hdf5 file through R
      created = h5createFile("example.h5") #func creating a file
      created
      created = h5createGroup("example.h5", "foo") #creates a group in previously created file
      created = h5createGroup("example.h5", "baa")
      created = h5createGroup("example.h5", "foo/foobaa") #creates a subgroup in a group
      h5ls("example.h5")
      #  group   name     otype dclass dim
      #0     /    baa H5I_GROUP           
      #1     /    foo H5I_GROUP           
      #2  /foo foobaa H5I_GROUP 
      
      A = matrix(1:10,nr=5,nc=2)
      h5write(A,"example.h5", "foo/A")
      B = array (seq(0.1,2.0,by=0.1), dim=c(5,2,2))
      attr(B, "scale")<-"liter"
      h5write(B,"example.h5","foo/foobaa/B")
      h5ls("example.h5")
        #        group   name       otype  dclass       dim
        #0           /    baa   H5I_GROUP                  
        #1           /    foo   H5I_GROUP                  
        #2        /foo      A H5I_DATASET INTEGER     5 x 2
        #3        /foo foobaa   H5I_GROUP                  
        #4 /foo/foobaa      B H5I_DATASET   FLOAT 5 x 2 x 2
            #small fallback about attributes
            # атрибу??т (переменная-член, data member, class field, instance
            #variable) в объектно-ориентированном программировании — 
            #переменная, связанная с классом или объектом. Все данные 
            #объекта хранятся в его полях. Доступ к полям осуществляется 
            #по их имени. Обычно тип данных каждого поля задаётся в описании 
            #класса, членом которого является поле.
                    Пример
                    library(data.table)
                    aa<-data.table(a=rnorm(26,mean=10),b=LETTERS,c=1:26)
                    attr(aa, "a")<-"26 numbers" # добавление атрибута к "a"
                    attr(aa,"a")
                      #[1] "26 numbers"
                    attr(aa,"class") # просмотр атрибута
                      #[1] "data.table" "data.frame"
                    attr(aa,"a")<-NULL #удаление ранее созданного атрибута
      df<- data.frame(a=1L:5L,bb=seq(0,1,length.out = 5),b= 
                      c("ab","cde","fghi","a","s"), stringsAsFactors = F)
      h5write(df, "example.h5","df")
      h5ls("example.h5")
      head(df)   
      H5close()
      
      readA= h5read("example.h5", "foo/A") #allows to read the spec. file by specifyinf the file's path
      readA
      
      h5write(c(20:22),"example.h5", "foo/A", index=list(1:3,1))# changes data in the table.
        #In this case we have changed the numbers on 20, 21 and 22 in first 3 rows in 1rst col.
      h5read("example.h5", "foo/A")
  
  
      #Reading from WEB
      #Webscraping  - extracting data from the web
      #Example by working with one web source
      con=url("https://scholar.google.com/citations?user=HI-I6C0AAAAJ&hl=en")
      htmlcode = readLines(con)
      close(con) #closing the connection with the source
      htmlcode
      
      #XML package
      library("httr")
      library("XML")
      library("bitops")# out of lecture - have to execute in order to make R to read url correctly for future operations.
      library("RCurl")
      url<-getURL("https://scholar.google.com/citations?user=HI-I6C0AAAAJ&hl=en", ssl.verifypeer = FALSE)
      html<- htmlTreeParse(url, useInternalNodes=TRUE)
      xpathSApply(html,"//title",xmlValue)
      
      htmlcode<-url("https://scholar.google.com/citations?user=HI-I6C0AAAAJ&hl=en", method = "wininet")
      code2<-readLines(htmlcode)
      try<-htmlParse(code2)
      xpathSApply(try,"//title",xmlValue)
      close(htmlcode)
      
      
      url1<-"https://scholar.google.com/citations?user=HI-I6C0AAAAJ&hl=en"
      html2=GET(url1)
      content2= content(html2, as="text")
      parsedHtml = htmlParse(content2, asText = T)
      xpathSApply(parsedHtml,"//title",xmlValue)
      xpathSApply(parsedHtml, "//td[@class='gsc_a_c']", xmlValue)
      
      
      #Reading websites, where pas authofication is needed
      pg2 = GET("http://httpbin.org/basic-auth/user/passwd",
                authenticate("user","passwd"))
      pg2    
          #Response [http://httpbin.org/basic-auth/user/passwd]
          #Date: 2017-05-20 11:39
          #Status: 200
          #Content-Type: application/json
          #Size: 47 B
          #{
          #  "authenticated": true, 
          #  "user": "user"
          #}
      names(pg2)
        #[1] "url"         "status_code" "headers"     "all_headers" "cookies"    
        #[6] "content"     "date"        "times"       "request"     "handle"
      
      google = handle("http://google.com")
      pg1= GET(handle = google, path = "/")
      pg1
      #MORE DATA ABOUT WEBSCRAPING - www.r-bloggers.com/?s=Web+Scraping
      
    #Reading from APIs
      #Accessing twitter from R
      myapp = oauth_app("twitter", key="Consummer key here", secret="yours")
      sig = sign_oauth1.0(myapp,
                          token = "yourtokenhere",
                          token_secret = "YourTokenSecretHere") 
      homeTL = GET("https://api.twitter.com/1.1/statueses/home_timeline.json", sig)
        #Link in homeTL:1.1 - version of APi
                    #statuses - data type to explore
                    #home_timeline - place 
                    #json - file format which is the only file type supported by Twitter.
                    # sig - abbreviative from sign in (it will use sign in data from "sign_oauth1.0" used previously)
        #homeTL - is simply a Json file 
      json1<- content(homeTL) #function allows to get the contetnt from the file
              #In a way it transforms json file into json for R. 
              # It is still complex to read, thus we come to next step.
      json2<- jsonlite::fromJSON(toJSON(json1)) #func. converts file into data frame
              #In this case - each row corresponds to a tweet in a timeline
              #How to know which URL to use - go to API documentation
      json2[1,1:4]
     
       #Readinf from other Sources 
        #Reading images
          #Jpeg
          #readbitmap
          #png
          #EBImage(Bioconductor)
        #Reading GIS (Geographic Information System) data
          #rdgal
          #rgeos
          #raster
        #Reading Music data
          #tuneR
          #seewave
      
    #Getting and cleaning data Week 2 Quiz
      #Q1 
      # 1. To make your own application, register at at
      #    https://github.com/settings/applications
      
      install.packages("httpuv")
      library("httpuv")
      library("httr")
      oauth_endpoints("github") #function finds links for authorization
      myapp <- oauth_app("github",
                         key = "719779ab8043ef968e35",
                        secret = "c5f4fa85968fdd59ce5d9c27ad855059e45e4e28")#Opening app in R by authorization
      # 2. Get OAuth credentials
      github_token <- oauth2.0_token(oauth_endpoints("github"), myapp) #Get OAuth credentials
      
      gtoken <- config(token = github_token)
      req <- GET("https://api.github.com/rate_limit", gtoken)
      stop_for_status(req)
      content(req)
      
      #Actual answer
     library(jsonlite)
      
      repos = GET("https://api.github.com/users/jtleek/repos", gtoken)
      stop_for_status(repos)
      jsonTemp = content(repos)
      json = fromJSON(toJSON(jsonTemp))
      json[json$name == "datasharing", "created_at"]
    #Q2
      install.packages("sqldf ")
      library(sqldf)
      setwd("C:/Users/Dell/Documents/R")
      cvsulr<-"https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06pid.csv"
      download.file(cvsulr, "C:/Users/Dell/Documents/R/American Community Survey.csv")
      acs<-read.csv("C:/Users/Dell/Documents/R/American Community Survey.csv")
    #Q4
      library("XML")
      library("httr")
      
      #1st code
      url1<-GET("http://biostat.jhsph.edu/~jleek/contact.html")
      db<- htmlTreeParse(url1, useInternalNodes = T)
      nchar(capture.output(db)[c(10,20,30,100)])
      length(capture.output(db))
      #result
      #[1]  68 117  44   2
      #[1] 167
      
      #2nd
      url1<-GET("http://biostat.jhsph.edu/~jleek/contact.html")
      db<- htmlTreeParse(url1, useInternalNodes = T)
      db2<-xmlRoot(db)
      nchar(capture.output(db2)[c(10,20,30,100)])
      length(capture.output(db2))
      #result
      #[1]  39 117   0   0
      #[1] 159
      
      #3rd
      url1 <- url("http://biostat.jhsph.edu/~jleek/contact.html")
      db3 <- readLines(url1)
      close(url1)
      nchar(db3[c(10, 20, 30, 100)])
      length(db3)
      #result
      #[1] 45 31  7 25
      #[1] 180
      
      
    #Q5
      #Need to read fixed width file
      getwd()
      forurl<-"https://d396qusza40orc.cloudfront.net/getdata%2Fwksst8110.for"
      download.file(forurl, "C:/Users/Dell/Documents/R/datase.for")
      dbfor<-read.fwf(file = "C:/Users/Dell/Documents/R/datase.for", widths=c(15, 4, 1, 3, 5, 4,1,3,5,4,1,3),header = FALSE, skip = 4)
      head(dbfor)
      sum(dbfor$V6)
  
  #Getting and cleaning data Week 3
    #Subsetting and sorting
      #Subseting
        set.seed(13435)
        x<- data.frame("var1"= sample(1:5), "var2"= sample(6:10), "var3"= sample(11:15))
              #sample - раскидывает числа в рандомном порядке
        x<- x[sample(1:5),];x$var2[c(1,3)]= NA
            #x[sample(1:5),] - в рандомном порядке меняет местами rows
            #x$var2[c(1,3)]= NA -в колонке var2б линии 1 и 3 становятся Na
        x
        x[,1]
        x[(x$var1 <= 3 & x$var3>11),] # returns a data.frame where 2 conditions are met
            # var1 var2 var3
            #   1    2   NA   15
            #   2    3   NA   12
        x[(x$var1 <= 3 | x$var3>11),]# | - means "or". So here there are two conditions and one of them should be met
            #var1 var2 var3
            #1    2   NA   15
            #5    4    9   13
            #2    3   NA   12
            #4    1   10   11
            #3    5    6   14
        x[which(x$var2 > 8),]# "which" - does not return NA values!!!!
            #var1 var2 var3
            #5    4    9   13
            #4    1   10   11
    #Sorting
        sort(x$var1) # sort - returns numbers in a particular order
        #[1] 1 2 3 4 5
        
        sort(x$var1, decreasing = T) #decreasing returns numbers in decreasing order
        #[1] 5 4 3 2 1
        
        sort(x$var2, na.last=T) #puts all NA values at the end of the return
    #Ordering 
        x[order(x$var1),] # "order" allows to order all rows in order of a particular column 
          #var1 var2 var3
          #4    1   10   11
          #1    2   NA   15
          #2    3   NA   12
          #5    4    9   13
          #3    5    6   14
        x[order(x$var1, x$var3),] #double ordering by 2 columns
          #var1 var2 var3
          #4    1   10   11
          #1    2   NA   15
          #2    3   NA   12
          #5    4    9   13
          #3    5    6   14
        
        
        #Ordering with plyr package
          
          library("plyr")
          arrange(x, var1) #doing basically the same thing as above
              #  var1 var2 var3
              #1    1   10   11
              #2    2   NA   15
              #3    3   NA   12
              #4    4    9   13
              #5    5    6   14
          
          arrange(x,desc(var1)) #ordering in decrease
          
              #  var1 var2 var3
              #1    5    6   14
              #2    4    9   13
              #3    3   NA   12
              #4    2   NA   15
              #5    1   10   11
        
        
        #Adding rows and columns
          x$var4<-rnorm(5) #add a new row named "var4" with value rnorm(5)
          x
          
          y<-cbind(x,var4=rnorm(5)) # adding new colum with cbind function
          y<-rbind(x, rnorm(4)) # adding new row with rbind function
          y<-rbind(c(1,5,7,9),x) #In this case row adds to the top of data frame
            y       
        
      #Summarazinf data
 
                       getwd()if(!file.exists("./data")){dir.create("./data")}
            url<-"https://data.baltimorecity.gov/api/views/kewm-hd3n/rows.csv?accessType=DOWNLOAD"
            download.file(url,destfile = "C:/Users/Dell/Documents/R/data/restauraunts.csv", method = "wininet")
            restdata<- read.csv("C:/Users/Dell/Documents/R/data/restauraunts.csv")
            head(restdata)          
            tail(restdata,3)
            summary(restdata)            
            str(restdata)
            
            quantile(restdata$councilDistrict, na.rm=T) # gives the values: min value of that col - 7 and max is 14
              #0%  25%  50%  75% 100% 
              #7    7    7   14   14 
            quantile(restdata$zipCode, probs = c(0.5,0.7,0.9))
              #50%   70%   90% 
              #21211 21211 21211
            table(restdata$neighborhood, useNA = "ifany") #allows to see how many times the particular values in one row repeats.
                                            # useNA = "ifany" - by adding it will create the additional row with number of NA repeats
              #Hampden  Medfield Woodberry 
              #29         1         3
            table(restdata$neighborhood, restdata$zipCode) # creates a table where two colums are combined and there is info about repeats based on theese 2 columns
              #            21209 21211 21215
              #Hampden       0    28     1
              #Medfield      1     0     0
              #Woodberry     0     3     0
        #Check for missing values
            sum(is.na(restdata$zipCode))#no missing values in zipcode column
              #[1] 0 #if it would be "1" it means that there are NA values
            any(is.na(restdata$zipCode))# logical function stating that it FALSE that there is any NA values in a column
              #[1] FALSE
            all(restdata$zipCode<0) #does all values meet the desired condition
              #[1] FALSE
            colSums(is.na(restdata)) #determins existence of NA in each column
              #name         zipCode    neighborhood councilDistrict  policeDistrict      Location.1 
              #0               0               0               0               0               0
            all(colSums(is.na(restdata))==0)
              #[1] TRUE 
            table(restdata$zipCode %in% c("21215") ) #how many values in a column a having a particular value
              #FALSE  TRUE 
              #32     1
            table(restdata$zipCode %in% c("21215", "21211") ) #how many values meet 1 of 2 conditions
              #FALSE  TRUE 
              #1    32 
            restdata[restdata$zipCode %in% c("21215","21209"),] #it filters the table and returns the table based on the filtered column
                #            name zipCode neighborhood councilDistrict policeDistrict
                #4    BACKSTRETCH SALOON   21209     Medfield               7       NORTHERN
                #17 GRANDVIEW RESTAURANT   21215      Hampden              14       NORTHERN
                #Location.1
                #4  1301 OLD COLDSPRING Ln\nBaltimore, MD\n
                #17        3838 ROLAND AVE\nBaltimore, MD\n
          #Cross Tabs
            data("UCBAdmissions")
            DF<-as.data.frame(UCBAdmissions) #function creates a data frame from a data set
            summary(DF)
            head(DF)
                #Admit       Gender   Dept       Freq      
                #Admitted:12   Male  :12   A:4   Min.   :  8.0  
                #Rejected:12   Female:12   B:4   1st Qu.: 80.0  
                                                #C:4   Median :170.0  
                                                #D:4   Mean   :188.6  
                                                #E:4   3rd Qu.:302.5  
                                                #F:4   Max.   :512.0
            xt<-xtabs(Freq ~ Gender + Admit, data = DF) # func. allows to match columns and calculate the total sum of desired column (in that case:Freq) for each value in specified neigbor columns (Gender & Admit)
              #Gender   Admitted Rejected
              #Male       1198     1493
              #Female      557     1278
              
            head(DF,30)
            
          #Flat tables
            dim(warpbreaks)
            warpbreaks$replicate <- rep(1:8,len=54)
            xt<-xtabs(breaks~ .,data=warpbreaks) # when"." in counts specified column for all neighbour columns            
            xt           
            
                #, , replicate = 1
                #
                #tension
                #wool   L   M   H
                #A 268  86 124
                #B  84 150  69
                #
                #, , replicate = 2
                #
                #tension
                #wool   L   M   H
                #A 133 130  97
                #B 170 109 100
                
            ftable(xt)  # it flats the info and make it easier to read then above    
                #replicate  1  2  3  4  5  6  7  8
                #wool tension                                  
                #A    L                 93 30 54 25 70 52 51 26
                #M                 30 54 21 29 17 12 18 35
                #H                 28 15 62 21 24 18 10 43
                #B    L                 31 41 20 71 14 29 19 29
                #M                 39 28 21 39 71 26 19 16
                #H                 17 13 15 15 16 48 21 24
          #Data size
            fakedb<-rnorm(1e7) 
            object.size(fakedb)
              #80000040 bytes
            print(object.size(fakedb), units = "Mb")
              #76.3 Mb
            
    #Creating New Variables
      #Getting the data from the web
        download.file(url,destfile = "C:/Users/Dell/Documents/R/data/restauraunts.csv", method = "wininet")
        restdata<- read.csv("C:/Users/Dell/Documents/R/data/restauraunts.csv")
        head(restdata) 
         #Creating sewuences
            s1<-seq(1,10,by=2) #returns numbers nembers from 1 to 10 overjumping through 2
            s1
              #[1] 1 3 5 7 9
            s2<-seq(1,10,length=2)# returns 2 numbers from 1 to 10 in particular order
            s2
              #[1]  1 10
            x<-c(1,3,8,25,100,1)
            seq(along=x) #couts number of charachters
              #[1] 1 2 3 4 5 6
          
          restdata$nearMe<-restdata$neighborhood %in% c("Medfield","Woodberry")
            #FALSE  TRUE 
            #29     4 
          table(restdata$nearMe)
          head(restdata)
          
          restdata$ziprong<-ifelse(restdata$zipCode<0,T,F) - #in this function, TRUE comes if statement right and FALSE vs.
          table(restdata$ziprong, restdata$zipCode<0) #returns a logical statement of 2 variables that meet condition
            #FALSE
            #FALSE    33
        
        #Creating categorial valriables (breaking the data type by categories)
          restdata$ziipgroups<-cut(restdata$zipCode, breaks = quantile(restdata$zipCode, probs=c(0.1,0.5) ))
          quantile(restdata$zipCode)
        #Eesier cutting by group with special package  
          install.packages("Hmisc")
          library("Hmisc")
          restdata$zipgroups<-cut2(restdata$zipCode,g=1)# AUTOMATICALLY FIND QUANTILES AND MAKES 4 GOUPS (due to small amount of data created only 2 groups, but had to creat 4)
          table(restdata$zipgroups)
          #[21209,21215)         21215 
          #         32             1 
          
        #Turning variable into factor type
          restdata$zcf<-factor(restdata$zipCode)
          restdata$zcf[1:10]
            #[1] 21211 21211 21211 21209 21211 21211 21211 21211 21211 21211
            #Levels: 21209 21211 21215
        #Mutate function creting a new table by adding new variable
          library("plyr")
            restdata2<-mutate(restdata, zipgroups = cut2(zipCode, g=4))
            head(restdata2)            
            head(restdata)
      #Reshaping data
            
        # Start with reshaping 
            library("reshape2")
            head(mtcars)
            
        # Melting data frame
            #Позволяет трасформировать таблицу, что часть колонок уйдет, а их название попадет
            # в новую колонку и им будет присвоено значение в соответствии со старой таблицей
            mtcars$carnames<-rownames(mtcars)
            carmelt<- melt(mtcars, id=c("carnames", "gear","cyl"), measure.vars = c("mpg","hp"))
            head(carmelt, 3)
              #       carnames gear cyl variable value
              #1     Mazda RX4    4   6      mpg  21.0
              #2 Mazda RX4 Wag    4   6      mpg  21.0
              #3    Datsun 710    4   4      mpg  22.8
        
        # Casting data frames (very similar to xtabs function)
            cyldata<- dcast(carmelt, cyl ~ variable, length)
            cyldata
              # cyl mpg hp
              #1   4  11 11
              #2   6   7  7
              #3   8  14 14
            
            cyldata<- dcast(carmelt, cyl ~ variable, mean) #gettin the mean for all cyl gropus 
            cyldata            
              # cyl      mpg        hp
              #1   4 26.66364  82.63636
              #2   6 19.74286 122.28571
              #3   8 15.10000 209.21429
        
        # Averaging values
            head(InsectSprays)
              # count spray
              #1    10     A
              #2     7     A
              #3    20     A
              #4    14     A
              #5    14     A
              #6    12     A
            
            tapply(InsectSprays@count, InsectSprays@spray, sum) #counts the sum of one variable by groups wrote in another variable (column)
            spIn<- split(InsectSprays$count, InsectSprays$spray) #shows the list all values by each group
              #$A
              #[1] 10  7 20 14 14 12 10 23 17 20 14 13
              #
              #$B
              #[1] 11 17 21 11 16 14 17 17 19 21  7 13
              #...
            sprcount<-lapply(spIn,sum)
            sprcount
              #$A
              #[1] 174
              #
              #$B
              #[1] 184
              #...
            unlist(sprcount)#useful for reading after applying above function. but this can be done in one time with "tapply"
              #A   B   C   D   E   F 
              #174 184  25  59  42 200 
            sapply(spIn, sum)#useful for reading and could be performed after "split"
              #A   B   C   D   E   F 
              #174 184  25  59  42 200 
          
#TEST vK members rekvizit
    dbvk<-read.csv("C:/Users/Dell/Documents/R/R vktest/new members vk rekvizit.csv")
    head(dbvk)
    dim(dbvk)
  #the end
    
          #plyr package to count totals for each neigbour variable
            install.packages("plyr")
            library("plyr")
            head(InsectSprays,10)
            ddply(InsectSprays,.(spray), summarize, sum=sum(count))
            t1<-data.frame(numbers=c(1,1,1,1,1,1,1,1,1,1,1,1), let=c("a","b","c"))
            ddply(t1,.(let), summarise, sum=sum(numbers))
                #Warning in install.packages :
                #package ‘ddplyr’ is not available (for R version 3.3.3)
              #   pray sum
              #1     A 174
              #2     B 184
              #3     C  25
              #4     D  59
              #5     E  42
              #6     F 200
            table(InsectSprays$spray)
      # Managig data frames with dplyr package
        #Dplyr verbs
            #select()	select columns
            #filter()	filter rows
            #arrange()	re-order or arrange rows
            #mutate()	create new columns
            #summarise()	summarise values
            #group_by()	allows for group operations in the “split-apply-combine” concept
            
            library("dplyr")
            
            chicago<-readRDS("chicago.rds")
            db1<-read.csv("C:/Users/Dell/Documents/R/Course 2/hw1_data.csv")
            dim(db1)
            names(db1)
              #[1] "Ozone"   "Solar.R" "Wind"    "Temp"    "Month"   "Day" 
          #select
            head(select(db1, Ozone:Wind)) #function "select" allows not to use $ and write the colnames directly
              #1    41     190  7.4
              #2    36     118  8.0
              #3    12     149 12.6
              #4    18     313 11.5
              #5    NA      NA 14.3
              #6    28      NA 14.9
            head(select(db1,-(Ozone:Wind))) #shows all cols except chosen by putting "-"
                #Temp Month Day
                #1   67     5   1
                #2   72     5   2
                #3   74     5   3
                #4   62     5   4
                #5   56     5   5
                #6   66     5   6 
            names(db1)
            
          #filter 
            filter(db1, Temp>95) #filtering by Temp col>95
              #   Ozone Solar.R Wind Temp Month Day
              #1    76     203  9.7   97     8  28
              #2    84     237  6.3   96     8  30
            head(filter(db1, Temp > 80 & Solar.R > 100),3) # Filtering by 2 columns
              #Ozone Solar.R Wind Temp Month Day
              #1    45     252 14.9   81     5  29
              #2    NA     186  9.2   84     6   4
              #3    NA     220  8.6   85     6   5
            head(filter(db1, Temp>=60 & Solar.R>190 & Month==5 & Temp==66),5)
            head(db1,10)
            table(db1$Temp, useNA = "ifany")
            mean(db1$Temp)
          #arrange
            #Filter table in order of chosen column по порядку
              head(arrange(db1, Ozone),3)
                #  Ozone Solar.R Wind Temp Month Day
                #1     1       8  9.7   59     5  21
                #2     4      25  9.7   61     5  23
                #3     6      78 18.4   57     5  18
              head(arrange(db1, desc(Ozone)),3) # shows in disorder (from botumn to top)
                #  Ozone Solar.R Wind Temp Month Day
                #1   168     238  3.4   81     8  25
                #2   135     269  4.1   84     7   1
                #3   122     255  4.0   89     8   7
          #Rename
              install.packages("rsdmx")
              library(rsdmx)
              library(plyr)
              library(dplyr)
              names(db1)
              db1 <- rename(db1,TempNew = Temp, MonthNew=Month) #names changed (ex.:below)
              
              detach("package:plyr", unload=TRUE) # used to turn off plyr package cause it conflicts with dplyr
              names(db1)
                #                                     !
                #[1] "Ozone"   "Solar.R" "Wind"    "Temp"    "Month"   "Day" 
                #[1] "Ozone"   "Solar.R" "Wind"    "tmp"     "Month"   "Day"
          
          #mutate - creates new variables
              db1<- mutate(db1,NewTemp = Temp - mean(Temp, na.rm = T) )
              head(select(db1, Temp, NewTemp))
              #  Temp    NewTemp
              #1   67 -10.882353
              #2   72  -5.882353
              #3   74  -3.882353
              #4   62 -15.882353
              #5   56 -21.882353
              #6   66 -11.882353
            db1<-mutate(db1, TempLvl3 = (cut2(Temp,g=3)))
            table(db1$TempLvl3)
            db1<-mutate(db1, TempLvl = factor(db1$Temp>77.88235, labels = c("cold","hot"))) #creates new column 
            db1<-mutate(db1, TempLvl = cut(db1$Temp, breaks = 3, labels = c("cold", "normal", "hot")))
            head(db1)
            
            head(filter(db1, Temp>75))
            hotcold<-group_by(db1, TempLvl ) #allows to categories or group the whole table by specific column
            summarise(hotcold, TempMax= max(Temp), TempMin = min(Temp))# used after group_by function to sum chosen columns based on previously chosen group
            j<-table(db1$TempLvl)
            jdf<-data.frame(j)
            
            db1<-mutate(db1, year = as.POSIXlt(date)$yea+1900)
          head(db1)
          
      #Merging data
          getwd()
          setwd("C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/")
          if(!file.exists("./data")){dir.create("./data")}          
          fileurl1<-"https://dl.dropboxusercontent.com/u/7710864/data/reviews-apr29.csv"
          fileurl2<-"https://dl.dropboxusercontent.com/u/7710864/data/solutions-apr29.csv"
          download.file(fileurl1, destfile = "./data/reviews.csv", method = "curl")
          download.file(fileurl2, destfile = "./data/solutions.csv", method = "curl")
          reviews<-read.csv("./data/reviews.csv");solutions<-read.csv("./data/solutions.csv")
          head(reviews,2)
          head(solutions,2)
          names(reviews)
          names(solutions)
        #Merge command
          #It has special parameters:x,y,by,by.x,by.y,all
          #it is used for telleting MERGE command which columns to merge 
          #(by default it merge all columns with the same name)
          
          mergeData<- merge(reviews, solutions, by.x = "solution_id", by.y = "id", all=T)
            #in cmd it says that we merge mentioned columns in new table. "all=T" means
            # that if there is no value in add a row with NA value
          head(mergeData, 2)
            #  solution_id id reviewer_id    start.x     stop.x time_left.x accept problem_id
            #1           1  4          26 1304095267 1304095423        2089      1        156
            #2           2  6          29 1304095471 1304095513        1999      1        269
            #  subject_id    start.y     stop.y time_left.y answer
            #1         29 1304095119 1304095169        2343      B
            #2         25 1304095119 1304095183        2329      C
          intersect(names(reviews),names(solutions))
            #shows variaables that intersects (пересекаются)
            #[1] "id"        "start"     "stop"      "time_left"
        
        # "join" function for merging in plyr package
          #It is faster then "merge", but it only can merge based on common names
          
          df1<-data.frame(id=sample(1:10),x=rnorm(10));df2<-data.frame(id=sample(1:10), y = rnorm(10))  
          head(arrange(join(df1,df2),id)) #arrange делает все по порядку
            #  id           x           y
            #1  1 -0.21686514  0.11929735
            #2  2  0.12245654 -1.35995136
            #3  3  0.04677682  0.10403770
        
      #Swirl Lesson 1: Manipulating Data with dplyr  
        library("swirl")  
        swirl()
        
        #select()
          #1st it allows to show only chosen columns
            #> select(cran, ip_id, package, country)
            # A tibble: 225,468 x 3
            #ip_id      package country
            #<int>        <chr>   <chr>
            #  1     1    htmltools      US
            #2     2      tseries      US
            #3     3        party      US
              #It allso can show columns from to
                #> select(cran,r_arch:country)
                # A tibble: 225,468 x 5
                #r_arch      r_os      package version country
                #<chr>     <chr>        <chr>   <chr>   <chr>
                #  1 x86_64   mingw32    htmltools   0.2.4      US
                  #To show all columns "except" specific ones put "-"
                    #> select(cran, -time)
                    # A tibble: 225,468 x 10
                    #X       date    size r_version r_arch      r_os      package version country
                    #  1     1 2014-07-08   80589     3.1.0 x86_64   mingw32    htmltools   0.2.4      US
        #filter()
          #allows to filter by subset of specific column  
            #> filter(cran, package == "swirl")
            # A tibble: 820 x 11
            #X       date     time   size r_version r_arch         r_os package version
            #<int>      <chr>    <chr>  <int>     <chr>  <chr>        <chr>   <chr>   <chr>
            #1    27 2014-07-08 00:17:16 105350     3.0.2 x86_64      mingw32   swirl   2.2.9
            #2   156 2014-07-08 00:22:53  41261     3.1.0 x86_64    linux-gnu   swirl   2.2.9
              # filter with condition eather/or
                #> filter(cran, country == "US" | country == "IN")
                # A tibble: 95,283 x 11
                #X       date     time    size r_version r_arch      r_os      package version
                #<int>      <chr>    <chr>   <int>     <chr>  <chr>     <chr>        <chr>   <chr>
                #  1     1 2014-07-08 00:54:41   80589     3.1.0 x86_64   mingw32    htmltools   0.2.4
                  # filter by conditioning to show without NA values
                    #> filter(cran, !is.na(r_version))
                    # A tibble: 207,205 x 11
                    #X       date     time    size r_version r_arch      r_os      package version
                    #<int>      <chr>    <chr>   <int>     <chr>  <chr>     <chr>        <chr>   <chr>
                    #  1     1 2014-07-08 00:54:41   80589     3.1.0 x86_64   mingw32    htmltools   0.2.4
        #arrange
          #arrange по порядку allows to arrange data based on specific column
            #> arrange(cran2, ip_id)
            # A tibble: 225,468 x 8
            #size r_version r_arch         r_os     package version country ip_id
            #<int>     <chr>  <chr>        <chr>       <chr>   <chr>   <chr> <int>
            #1  80589     3.1.0 x86_64      mingw32   htmltools   0.2.4      US     1
            #2 180562     3.0.2 x86_64      mingw32        yaml  2.1.13      US     1
            #3 190120     3.1.0   i386      mingw32       babel   0.2-6      US     1
              #to arrange descending (убывающий) write desc
                # arranging by multiple variables
                  #> arrange(cran2, package, ip_id)
                  # A tibble: 225,468 x 8
                  #size r_version r_arch         r_os package version country ip_id
                  #<int>     <chr>  <chr>        <chr>   <chr>   <chr>   <chr> <int>
                  #1 71677     3.0.3 x86_64 darwin10.8.0      A3   0.9.2      CN  1003
                  #2 71672     3.1.0 x86_64    linux-gnu      A3   0.9.2      US  1015
        #mutate
          # At a time possible to create several variables, which comes one from another in one line
            #> mutate(cran3, size_mb = size / 2^20, size_gb = size_mb / 2^10)
            # A tibble: 225,468 x 5
            #ip_id      package    size     size_mb      size_gb
            #<int>        <chr>   <int>       <dbl>        <dbl>
            #  1     1    htmltools   80589 0.076855659 7.505435e-05
        #summarize
          #Example  
            #> summarize(cran, avg_bytes = mean(size))
            #avg_bytes
            #1  844086.5
      
     # swirl Lesson 2: Grouping and Chaining with dplyr 
        #Group_by
        #pack_sum <- summarize(by_package,
        #                      count = n() ,
        #                      unique = n_distinct(ip_id) ,
        #                      countries = n_distinct(country) ,
        #                      avg_bytes = mean(size) )
         #n() - number of rows for particular group 
         #n_distinct() - amount of unique values 
         #> pack_sum
         # A tibble: 6,023 x 5
         #package count unique countries  avg_bytes
         #<chr> <int>  <int>     <int>      <dbl>
         #  1     A3    25     24        10   62194.96
         #  2    abc    29     25        16 4826665.00
        
        #%>%
        #example of writing the same piece of code in dif. style
          #1st
            result2 <-
              arrange(
                filter(
                  summarize(
                    group_by(cran,
                             package
                    ),
                    count = n(),
                    unique = n_distinct(ip_id),
                    countries = n_distinct(country),
                    avg_bytes = mean(size)
                  ),
                  countries > 60
                ),
                desc(countries),
                avg_bytes
              )
            
            print(result2)
          #2nd
            result3 <-
              cran %>%
              group_by(package) %>%
              summarize(count = n(),
                        unique = n_distinct(ip_id),
                        countries = n_distinct(country),
                        avg_bytes = mean(size)
              ) %>%
              filter(countries > 60) %>%
              arrange(desc(countries), avg_bytes)
            
     #Swirl Lesson 3: Tidying Data with tidyr
        #Three main rules of tidyr:
        #1) Each variable forms a column
        #2) Each observation forms a row
        #3) Each type of observational unit forms a table
          
          #gather() function allows to combine 2 columns into 1 if theese under 1 header.
            #Example: male and female are now in 1 col. after gather func.
            #> gather(students, sex, count, -grade)
            #   grade    sex count
            #1      A   male     1
            #2      A female     5
              #Example 2
                #before:
                  #> students2
                  #  grade male_1 female_1 male_2 female_2
                  #1     A      3        4      3        4
                  #2     B      6        4      3        5
                #after gather() function:
                  #> res<-gather(students2, sex_class, count,-grade)
                    #sex_class - name of new column in which all unmentioned columns' names
                      #in one column(variable)
                    #count - rest data from previous excisted columns will go in it.
                  #res
                  #   grade sex_class count
                  #1      A    male_1     3
                  #2      B    male_1     6
          
          #separate() - separate 1 column into multiple
            #Example:
              #Before func.:
                #   grade sex_class count
                #1      A    male_1     3
                #2      B    male_1     6
              #After
                #> separate(res, sex_class, c("sex","class"))
                #grade    sex class count
                #    1      A   male     1     3
                  #It has splited sex_class onto "sex" and "class". values are 
                  #separated by something other than a letter or 
                  #number (in this case, an underscore.)
            #spread - Spread a key-value pair across multiple columns.
              #Example:
                #Before:
                  #    name    test  class grade
                  #1  Sally midterm class1     A
                  #2  Sally   final class1     C
                #After:
                  #    name  class final midterm
                  #1  Brian class1     B       B
                  #...
          #parse_number() with mutate()-allows to take numbers only from column's values
            #Example:
              #before:
                #   name  class final midterm
                #1  Brian class1     B       B
              #after
                #students3 %>%
                #  gather(class, grade, class1:class5, na.rm = TRUE) %>%
                #  spread(test,grade ) %>%
                #  print
                #    name class final midterm
                #1  Brian     1     B       B
         #unique() - if data repeates it takes duplicates off
            #Example
              #before
                #id  name sex
                #1  168 Brian   F
                #2  168 Brian   F
                #3  588 Sally   M
                #4  588 Sally   M
              #after
                #student_info <- students4 %>%
                #  select(id, name, sex) %>%
                #  unique()%>%
                #  print
                #submit()
                #id  name sex
                #1 168 Brian   F
                #3 588 Sally   M
         #bind_rows -  Efficiently bind multiple data frames by row and column
            #Example:
            #> bind_rows(passed,failed)
            #   name class final status
            #1  Brian     1     B passed
            #2  Roger     2     A passed
            #3  Roger     5     A passed
            #4  Karen     4     A passed
            #5  Brian     5     C failed
            #6  Sally     1     C failed
            #7  Sally     3     C failed
  #Week 3 Quiz
     #Q1.
      #Create a logical vector that identifies the households on greater than 
      #10 acres who sold more than $10,000 worth of agriculture products. Assign
      #that logical vector to the variable agricultureLogical. Apply the which()
      #function like this to identify the rows of the data frame where the logical
      #vector is TRUE.
            
       setwd("C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/Assignment week3 Quiz")
      
      if(!file.exists("./Assignment week3 Quiz")){dir.create("./Assignment week3 Quiz")}
      fileurl1<-"https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv"
      download.file(fileurl1, destfile = "C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/Assignment week3 Quiz/ushouse.csv", mode = "wininet" )
      dataush<-read.csv("./ushouse.csv")
      library(dplyr)
   dt<-tbl_df(dataush)
   agricultureLogical<-which(with(dt, ACR==3 & AGS==6 ))
   agricultureLogical
   # [1]  125  238  262
     #Q2
      #Using the jpeg package read in the following picture of your instructor 
      #into R
      #https://d396qusza40orc.cloudfront.net/getdata%2Fjeff.jpg
      #Use the parameter native=TRUE. What are the 30th and 80th quantiles
      #of the resulting data? (some Linux systems may produce an answer 638 
      #different for the 30th quantile)
   
     install.packages("jpeg")
      library(jpeg)   
     fileurl12<-"https://d396qusza40orc.cloudfront.net/getdata%2Fjeff.jpg"
     download.file(fileurl12, destfile = "C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/Assignment week3 Quiz/photo.jpg", mode = "wb")
     photo<-readJPEG("./photo.jpg", native = TRUE)
    quantile(photo, probs = c(0.3,0.8))
     file.remove("C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/Assignment week3 Quiz/photo.jpg")
     
    #Q3 
     #Load the Gross Domestic Product data for the 190 ranked countries in this
     #data set:
     #https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FGDP.csv
     #Load the educational data from this data set:
     #https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FEDSTATS_Country.csv
     #Match the data based on the country shortcode. How many of the IDs match? Sort the data frame in descending order by GDP rank (so United States is last). What is the 13th country in the resulting data frame?
     #Original data sources:
     #http://data.worldbank.org/data-catalog/GDP-ranking-table
     #http://data.worldbank.org/data-catalog/ed-stats
     
     wd<-getwd()
     getwd()
     fileurl13<-"https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FGDP.csv"
     fileurl14<-"https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FEDSTATS_Country.csv"
     download.file(fileurl13, destfile ="C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/Assignment week3 Quiz/gdp.csv" )
     download.file(fileurl14, destfile = "C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/Assignment week3 Quiz/Country.csv")
     gdp<-read.csv("C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/Assignment week3 Quiz/gdp.csv", skip = 4, nrows = 190)
     country<-read.csv("C:/Users/Dell/Documents/R/Course 3 cleaning and getting data/Assignment week3 Quiz/Country.csv")
     tbl_df(gdp)
     country1<-tbl_df(country)
     gdp<-filter(gdp,X!="")
     tbl_df(gdp)
     country1
    
      unique(gdp$X)
      unique(country1$CountryCode)
     library(dplyr)
     merged<-merge(gdp,country,all=T , by.x = "X", by.y = "CountryCode")
     filmerged<-filter(merged,!is.na(X))
     tbl_df(merged)
     length(unique(merged$X.1))
     tbl_df(filmerged)
     View(merged)
     sum(filmerged$X=="")
     merged<-arrange(merged, desc(X) )
     head(merged,13)
     View(merged)
     
     avfilt<-filter(merged, Income.Group == "High income: nonOECD")
    mean(avfilt$X.1, na.rm = T)              
    avfilt1<-filter(merged, Income.Group == "High income: OECD")
    mean(avfilt1$X.1, na.rm = T)  
    
    merged$cutrank<-cut(merged$X.1, breaks = 5)
    unique(merged$cutrank)
    top<-merged %>%
      group_by(cutrank)
    
    table(merged$cutrank, merged$Income.Group)
  
  #Editing text variables
    getwd()
    setwd("C:/Users/Dell/Documents/R/Course 3 cleaning and getting data")
    if(!file.exists("./week4")){dir.create("week4")}
    dir()  
    setwd("./week4/")
    fileurl<-"https://data.baltimorecity.gov/api/views/dz54-2aru/rows.csv?accessType=DOWNLOAD"
    download.file(fileurl,destfile = "./cameras.csv")
    cameradata<-read.csv("./cameras.csv")
    names(cameradata)
      tolower(names(cameradata))  #func.allows to all info with lower letters
      #[1] "address"      "direction"    "street"       "crossstreet"  "intersection"
      #[6] "location.1"  
      
      toupper(names(cameradata))  #...with upper letters
      #[1] "ADDRESS"      "DIRECTION"    "STREET"       "CROSSSTREET"  "INTERSECTION"
      #[6] "LOCATION.1"
     
      splitNames<-strsplit(names(cameradata),"[.]")

      mylist<-list(letters = c("A","B","C"), numbers = 1:3, matrix(1:25, ncol = 5))      
      head(mylist)
      mylist[[1]][2]
      
      splitNames
      Firstelement<-function(x){x[1]}
      sapply(splitNames, Firstelement) #provides only 1st elements in the list
      #[1] "address"      "direction"    "street"       "crossStreet"  "intersection"
      #[6] "Location"
      
      sub("i"," ",names(cameradata)) #changes 1st mentioned element ("i") of chosen words on another ("")
      #[1] "address"      "d rection"    "street"       "crossStreet"  " ntersection"
      #[6] "Locat on.1"  
      gsub("i","",names(cameradata))#changes all mentioned element ("i") of chosen words on another ("")
      #[1] "address"      "d rect on"    "street"       "crossStreet"  " ntersect on"
      #[6] "Locat on.1"  
      
    #Finding values (like ctrl+F)
      grep("Alameda", cameradata$intersection) #provides No of rows with mentioned word (Alameda)
      #[1]  4  5 36
      
      table(grepl("A", cameradata$intersection)) #grepl comes as logical vector and says False or True
      #FALSE  TRUE 
      #   46    34 
      
      cameradata[grepl("Alameda", cameradata$intersection),] #subset where mentioned condition (contains word ALameda) is TRUE
      #4   THE ALAMEDA & E 33RD ST       S/B The Alameda     33rd St
      #5   E 33RD ST & THE ALAMEDA       E/B      E 33rd The Alameda
      #36 HARFORD RD & THE ALAMEDA       N/B  Harford \n The Alameda
      
      grep("Alameda", cameradata$intersection, value = T) # returns the values instead of number location
      #[1] "The Alameda  & 33rd St"   "E 33rd  & The Alameda"   
      #[3] "Harford \n & The Alameda"
      
      grep("Hello world!", cameradata$address) #shows that nothing follow the condition
      #integer(0) 
      
      length(grep("Hi", cameradata$address))
      #[1] 0
      
      
    #Stringr package
      library("stringr")
      nchar("Hello World!") # shows No of symbols in text's piece
      #[1] 12
      
      substr("Hello World!", 1,6)# Takes chosen symbols(1to6) and puts it together
      #[1] "Hello "
      
      a<-"Of"
      b<-"course"
      paste(a,b) #puts chosen symbols together into one row
      #[1] "Of course"
      
        paste0(a,b) #pasting with no space in between
        #[1] "Ofcourse"
      str_trim("Hi       ") #takes useless space off
      #[1] "Hi"
      
  #Regular Expressions
      #Terms:
        #literals - set of charachters that exactly mathc the condition
        #metacharacters - special symbols that represent the particular functions when working with text
          #^ - represents a START of a line (shows all text pieces that starts based prederminated condition)
          #$ - .. end line...
          #[]- mathcing the all lines with mentioned charachters ([Hh][Ee][Ii])
            #Examples:
              #^[0-9][a-zA-Z] - any line starts with number from 1to9 and any capital or small letter from A-Z
              
