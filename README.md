# RPROGRAM9.A
#Binomial fit and goodness of fit
x<-c(0,1,2,3,4,5,6)
f<-c(7,64,140,210,132,75,12)
fx<-f*x
sumfx<-sum(f*x)
print(sumfx)
sumf<-sum(f)
print(sumf)
s<-length(x)-1
p=sumfx/sumf/s
print(p)
pr<-dbinom(0:6,size=s,prob=p)
pr<-round(pr,digits=5)
fee<-(pr*sumf)
fe<-round(fee,digits=0)
mydata<- data.frame(x,f,fx,pr,fee,fe)
print(mydata)
sums<-list(NA,sum(f),sum(f*x),NA,NA,sum(fe))
mydata<-rbind(mydata,sums)
print(mydata,row.names=FALSE)
result<-chisq.test(f,p=pr,rescale.p=TRUE)
print(result)
tablevalue<-qchisq(.95, df=s)
print(tablevalue)
OUTPUT:
> x<-c(0,1,2,3,4,5,6)
> f<-c(7,64,140,210,132,75,12)
> fx<-f*x
> sumfx<-sum(f*x)
> print(sumfx)
[1] 1949
> sumf<-sum(f)
> print(sumf)
[1] 640
> s<-length(x)-1
> p=sumfx/sumf/s
> print(p)
[1] 0.5075521
> pr<-dbinom(0:6,size=s,prob=p)
> pr<-round(pr,digits=5)
> fee<-(pr*sumf)
> fe<-round(fee,digits=0)
> mydata<- data.frame(x,f,fx,pr,fee,fe)
> print(mydata)
  x   f  fx      pr      fee  fe
1 0   7   0 0.01426   9.1264   9
2 1  64  64 0.08819  56.4416  56
3 2 140 280 0.22724 145.4336 145
4 3 210 630 0.31229 199.8656 200
5 4 132 528 0.24140 154.4960 154
6 5  75 375 0.09952  63.6928  64
7 6  12  72 0.01710  10.9440  11
> sums<-list(NA,sum(f),sum(f*x),NA,NA,sum(fe))
> mydata<-rbind(mydata,sums)
> print(mydata,row.names=FALSE)
  x   f   fx      pr      fee  fe
  0   7    0 0.01426   9.1264   9
  1  64   64 0.08819  56.4416  56
  2 140  280 0.22724 145.4336 145
  3 210  630 0.31229 199.8656 200
  4 132  528 0.24140 154.4960 154
  5  75  375 0.09952  63.6928  64
  6  12   72 0.01710  10.9440  11
 NA 640 1949      NA       NA 639
> result<-chisq.test(f,p=pr,rescale.p=TRUE)
> print(result)

	Chi-squared test for given probabilities

data:  f
X-squared = 7.6094, df = 6, p-value = 0.2681

> tablevalue<-qchisq(.95, df=s)
> print(tablevalue)
[1] 12.59159
