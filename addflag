library(plotly)
library(tidyverse)

merflag <- function(dat) {
  final <- read.csv("https://raw.github.com/student3841701/plotlyflag/master/countrylist.csv",h=T)
  al <- merge(dat,final,'iso2c_name')
  al <- al[order(al$order,decreasing=F),]
  al$reor <- seq(1:dim(al)[1])
  all <- al %>% select(-order)
  return(all)}


#random sample example
dta <- data.frame(
xa = sample(1:16), 
ya = sample(1:16),
za = sample(1:16),
iso2c_name=c("AS","AT","AU","AW","BA","BB","BW","BY","BZ","CA","JO","JP","KE","TW","US","YE"))


#use merflag funciton to specific png position
mydta <- merflag(dta)


#choose your x and y variables
out <- list()
for (i in 1:dim(mydta)[1]){
  out[i] <- list(list(
    source =  mydta$source[i],
    xref = 'x',
    yref = 'y',
    x = mydta$xa[i],  #change your x axis variable with mydta$xa
    y = mydta$ya[i],  #change your y axis variablew ith mydta$ya
    sizex = 1,sizey = 1,  #change size 
    xanchor="center",yanchor="middle"))
  }
  

#use "out" in plotly and mapping flag
plot_ly(mydta,x = ~xa, y = ~ya) %>% 
  layout(
    images = out  #add flag
)
