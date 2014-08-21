---
title       : GAS EXPENSES
subtitle    : Based on country gas prices and car gas consumption.  
author      : Igor Demetrius Alencar
job         : Project for Developing data produtcs 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap, regex}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
github:
        user:alencaru
        repo:slidify
--- 

## <p style="color:#2E8B57;">The gas expenses App</p>
<br>
<br>
This app shows the fuel expenses by gas litre country prices and by gasoline consumption for a selected car.

The app was build in <b style="color:#008B8B;">R</b> using shiny package.
If you want run this app you can find it at:
https://github.com/alencaru/Developing-data-products.git

You need download all files and also have <b style="color:#008B8B;">R</b> and <b>shiny</b> package istalled.



--- 

## Data Base 

# This app is compound by two tables:                                                              
                                                                                         
                                                                                          
1. tprices: is the source of country gas prices;
2. tcar: is the source of gas consumption by car.

* tprice source: http://www.nationmaster.com/country-info/stats/Energy/Gasoline-prices;
* tcar source: http://pbeveicular.petrobras.com.br/TabelaConsumo.aspx (in Portuguese only).

---

# <b style="font-size:1.2em;color:#D2691E;">How the app works</b>

After set up that two tables the app run a function that takes the inpts from TextBox and the chosen of DropBox alternatives.

The <b>TextBox</b> is the kilometer you want drive.                                                    
The <b>DropBox</b> has a list with some cars.                                                          
To generate the output the app use a custom function:


```r
myfunction <- function(x,y) {
        x 
        y   
        z <- tcar[tcar$CAR == c(y), 3]
        within(tprice[, c(2, 3)], {expenditure <- x/z*price})
}
```

- The function works with two variables.                                                         
- The first one is the km you want drive.                                                         
- The second one is the car name you will chosen in a dropbox list in the shiny app.

---

## <p style="font-size:0.7em;">Some exemple of the function output
<p>

<!-- html table generated in R 3.0.2 by xtable 1.7-3 package -->
<!-- Mon Aug 18 22:14:52 2014 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> country </TH> <TH> price </TH> <TH> expenditure </TH>  </TR>
  <TR> <TD align="right"> 1 </TD> <TD> Venezuela </TD> <TD align="right"> 0.02 </TD> <TD align="right"> 0.09 </TD> </TR>
  <TR> <TD align="right"> 2 </TD> <TD> United States </TD> <TD align="right"> 0.97 </TD> <TD align="right"> 4.53 </TD> </TR>
  <TR> <TD align="right"> 3 </TD> <TD> Russia </TD> <TD align="right"> 0.99 </TD> <TD align="right"> 4.63 </TD> </TR>
  <TR> <TD align="right"> 4 </TD> <TD> India </TD> <TD align="right"> 1.25 </TD> <TD align="right"> 5.84 </TD> </TR>
  <TR> <TD align="right"> 5 </TD> <TD> Canada </TD> <TD align="right"> 1.32 </TD> <TD align="right"> 6.17 </TD> </TR>
  <TR> <TD align="right"> 6 </TD> <TD> China </TD> <TD align="right"> 1.37 </TD> <TD align="right"> 6.40 </TD> </TR>
  <TR> <TD align="right"> 7 </TD> <TD> Brazil </TD> <TD align="right"> 1.39 </TD> <TD align="right"> 6.50 </TD> </TR>
  <TR> <TD align="right"> 8 </TD> <TD> France </TD> <TD align="right"> 1.91 </TD> <TD align="right"> 8.93 </TD> </TR>
  <TR> <TD align="right"> 9 </TD> <TD> Germany </TD> <TD align="right"> 1.96 </TD> <TD align="right"> 9.16 </TD> </TR>
  <TR> <TD align="right"> 10 </TD> <TD> United Kingdom </TD> <TD align="right"> 2.17 </TD> <TD align="right"> 10.14 </TD> </TR>
  <TR> <TD align="right"> 11 </TD> <TD> Turkey </TD> <TD align="right"> 2.54 </TD> <TD align="right"> 11.87 </TD> </TR>
   </TABLE>


