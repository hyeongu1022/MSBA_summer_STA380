Portfolio Modeling
------------------

### Portfolio 1

For this first portfolio, we chose the following ETFs: JPEM = JPMorgan
Diversified Return Emerging Markets Equity ETF VGT = Vanguard
Information Technology ETF SCHZ = Schwab U.S. Aggregate Bond ETF XOM =
iShares J.P. Morgan USD Emerging Markets Bond ETF USO = United States
Oil Fund

And we loaded these stocks’ data sets from January 9th, 2015. Then we
adjusted Open, High, Low, Close prices for splits and dividends. We
combined all the data matrices into one for close-to-close returns. From
this matrix, we could get overall view of the each stocks’ returns of
each days. The plots below indicates close positive correlation between
the close-to-close returns of JPEM and that of VGT, JPEM and XOM, and
VGT and XOM.

    library(mosaic)

    ## Loading required package: dplyr

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

    ## Loading required package: lattice

    ## Loading required package: ggformula

    ## Loading required package: ggplot2

    ## Loading required package: ggstance

    ## 
    ## Attaching package: 'ggstance'

    ## The following objects are masked from 'package:ggplot2':
    ## 
    ##     geom_errorbarh, GeomErrorbarh

    ## 
    ## New to ggformula?  Try the tutorials: 
    ##  learnr::run_tutorial("introduction", package = "ggformula")
    ##  learnr::run_tutorial("refining", package = "ggformula")

    ## Loading required package: mosaicData

    ## Loading required package: Matrix

    ## Registered S3 method overwritten by 'mosaic':
    ##   method                           from   
    ##   fortify.SpatialPolygonsDataFrame ggplot2

    ## 
    ## The 'mosaic' package masks several functions from core packages in order to add 
    ## additional features.  The original behavior of these functions should not be affected by this.
    ## 
    ## Note: If you use the Matrix package, be sure to load it BEFORE loading mosaic.
    ## 
    ## Have you tried the ggformula package for your plots?

    ## 
    ## Attaching package: 'mosaic'

    ## The following object is masked from 'package:Matrix':
    ## 
    ##     mean

    ## The following object is masked from 'package:ggplot2':
    ## 
    ##     stat

    ## The following objects are masked from 'package:dplyr':
    ## 
    ##     count, do, tally

    ## The following objects are masked from 'package:stats':
    ## 
    ##     binom.test, cor, cor.test, cov, fivenum, IQR, median, prop.test,
    ##     quantile, sd, t.test, var

    ## The following objects are masked from 'package:base':
    ## 
    ##     max, mean, min, prod, range, sample, sum

    library(quantmod)

    ## Loading required package: xts

    ## Loading required package: zoo

    ## 
    ## Attaching package: 'zoo'

    ## The following objects are masked from 'package:base':
    ## 
    ##     as.Date, as.Date.numeric

    ## 
    ## Attaching package: 'xts'

    ## The following objects are masked from 'package:dplyr':
    ## 
    ##     first, last

    ## Loading required package: TTR

    ## Registered S3 method overwritten by 'quantmod':
    ##   method            from
    ##   as.zoo.data.frame zoo

    ## Version 0.4-0 included new data defaults. See ?getSymbols.

    library(foreach)

    # Import a few stocks
    # JPEM = JPMorgan Diversified Return Emerging Markets Equity ETF
    # VGT = Vanguard Information Technology ETF
    # SCHZ = Schwab U.S. Aggregate Bond ETF
    # XOM = iShares J.P. Morgan USD Emerging Markets Bond ETF
    # USO = United States Oil Fund
    mystocks = c("JPEM", "VGT", "SCHZ", "XOM", "USO")
    getSymbols(mystocks, from = "2015-01-09")

    ## 'getSymbols' currently uses auto.assign=TRUE by default, but will
    ## use auto.assign=FALSE in 0.5-0. You will still be able to use
    ## 'loadSymbols' to automatically load data. getOption("getSymbols.env")
    ## and getOption("getSymbols.auto.assign") will still be checked for
    ## alternate defaults.
    ## 
    ## This message is shown once per session and may be disabled by setting 
    ## options("getSymbols.warning4.0"=FALSE). See ?getSymbols for details.

    ## [1] "JPEM" "VGT"  "SCHZ" "XOM"  "USO"

    for(ticker in mystocks) {
        expr = paste0(ticker, "a = adjustOHLC(", ticker, ")")
        eval(parse(text=expr))
    }

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/JPEM?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/JPEM?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/VGT?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/VGT?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/SCHZ?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/SCHZ?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/USO?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=div&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/USO?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query2.finance.yahoo.com/v7/finance/download/USO?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    head(JPEMa)

    ##            JPEM.Open JPEM.High JPEM.Low JPEM.Close JPEM.Volume JPEM.Adjusted
    ## 2015-01-09  44.30710  44.36001 44.30710   44.35134        1200      44.35134
    ## 2015-01-12  44.78505  44.78505 44.16050   44.16050        4000      44.16050
    ## 2015-01-13  44.16050  44.16050 44.16050   44.16050           0      44.16050
    ## 2015-01-14  44.16050  44.16050 44.16050   44.16050           0      44.16050
    ## 2015-01-15  44.43808  44.43808 44.43808   44.43808         200      44.43808
    ## 2015-01-16  44.43808  44.43808 44.43808   44.43808           0      44.43808

    # Combine all the returns in a matrix
    all_returns = cbind(    ClCl(JPEMa),
                                    ClCl(VGTa),
                                    ClCl(SCHZa),
                                    ClCl(XOMa),
                                    ClCl(USOa))
    head(all_returns)

    ##              ClCl.JPEMa    ClCl.VGTa   ClCl.SCHZa    ClCl.XOMa   ClCl.USOa
    ## 2015-01-09           NA           NA           NA           NA          NA
    ## 2015-01-12 -0.004302777 -0.012684990  0.001707132 -0.019218198 -0.04759304
    ## 2015-01-13  0.000000000 -0.000194637  0.000000000 -0.003653293  0.01206209
    ## 2015-01-14  0.000000000 -0.006035855  0.003029729 -0.002888911  0.03688987
    ## 2015-01-15  0.006285602 -0.015279109  0.004530829 -0.008691765 -0.04488231
    ## 2015-01-16  0.000000000  0.009846807 -0.004134505  0.024280621  0.05042975

    all_returns = as.matrix(na.omit(all_returns))

    # Compute the returns from the closing prices
    pairs(all_returns)

![](Figs/unnamed-chunk-1-1.png) We tried the bootstrap resampling on one
random day just as a small simulation. In 2015-07-20, JPEM went down by
-0.005505289, VGT went up by 0.00442037, SCH went down by -0.001932799,
XOM went down by -0.0102893, and USO went down by -0.0176574. Then we
set $100,000 as our initial wealth and ran the bootstrap resampling 5000
times to estimate the 4-week (20 trading day) value at risk of each of
your three portfolios at the 5% level. Each rows of the result of the
simulation represent simulated future and each columns represent 15000
different simulated values of final wealth of this portfolio after 20
days. The histogram below shows the wealth distribution of this
portfolio.

    # Sample a random return from the empirical joint distribution
    # This simulates a random day
    return.today = resample(all_returns, 1, orig.ids=FALSE)

    # Now simulate many different possible futures
    # just repeating the above block thousands of times
    initial_wealth = 100000
    sim1 = foreach(i=1:15000, .combine='rbind') %do% {
        total_wealth = initial_wealth
        weights = c(0.2, 0.2, 0.2, 0.2, 0.2)
        holdings = weights * total_wealth
        n_days = 20
        wealthtracker = rep(0, n_days)
        for(today in 1:n_days) {
            return.today = resample(all_returns, 1, orig.ids=FALSE)
            holdings = holdings + holdings*return.today
            total_wealth = sum(holdings)
            wealthtracker[today] = total_wealth
        }
        wealthtracker
    }
    # each row is a simulated trajectory (simulated future)
    # each column is a data 
    head(sim1)

    ##               [,1]      [,2]      [,3]      [,4]      [,5]      [,6]      [,7]
    ## result.1  98036.22  98050.17  94442.10  93968.82  94339.58  94197.48  96407.20
    ## result.2 100462.03 100432.12 101349.49 101850.79 100526.86 100580.55 100102.90
    ## result.3 100511.58 100167.71  99690.24 100052.60 100730.14 100558.96  99545.42
    ## result.4 100989.19 100981.59 101479.45 101760.84 102452.58 102743.78 101887.58
    ## result.5  98136.71  98417.60  98675.32 100240.24  99703.38 100968.43 100804.91
    ## result.6  99322.62  99129.73  99200.49  98925.89  99218.64  98662.56  98735.68
    ##               [,8]      [,9]     [,10]     [,11]     [,12]     [,13]     [,14]
    ## result.1  96665.42  93327.27  93542.73  92959.42  92595.37  93495.26  93006.85
    ## result.2  99250.83 100601.20 101356.84 102095.01 101252.69 101536.59 100286.40
    ## result.3  99863.86 101293.63 100953.93 100996.19 101413.48 100245.94  99458.65
    ## result.4 101587.63 101799.32 101401.31 100551.47 100614.57 100391.16  99973.24
    ## result.5 100357.58  99929.80 100786.42 100049.50 100100.93 100445.92 100186.07
    ## result.6  98601.88  96685.41  96270.02  96203.45  92636.84  92748.29  93422.44
    ##              [,15]     [,16]     [,17]     [,18]     [,19]     [,20]
    ## result.1  94109.68  93638.76  92595.84  93739.64  95049.81  94609.62
    ## result.2 101216.31 101707.48 101075.76  92367.66  88963.94  90367.73
    ## result.3  98930.66  98746.95 102442.48 101990.98 102003.55 102535.36
    ## result.4 101502.89 101243.54 100619.84 100544.56 100900.71  99534.60
    ## result.5 101459.46 100741.78 101582.30 102169.40 102589.35 102692.95
    ## result.6  93708.13  94213.85  95259.88  95833.99  95803.27  96979.98

    hist(sim1[,n_days], 25)

![](Figs/unnamed-chunk-2-1.png) As we expected from the graph above, we
are expecting to loss about 124.25 dollars with Value at Risk of
9322.883 dollars. This means that 5% of this simulated future has a loss
worse than 9322.883 dollars and the rest (95%) are better than losing
9322.883 dollars.

    # Profit/loss
    mean(sim1[,n_days]) # 99875.75

    ## [1] 99883.09

    mean(sim1[,n_days] - initial_wealth) #-124.2499

    ## [1] -116.9142

    hist(sim1[,n_days]- initial_wealth, breaks=30) #

![](Figs/unnamed-chunk-3-1.png)

    # 5% value at risk:
    quantile(sim1[,n_days]- initial_wealth, prob=0.05) # -9322.883 

    ##      5% 
    ## -9263.2

### Portfolio 2

Let’s contruct our second portfolio. This time, we used the following 6
ETFs: VNQ = Vanguard Real Estate Index Fund CPER = United States Copper
Index Fund RWO = SPDR DJ Wilshire Global Real Estate ETF ITB = iShares
U.S. Home Construction ETF XME = SPDR S&P Metals & Mining ETF XLK =
Technology Select Sector SPDR Fund

We chose these ETFs because we wanted to concentrate on real estate and
metal market. So we chose real estate ETF (VNQ), global real estate ETF
(RWO), buildings and construction ETF (ITB), copper ETF (CPER), metals
and mining (XME), and technology ETF (XLK). We extracted data from May
22, 2008. The plots below show more correlation between each ETFs than
that of the previous portfolio, except CPER which seems no correlation
between all the other ETFs.

    mystocks2 = c("VNQ", "CPER", "RWO", "ITB", "XME", "XLK")
    getSymbols(mystocks2, from="2008-05-22")

    ## pausing 1 second between requests for more than 5 symbols
    ## pausing 1 second between requests for more than 5 symbols

    ## [1] "VNQ"  "CPER" "RWO"  "ITB"  "XME"  "XLK"

    for(ticker in mystocks2) {
        expr = paste0(ticker, "a = adjustOHLC(", ticker, ")")
        eval(parse(text=expr))
    }

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query2.finance.yahoo.com/v7/finance/download/VNQ?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/VNQ?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/CPER?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=div&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query2.finance.yahoo.com/v7/finance/download/CPER?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/CPER?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query2.finance.yahoo.com/v7/finance/download/RWO?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/RWO?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query2.finance.yahoo.com/v7/finance/download/ITB?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/ITB?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query2.finance.yahoo.com/v7/finance/download/XME?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/XME?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query2.finance.yahoo.com/v7/finance/download/XLK?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/XLK?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    # Combine all the returns in a matrix
    all_returns2 = cbind(   ClCl(VNQa),
                                    ClCl(CPERa),
                                    ClCl(RWOa),
                                    ClCl(ITBa),
                                    ClCl(XMEa),
                                    ClCl(XLKa))
    all_returns2 = as.matrix(na.omit(all_returns2))

    # Compute the returns from the closing prices
    pairs(all_returns2)

![](Figs/unnamed-chunk-4-1.png) Here, we splitted the weights into 6
(0.166 per ETFs) and ran simulation using bootstrap resampling under the
same condition as before.

    # Now simulate many different possible futures
    # just repeating the above block thousands of times
    initial_wealth = 100000
    sim2 = foreach(i=1:15000, .combine='rbind') %do% {
        total_wealth = initial_wealth
        weights = c(0.166, 0.166, 0.166, 0.166, 0.166, 0.166)
        holdings = weights * total_wealth
        n_days = 20
        wealthtracker = rep(0, n_days)
        for(today in 1:n_days) {
            return.today = resample(all_returns2, 1, orig.ids=FALSE)
            holdings = holdings + holdings*return.today
            total_wealth = sum(holdings)
            wealthtracker[today] = total_wealth
        }
        wealthtracker
    }
    # each row is a simulated trajectory (simulated future)
    # each column is a data 
    head(sim2)

    ##               [,1]      [,2]      [,3]      [,4]      [,5]      [,6]      [,7]
    ## result.1 100022.15  99927.94 100864.63 101530.03 102648.60 102530.80 102426.49
    ## result.2  99683.81 101698.54 101773.78 102325.86 101144.81 101058.04 100662.72
    ## result.3 102077.47 101912.81 101894.30 100617.91 101069.48 100820.88 100465.41
    ## result.4 100294.49  98188.61  97808.62  97222.07  96199.93  98016.89  98111.28
    ## result.5 103216.11 103372.71 102736.02 102125.64 102684.81 101629.59 101507.42
    ## result.6  99741.22  99852.31 100394.01 100015.89 101338.43 100503.59  99028.64
    ##               [,8]      [,9]     [,10]     [,11]     [,12]     [,13]     [,14]
    ## result.1 101228.61 101950.27 102366.16 102501.05 102112.24 102155.51 102506.22
    ## result.2 102427.65 103270.76 103677.61 103086.58 102968.63 102127.84 101134.92
    ## result.3 101410.10 101363.38 101948.95 101013.54 100888.64 101089.20 101298.99
    ## result.4  98856.34  99034.08  98707.46  97322.41  97699.67 100591.39  99122.58
    ## result.5 101272.00 101101.95 104556.70 104849.70 104326.90 103592.13 104464.80
    ## result.6  99181.52  98524.87  99095.49  98812.77  98826.24  99303.91  99986.22
    ##              [,15]     [,16]     [,17]     [,18]     [,19]     [,20]
    ## result.1 102875.63 103522.13 104406.08 102284.16 103078.46 103402.16
    ## result.2 101422.42  99897.88 101340.05 101915.51 102000.69 102091.58
    ## result.3 101807.31 101234.07 101291.83 105156.24 104712.79 103991.78
    ## result.4  98995.88  99244.74  98264.31  98789.19  98844.03  96856.29
    ## result.5 103776.73 103379.79 103286.68 103042.97 103776.16 105245.19
    ## result.6 102438.52 102941.82 102636.98 102053.86 102879.99 102729.26

    hist(sim2[,n_days], 25)

![](Figs/unnamed-chunk-5-1.png) Now we are getting profit of 303.8911
dollars with value at risk 8028.351 dollars. This means that 5% of this
simulated future has a loss worse than 8028.351 dollars and the rest
(95%) are better than losing 8028.351 dollars.

    # Profit/loss
    mean(sim2[,n_days]) # 100303.9

    ## [1] 100444

    mean(sim2[,n_days] - initial_wealth) #303.8911

    ## [1] 443.9511

    hist(sim2[,n_days]- initial_wealth, breaks=30) 

![](Figs/unnamed-chunk-6-1.png)

    # 5% value at risk:
    quantile(sim2[,n_days]- initial_wealth, prob=0.05) # -8028.351 

    ##        5% 
    ## -7913.096

### Portfolio 3

Lastly, here is our thrid portfolio. This portfolio contains following 8
ETFs: VHT = Vanguard Healthcare ETF DBA = Invesco DB Agriculture Fund
PDBC = Invesco Optimum Yield Diversified Commodity Strategy No K-1 ETF
GNR = SPDR S&P Global Natural Resources ETF IJK = iShares S&P MidCap 400
Growth ETF PHO = Invesco Water Resources ETF FMAT = Fidelity MSCI
Materials Index ETF XLP = Consumer Staples Select Sector SPDR Fund

For this portfolio, we chose ETFs that are related to natural material
and biotech. When we did the same process as before and observed the
plot below, we could see that the ETFs most likely have positive
correlation between each other. Note that some pairs are showing almost
neutral correlation each other (such as VHT and DBA, VHT and PDBC, DBA
and GNR, etc…)

    mystocks3 = c("VHT", "DBA", "PDBC", "GNR", "IJK", "PHO", "FMAT", "XLP")
    getSymbols(mystocks3, from="2014-11-07")

    ## pausing 1 second between requests for more than 5 symbols
    ## pausing 1 second between requests for more than 5 symbols
    ## pausing 1 second between requests for more than 5 symbols
    ## pausing 1 second between requests for more than 5 symbols

    ## [1] "VHT"  "DBA"  "PDBC" "GNR"  "IJK"  "PHO"  "FMAT" "XLP"

    for(ticker in mystocks3) {
        expr = paste0(ticker, "a = adjustOHLC(", ticker, ")")
        eval(parse(text=expr))
    }

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query2.finance.yahoo.com/v7/finance/download/VHT?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/VHT?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query2.finance.yahoo.com/v7/finance/download/DBA?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=div&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/DBA?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/DBA?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query2.finance.yahoo.com/v7/finance/download/PDBC?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=div&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query2.finance.yahoo.com/v7/finance/download/PDBC?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/PDBC?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query2.finance.yahoo.com/v7/finance/download/GNR?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/GNR?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query2.finance.yahoo.com/v7/finance/download/IJK?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/IJK?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query2.finance.yahoo.com/v7/finance/download/PHO?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/PHO?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query2.finance.yahoo.com/v7/finance/download/FMAT?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/FMAT?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/XLP?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    ## Warning in read.table(file = file, header = header, sep = sep, quote
    ## = quote, : 'https://query1.finance.yahoo.com/v7/finance/download/XLP?
    ## period1=-2208988800&period2=1597708800&interval=1d&events=split&crumb=boe0syciCSS'에
    ## 서 readTableHeader에 의하여 발견된 완성되지 않은 마지막 라인입니다

    # Combine all the returns in a matrix
    all_returns3 = cbind(   ClCl(VHTa),
                                    ClCl(DBAa),
                                    ClCl(PDBCa),
                                    ClCl(GNRa),
                                    ClCl(IJKa),
                                    ClCl(PHOa),
                                    ClCl(FMATa),
                                    ClCl(XLPa))
    all_returns3 = as.matrix(na.omit(all_returns3))

    # Compute the returns from the closing prices
    pairs(all_returns3)

![](Figs/unnamed-chunk-7-1.png) Since we had 8 ETFs, we equally splitted
the weights for each ETFs (0.125) and ran the simulation using bottstrap
resampling 15000 times.

    initial_wealth = 100000
    sim3 = foreach(i=1:15000, .combine='rbind') %do% {
        total_wealth = initial_wealth
        weights = c(0.125, 0.125, 0.125, 0.125, 0.125, 0.125, 0.125, 0.125)
        holdings = weights * total_wealth
        n_days = 20
        wealthtracker = rep(0, n_days)
        for(today in 1:n_days) {
            return.today = resample(all_returns3, 1, orig.ids=FALSE)
            holdings = holdings + holdings*return.today
            total_wealth = sum(holdings)
            wealthtracker[today] = total_wealth
        }
        wealthtracker
    }
    # each row is a simulated trajectory (simulated future)
    # each column is a data 
    head(sim3)

    ##               [,1]      [,2]      [,3]      [,4]      [,5]      [,6]      [,7]
    ## result.1  99837.19  99790.89 100304.74 100449.02 101531.96 101137.00 101303.17
    ## result.2 100036.18 100417.71 100308.93 100779.89 100723.28 100676.37 100611.70
    ## result.3 101486.06 100605.89 100512.71 100012.53 100390.05 100081.17 100170.92
    ## result.4 100503.44 100214.87 100211.08 100592.47  99395.42  99580.12 101426.62
    ## result.5  99293.59  98673.01  99088.33  98575.06  98249.24 106075.93 106301.88
    ## result.6 100209.56  99940.55 100107.20  98102.01  97848.86  96977.14  97163.82
    ##               [,8]      [,9]     [,10]     [,11]     [,12]     [,13]     [,14]
    ## result.1 101514.20 102217.38 102710.40 101930.96 102077.40 102097.12 102235.61
    ## result.2 101338.36  98859.15  98799.73  96307.17  96760.81  97302.24  97428.12
    ## result.3 100263.35  99701.57  99729.20  99320.08  99689.96  99556.00  99955.65
    ## result.4  98311.02  98108.83  97573.88  98233.18  96012.15  93576.75  91871.39
    ## result.5 103998.39 103187.87 104318.20 104044.81 105010.73 103583.05 104164.50
    ## result.6  96720.67  95710.80  96096.50  97224.74  98059.54  97817.00  98158.16
    ##              [,15]     [,16]     [,17]     [,18]     [,19]     [,20]
    ## result.1 102950.69 102521.15 102540.67 102281.62 102973.40 101248.79
    ## result.2  96625.39  98073.10  98468.64  98837.48  99260.55  97896.41
    ## result.3  98577.11  97858.08  97583.26  98275.36 101637.53 100206.44
    ## result.4  91151.36  90851.27  88648.98  87590.51  87933.75  88082.37
    ## result.5 104372.87 104108.19 103783.03 103693.82 102428.99 100927.14
    ## result.6  98010.66  97339.71  96813.91  96452.32  96417.66  95977.24

    hist(sim3[,n_days], 25)

![](Figs/unnamed-chunk-8-1.png) Our thrid portfolio shows mean of
100358.8 dollars, indicating 358.8479 dollars profit with value at risk
6844.874 dollars. This means that 5% of this simulated future has a loss
worse than 6844.874 dollars and the rest (95%) are better than losing
6844.874 dollars.

    # Profit/loss
    mean(sim3[,n_days]) # 100358.8

    ## [1] 100411.6

    mean(sim3[,n_days] - initial_wealth) #358.8479

    ## [1] 411.6338

    hist(sim3[,n_days]- initial_wealth, breaks=30) 

![](Figs/unnamed-chunk-9-1.png)

    # 5% value at risk:
    quantile(sim3[,n_days]- initial_wealth, prob=0.05) # -6844.874 

    ##        5% 
    ## -6800.019

To sum up, we could get these results from our three portfolios:
Portfolio 1 (5 random ETFs): loss = $124.2499, VaR = $9322.883 Portfolio
2 (6 related ETFs): profit = $303.8911, VaR = $8028.351 Portfolio 3 (8
related ETFs): profit = $358.8479, VaR = $6844.874

In conclusion, throughout our three simulations utilzing bootstrap
resampling technique, we discovered that choosing random (unrelated)
ETFs is definitely not profitable choice. While some might claim that
splitting ETFs into various unrelated assets of ETF is profitable way
because of its wide range of ETFs, our simulation denies that notion.
Rather, our simulations indicate that choosing related ETFs in fact
gives better results and profit. Also note that the VaR has gotten low
as we added more related ETFs. Therefore, we could conclude that
inverting into related ETFs is the better way of getting profit with low
VaR than investing into random ETFs.

Market segmentation
-------------------

### Data Cleaning

We divided columns by relevant interests. For example, we gathered sport
columns like “sports\_fandom”, “sports\_playing” and “personal
training”. This results more sorted data set by their relevant
interests.

    library(ggplot2)
    library(LICORS)  # for kmeans++
    library(foreach)
    library(mosaic)
    library(tidyverse)

    ## ─ Attaching packages ────────────────────────────────────────── tidyverse 1.3.0 ─

    ## ✓ tibble  3.0.3     ✓ purrr   0.3.4
    ## ✓ tidyr   1.1.0     ✓ stringr 1.4.0
    ## ✓ readr   1.3.1     ✓ forcats 0.5.0

    ## ─ Conflicts ──────────────────────────────────────────── tidyverse_conflicts() ─
    ## x purrr::accumulate()        masks foreach::accumulate()
    ## x mosaic::count()            masks dplyr::count()
    ## x purrr::cross()             masks mosaic::cross()
    ## x mosaic::do()               masks dplyr::do()
    ## x tidyr::expand()            masks Matrix::expand()
    ## x dplyr::filter()            masks stats::filter()
    ## x xts::first()               masks dplyr::first()
    ## x ggstance::geom_errorbarh() masks ggplot2::geom_errorbarh()
    ## x dplyr::lag()               masks stats::lag()
    ## x xts::last()                masks dplyr::last()
    ## x tidyr::pack()              masks Matrix::pack()
    ## x mosaic::stat()             masks ggplot2::stat()
    ## x mosaic::tally()            masks dplyr::tally()
    ## x tidyr::unpack()            masks Matrix::unpack()
    ## x purrr::when()              masks foreach::when()

    data <- read.csv("social_marketing.csv")
    # reorder the columns
    sns <- data[, -6]
    sns$uncategorized <- data[, 6]

    data2 <- read.csv("social_marketing.csv", row.names = 1)
    sns_reorder <- data2[, c(1,2,4,29, 9,10,15,28, 18,8, 30,16, 32,27,23,14, 6,17,31, 20,13,24, 3,22,19, 21,33, 12,7,5, 25,11, 26, 34,35,36)]

Before we dive into data analysis, let’s first see the total
distribution across the interests. Note that “chatter” is the highest,
followed by “photo\_sharing”. This is a straightforward information
since most of posts in Twitter can be fall into these two categories.
One interesting aspect is that “health\_nutrition” is the highest except
“chatter” and “photo\_sharing”. This roughly indicates that many of the
brand’s followers are interested in health and nutrient. Maybe that was
the reason why they followed the brand NutrientH20, which our group
guessed as nutrition brand as the name of the brand indicates.

    par(mar=c(11,4,4,4))
    barplot(colSums(sns_reorder), horiz=TRUE, xlim=c(0, 40000), main="Total Distribution Across the Interests", col=rainbow(36), cex.names=0.5, axis.lty=1, las=2)

![](Figs/unnamed-chunk-11-1.png) \#\#\# PCA The picture below shows our
group’s definition of market segmentation. We divided each related
interests into separate groups. For example, we gathered “family”,
"home\_&\_garden“,”health\_nutrition“, and”parenting" as family-related
group. We also gathered “travel”, “eco”, and “outdoor” as travel-related
group. There are 13 clusters in total in our drawing. Note that this is
mere a rough-draft of our entire process. We thought this drawing gives
nice overview of our 36 interests in the dataset. ![Rough Drawing of
Market
Segmentaion](/Users/macintosh/Documents/R%20studio/ourmarketsegmentation.jpeg)

In order to perform PCA, we first measured means of all interests and
created a new data frame. Then we created a correlation matrix to see
overall correlation between each interests in our data set. Although the
matrix shows not many correlation, there are some strong positive
correlation which indicates that we could reduce the dimensionality.
Interestingly enough, we could observe that some of our “prediction” of
above drawing actually are represented in below correlation matrix. For
example, “politics” has strong correlation with “news” and “beauty” has
strong correlation with fashion. However, there are some correlations
that we did not expect: “food”, “sports\_fandom”, “religion” and
“parenting”, and “travel” and “politics”. Recall that this data was
achieved from human annotators. Such unexpected correlation might be
influenced by inevitable error by annotators.

    sns_results = sns %>%
        group_by(X) %>% 
        summarize_all(mean) %>% 
      column_to_rownames(var="X")

    # a look at the correlation matrix
    head(cor(sns_results))

    ##                   chatter current_events      travel photo_sharing    tv_film
    ## chatter        1.00000000     0.15621116  0.01466681    0.53626660 0.01289863
    ## current_events 0.15621116     1.00000000  0.05094616    0.14595286 0.07767346
    ## travel         0.01466681     0.05094616  1.00000000    0.02406795 0.09698995
    ## photo_sharing  0.53626660     0.14595286  0.02406795    1.00000000 0.02117091
    ## tv_film        0.01289863     0.07767346  0.09698995    0.02117091 1.00000000
    ## sports_fandom  0.01439263     0.06178037 -0.00870919    0.01992100 0.03075880
    ##                sports_fandom   politics         food     family home_and_garden
    ## chatter           0.01439263 0.05144838 -0.004704080 0.07917038      0.07015760
    ## current_events    0.06178037 0.06828273  0.059767526 0.06336701      0.05351146
    ## travel           -0.00870919 0.66021000  0.075142216 0.01753476      0.04093187
    ## photo_sharing     0.01992100 0.03976700  0.006802181 0.09858794      0.08395511
    ## tv_film           0.03075880 0.03225454  0.080683325 0.02177639      0.10659105
    ## sports_fandom     1.00000000 0.06709790  0.532638366 0.43781038      0.08482199
    ##                     music         news online_gaming   shopping
    ## chatter        0.09131777 -0.001163561   0.004784789 0.58337322
    ## current_events 0.07236614  0.060284226  -0.001645689 0.15014362
    ## travel         0.03864032  0.250616947   0.013222873 0.01990778
    ## photo_sharing  0.14618817 -0.011980028   0.037234010 0.53562102
    ## tv_film        0.27483223  0.067440558   0.035331802 0.04162464
    ## sports_fandom  0.05453751  0.200289676   0.024760877 0.02626127
    ##                health_nutrition college_uni sports_playing      cooking
    ## chatter             0.003727738  0.03399144     0.06107395 0.0020816423
    ## current_events      0.019863015  0.03095266     0.03072078 0.0467164788
    ## travel             -0.011922499  0.05383514     0.05496195 0.0175974884
    ## photo_sharing       0.034804791  0.06149484     0.09869699 0.3605909943
    ## tv_film            -0.001790684  0.20421826     0.10326318 0.0006017955
    ## sports_fandom      -0.011229255  0.02645641     0.07104991 0.0076921174
    ##                       eco    computers   business     outdoors     crafts
    ## chatter        0.15511774  0.072489571 0.16610690 -0.006597319 0.11174145
    ## current_events 0.07690347  0.054824859 0.07458087  0.017898948 0.07372363
    ## travel         0.06143429  0.602934879 0.16184567  0.027133231 0.08695379
    ## photo_sharing  0.17341168  0.093000186 0.17863635  0.032783874 0.11094571
    ## tv_film        0.06282547 -0.005485945 0.10114738  0.028928541 0.18468945
    ## sports_fandom  0.08585083  0.050633295 0.06813277  0.062217647 0.20118860
    ##                 automotive          art     religion     beauty   parenting
    ## chatter         0.13376735 -0.005076772 -0.023111699 0.02636423  0.02074252
    ## current_events  0.07244481  0.053477246  0.067694509 0.07011221  0.05023716
    ## travel         -0.00278411  0.086394257  0.063933064 0.01256552  0.04234113
    ## photo_sharing   0.11524903  0.024752344  0.003299888 0.31796590  0.04116965
    ## tv_film         0.02050753  0.498771827  0.045027564 0.01678311 -0.00178809
    ## sports_fandom   0.23964647  0.022319534  0.637974843 0.12286324  0.60771812
    ##                     dating     school personal_fitness    fashion
    ## chatter        0.184452453 0.11667862     0.0327477067 0.06331429
    ## current_events 0.031045863 0.06804713     0.0383886537 0.05590622
    ## travel         0.086756030 0.02219954    -0.0052992453 0.02601565
    ## photo_sharing  0.028511721 0.10620924     0.0625236821 0.34724880
    ## tv_film        0.004170894 0.02502227    -0.0004447435 0.01760887
    ## sports_fandom  0.016925530 0.49310619     0.0142720768 0.03076729
    ##                small_business         spam        adult uncategorized
    ## chatter            0.11673062  0.004603242  0.015372712  0.0669934396
    ## current_events     0.06549793  0.019402989  0.016764279  0.0296742259
    ## travel             0.11695071  0.022773349  0.020244743  0.0308655618
    ## photo_sharing      0.13811239 -0.008664858 -0.012707084  0.0963980989
    ## tv_film            0.18879824 -0.004210646 -0.021700249  0.1632789878
    ## sports_fandom      0.04866224  0.008957464  0.007986164 -0.0005287314

    # looks a mess -- reorder the variables by hierarchical clustering
    ggcorrplot::ggcorrplot(cor(sns_results), title="Correlation Plot", type="lower", hc.order = TRUE)

![](Figs/unnamed-chunk-12-1.png) We performed PCA and created the
variance plot of each PCs. Obviously, the first PC has the highest
variance while others share somewhat similar behaviors.

    # Now look at PCA of the (average) survey responses.  
    # This is a common way to treat survey data
    PCAsns = prcomp(sns_results, scale=TRUE)

    ## variance plot
    plot(PCAsns)

![](Figs/unnamed-chunk-13-1.png)

    #summary(PCAsns)

We checked the number of PCs by creating an elbow plot. The elbow plot
below shows the knee around 11 PCs. So we could narrow our 36 PCs down
to 11 PCs.

    # std dev of each PCs
    std_dev <- PCAsns$sdev

    # Variances of each PCs
    pca_var <- std_dev^2
    # check first 10 variance
    pca_var[1:10]

    ##  [1] 4.488436 2.884020 2.540463 2.354914 2.191213 1.873759 1.653216 1.422705
    ##  [9] 1.325425 1.143411

    # We want to find the components which explain the maximum variance.
    # Higher variance retains more information 

    # To compute the proportion of variance explained by each component, 
    # we simply divide the variance by sum of total variance.

    # proportion of variance explained
    prop_var <- pca_var / sum(pca_var)
    prop_var[1:10]

    ##  [1] 0.12467878 0.08011168 0.07056843 0.06541427 0.06086704 0.05204886
    ##  [7] 0.04592267 0.03951959 0.03681735 0.03176140

    plot(prop_var, xlab = "Principal Component",
                 ylab = "Proportion of Variance Explained",
                 type = "b")

![](Figs/unnamed-chunk-14-1.png)

    # create a tidy summary of the loadings
    loadings_summary = PCAsns$rotation %>%
      as.data.frame() %>%
      rownames_to_column('Interest')

    loadings_summary %>%
      select(Interest, PC1) %>%
      arrange(desc(PC1))

    ##            Interest        PC1
    ## 1          religion 0.29709999
    ## 2              food 0.29690952
    ## 3         parenting 0.29400412
    ## 4     sports_fandom 0.28773177
    ## 5            school 0.28063791
    ## 6            family 0.24426866
    ## 7            beauty 0.20151836
    ## 8            crafts 0.19362762
    ## 9           cooking 0.18880850
    ## 10          fashion 0.18388185
    ## 11    photo_sharing 0.18027952
    ## 12              eco 0.14533561
    ## 13        computers 0.14333124
    ## 14         outdoors 0.14260424
    ## 15 personal_fitness 0.13750109
    ## 16         business 0.13501004
    ## 17         shopping 0.13299500
    ## 18       automotive 0.13132522
    ## 19         politics 0.13026617
    ## 20   sports_playing 0.13021653
    ## 21             news 0.12764328
    ## 22          chatter 0.12599239
    ## 23 health_nutrition 0.12420109
    ## 24            music 0.12408921
    ## 25   small_business 0.11904181
    ## 26           travel 0.11664903
    ## 27  home_and_garden 0.11576501
    ## 28           dating 0.10515646
    ## 29              art 0.09794933
    ## 30          tv_film 0.09745666
    ## 31   current_events 0.09723669
    ## 32    uncategorized 0.09443507
    ## 33      college_uni 0.09415672
    ## 34    online_gaming 0.07388979
    ## 35            adult 0.02673097
    ## 36             spam 0.01146092

    loadings_summary %>%
      select(Interest, PC2) %>%
      arrange(desc(PC2))

    ##            Interest          PC2
    ## 1     sports_fandom  0.316923635
    ## 2          religion  0.316152778
    ## 3         parenting  0.295082234
    ## 4              food  0.237808675
    ## 5            school  0.197572367
    ## 6            family  0.196253208
    ## 7              news  0.036198891
    ## 8        automotive  0.031564108
    ## 9            crafts  0.021623185
    ## 10            adult  0.006918154
    ## 11             spam  0.004551609
    ## 12         politics -0.013939964
    ## 13        computers -0.037334899
    ## 14           travel -0.039947269
    ## 15  home_and_garden -0.046803486
    ## 16              art -0.060347094
    ## 17   current_events -0.064036499
    ## 18           dating -0.071535239
    ## 19          tv_film -0.079352508
    ## 20    online_gaming -0.083591578
    ## 21              eco -0.085321972
    ## 22   small_business -0.094048059
    ## 23         business -0.098782574
    ## 24   sports_playing -0.108595355
    ## 25         outdoors -0.113581774
    ## 26      college_uni -0.115959664
    ## 27            music -0.144259544
    ## 28 personal_fitness -0.144611756
    ## 29    uncategorized -0.146498856
    ## 30 health_nutrition -0.146577761
    ## 31          chatter -0.197225501
    ## 32           beauty -0.208609941
    ## 33         shopping -0.209852847
    ## 34          fashion -0.279799725
    ## 35    photo_sharing -0.303077634
    ## 36          cooking -0.314287972

### K Means Clustering

Before we perform K-Means Clustering, we scaled our PCA values and
created an elbow plot for the right number of K. Among 20 Ks, the elbow
plot shows a knee near when K equals 12. Interestingly enough, this was
very close to what we roughly predicted when we drew the picture above.
Although the correlation matrix showed some unexpected correlation, we
thought this was interesting fact to note.

    X <- as.data.frame(PCAsns$x[, 1:11])

    sns_scaled = scale(X, center=TRUE, scale=TRUE)

    k_grid = seq(2, 20, by=1)
    SSE_grid = foreach(k = k_grid, .combine="c") %do%{
      cluster_k = kmeans(sns_scaled, k, nstart=50)
      cluster_k$tot.withinss
    }

    plot(k_grid, SSE_grid)

![](Figs/unnamed-chunk-16-1.png) We then performed K-Means Clustering
with 25 different random initializations. The table below shows the
centers of the clusters.

    # Extract the centers and scales from the rescaled data (which are named attributes)
    mu = attr(sns_scaled,"scaled:center")
    sigma = attr(sns_scaled,"scaled:scale")

    # Run k-means with 6 clusters and 25 starts
    clust1 = kmeans(sns_scaled, 13, nstart=25)
    # 25 different random initialization and the result of the algorithm is the best of those 25 so it's like running a tournament of 25 different random

    # What are the clusters?
    clust1$center[1,]*sigma + mu

    ##         PC1         PC2         PC3         PC4         PC5         PC6 
    ##  0.20675215 -1.04067474  0.24492287 -0.73389367  1.21998331 -2.16830633 
    ##         PC7         PC8         PC9        PC10        PC11 
    ##  0.48388056 -0.24443676 -0.11784886  0.28832815  0.08627613

    #clust1$center[2,]*sigma + mu
    #clust1$center[4,]*sigma + mu

We also tried K Means++, but its sum of within-cluster sum of squares is
actually higher and its between-cluster sum of squares is lower than
regular K Means. So we decided to stick with regular K Means clustering
as our model.

    # Using kmeans++ initialization
    clust2 = kmeanspp(sns_scaled, k=13, nstart=25)

    qplot(chatter, health_nutrition, data=sns_reorder, color=factor(clust2$cluster))

![](Figs/unnamed-chunk-18-1.png)

    qplot(college_uni, school, data=sns_reorder, color=factor(clust2$cluster))

![](Figs/unnamed-chunk-18-2.png)

    # Compare versus within-cluster average distances from the first run
    clust1$withinss

    ##  [1] 3497.035 3410.373 4606.995 2640.571 1528.304 2820.600 2252.921 1696.195
    ##  [9] 3412.800 2457.576 3251.999 3149.200 1824.281

    clust2$withinss

    ##  [1] 2768.9192 1827.5151 3736.6997 2236.0410  834.8267 3432.7271 3174.1933
    ##  [8] 2450.8734 6333.9326 2144.0377 1176.6322 2646.1040 3377.7068

    sum(clust1$withinss)

    ## [1] 36548.85

    sum(clust2$withinss)

    ## [1] 36140.21

    clust1$tot.withinss

    ## [1] 36548.85

    clust2$tot.withinss

    ## [1] 36140.21

    clust1$betweenss

    ## [1] 50142.15

    clust2$betweenss

    ## [1] 50550.79

Now we plotted the result as shown below. All plots share similar
behavior: It looks like other clusters are moving towards the cluster 1.
Below is the plot of PC1 and PC2.

    # plot
    qplot(PC1, PC2, data=X, color=factor(clust1$cluster))

![](Figs/unnamed-chunk-19-1.png) Below is the plot of PC2 and PC3

    qplot(PC2, PC3, data=X, color=factor(clust1$cluster))

![](Figs/unnamed-chunk-20-1.png) Below is the plot of PC3 and PC4

    qplot(PC3, PC4, data=X, color=factor(clust1$cluster))

![](Figs/unnamed-chunk-21-1.png)

    qplot(PC4, PC5, data=X, color=factor(clust1$cluster))

![](Figs/unnamed-chunk-22-1.png)

    for (i in seq(1:13)) {
      print(paste("Number of Cluster ", i, ": ", length(which(clust1$cluster == i))))
    }

    ## [1] "Number of Cluster  1 :  856"
    ## [1] "Number of Cluster  2 :  607"
    ## [1] "Number of Cluster  3 :  2243"
    ## [1] "Number of Cluster  4 :  349"
    ## [1] "Number of Cluster  5 :  84"
    ## [1] "Number of Cluster  6 :  468"
    ## [1] "Number of Cluster  7 :  274"
    ## [1] "Number of Cluster  8 :  222"
    ## [1] "Number of Cluster  9 :  701"
    ## [1] "Number of Cluster  10 :  351"
    ## [1] "Number of Cluster  11 :  1046"
    ## [1] "Number of Cluster  12 :  461"
    ## [1] "Number of Cluster  13 :  220"

Author Attribution
------------------

For this problem, we utilized “tm” library for reading our text data
sets. The “readPlain” function reads in English texts so that we can
work on it in our R studio enviroment. Then we loaded our C50train data
set by “Sys.glob” function. This function allows us to load all the data
we need inside the C50train folder. After that, we had 50 training
article data (2500 in total). We then cleaned up the file names by using
“strsplit” function so that our file names look like
“AaronPressman106247newsML.txt”. We used “VectorSource” function in
order to create a vector source of our data. Then we used “Corpus”
function so that we can make kind of a dataframe that contains 2500
articles.

    install.packages('tm', repos="http://cran.us.r-project.org")

    ## 
    ## The downloaded binary packages are in
    ##  /var/folders/w3/z6pvwvds5mz40qs1b6y0xlb00000gn/T//RtmptFN160/downloaded_packages

    install.packages('e1071', repos="http://cran.us.r-project.org")

    ## 
    ## The downloaded binary packages are in
    ##  /var/folders/w3/z6pvwvds5mz40qs1b6y0xlb00000gn/T//RtmptFN160/downloaded_packages

    install.packages('gmodels', repos="http://cran.us.r-project.org")

    ## 
    ## The downloaded binary packages are in
    ##  /var/folders/w3/z6pvwvds5mz40qs1b6y0xlb00000gn/T//RtmptFN160/downloaded_packages

    library(tm) 

    ## Loading required package: NLP

    ## 
    ## Attaching package: 'NLP'

    ## The following object is masked from 'package:ggplot2':
    ## 
    ##     annotate

    ## 
    ## Attaching package: 'tm'

    ## The following object is masked from 'package:mosaic':
    ## 
    ##     inspect

    library(tidyverse)
    library(slam)
    library(proxy)

    ## 
    ## Attaching package: 'proxy'

    ## The following object is masked from 'package:Matrix':
    ## 
    ##     as.matrix

    ## The following objects are masked from 'package:stats':
    ## 
    ##     as.dist, dist

    ## The following object is masked from 'package:base':
    ## 
    ##     as.matrix

    library(tidyr)
    library(glmnet)

    ## Loaded glmnet 4.0-2

    library(e1071) 
    library(gmodels)
    library(caret)

    ## 
    ## Attaching package: 'caret'

    ## The following object is masked from 'package:purrr':
    ## 
    ##     lift

    ## The following object is masked from 'package:mosaic':
    ## 
    ##     dotPlot

    readerPlain = function(fname){
                    readPlain(elem=list(content=readLines(fname)), 
                                id=fname, language='en') }
                            
    ## Test it on Adam Smith
    #adam = readerPlain("/Users/macintosh/Documents/R studio/division_of_labor.txt")
    #adam
    #meta(adam)
    #content(adam)

    # load all 50 training articles (2500 total)
    fileNames <- Sys.glob("/Users/macintosh/Documents/R studio/ReutersC50/C50train/*/*.txt")
    articles_train = lapply(fileNames, readerPlain)
    #fileNames

    # Clean up the file names
    mynames = fileNames %>%
        { strsplit(., '/', fixed=TRUE) } %>%
        { lapply(., tail, n=2) } %>%
        { lapply(., paste0, collapse = '') } %>%
        unlist

    # Rename the articles
    #author_names <- c()

    #for (i in seq(1, length(fileNames))){
    #  name <- strsplit(fileNames[i], split = "/")[[1]][8]
    #  author_names <- append(author_names, name)
    #}
    #mynames
    names(articles_train) = mynames 

    documents_raw = Corpus(VectorSource(articles_train))

For preprocessing and tokenization steps, we utilized
“content\_transformer” function to remove numbers, punctuation, excess
white-spaces, and converting everything into lowercase. Then we used
“tm\_map” to map these into the corpus dataframe.

    ## Some pre-processing/tokenization steps.
    ## tm_map just maps some function to every document in the corpus
    my_documents = documents_raw %>%
      tm_map(content_transformer(tolower))  %>%             # make everything lowercase
      tm_map(content_transformer(removeNumbers)) %>%        # remove numbers
      tm_map(content_transformer(removePunctuation)) %>%    # remove punctuation
      tm_map(content_transformer(stripWhitespace))          # remove excess white-space

    ## Warning in tm_map.SimpleCorpus(., content_transformer(tolower)): transformation
    ## drops documents

    ## Warning in tm_map.SimpleCorpus(., content_transformer(removeNumbers)):
    ## transformation drops documents

    ## Warning in tm_map.SimpleCorpus(., content_transformer(removePunctuation)):
    ## transformation drops documents

    ## Warning in tm_map.SimpleCorpus(., content_transformer(stripWhitespace)):
    ## transformation drops documents

Then we removed stopwords. Among two built-in stopwords, we decided to
use “en” which is just basic English stopwords.

    my_documents = tm_map(my_documents, content_transformer(removeWords), stopwords("en"))

    ## Warning in tm_map.SimpleCorpus(my_documents, content_transformer(removeWords), :
    ## transformation drops documents

We created a doc-term-matrix from the corpus. This matrix shows 99%
sparsity which indicates that there are 99% of data which are zeros.

    DTM_train = DocumentTermMatrix(my_documents)
    DTM_train # some basic summary statistics

    ## <<DocumentTermMatrix (documents: 2500, terms: 32571)>>
    ## Non-/sparse entries: 540361/80887139
    ## Sparsity           : 99%
    ## Maximal term length: 46
    ## Weighting          : term frequency (tf)

We explored some functions for the doc-term-matrix from the corpus such
as “inspect”, “findFreqTerms”, and “findAssocs”. We used word “genetic”
that we used in our class for finding association terms.

    inspect(DTM_train)

    ## <<DocumentTermMatrix (documents: 2500, terms: 32571)>>
    ## Non-/sparse entries: 540361/80887139
    ## Sparsity           : 99%
    ## Maximal term length: 46
    ## Weighting          : term frequency (tf)
    ## Sample             :
    ##       Terms
    ## Docs   billion character company market million new percent said will year
    ##   111        0         4       0      3       2   3       0    6    4    1
    ##   130        0         4       1      1       5   0       2    1    1    4
    ##   142        3         4       1      3       1   2       1    9    6    8
    ##   2127       4         4       1      2       0   7       7    5   11    7
    ##   2133       2         4       0      1       0   0       5    7    3    4
    ##   2139       0         4       1      7       0   1      14   23    9    2
    ##   2140       4         4       0      0       0   2       3   12   15    3
    ##   599        1         4       5     11       0   0       0   16    1    2
    ##   763        0         4       0      4       0   3       0   20    3   10
    ##   766        0         4       0      7       0   4       0   20    4   10

    head(findFreqTerms(DTM_train, 50))

    ## [1] "access"    "accounts"  "agencies"  "alliance"  "also"      "announced"

    findAssocs(DTM_train, "genetic", .5)

    ## $genetic
    ##            abi          tests       athritis        cancers         cystic 
    ##           0.97           0.91           0.87           0.87           0.87 
    ##       diabetes      disorders      dystrophy     rheumatoid     underclass 
    ##           0.87           0.87           0.87           0.87           0.87 
    ##       genetics    detrimental      actuaries        defects         insure 
    ##           0.86           0.76           0.74           0.73           0.71 
    ##     expectancy       fibrosis       diagnose susceptibility     lifestyles 
    ##           0.71           0.71           0.71           0.71           0.71 
    ##    commonplace        infancy     profession       chadwick     euroscreen 
    ##           0.71           0.69           0.62           0.56           0.56 
    ##     geneticist     hereditary    huntingtons        payoffs predisposition 
    ##           0.56           0.56           0.56           0.56           0.56 
    ##      twitching    untreatable         makeup      undergone        testing 
    ##           0.56           0.56           0.55           0.55           0.52 
    ##        wishing 
    ##           0.50

As our final preprocessing step, we removed the terms that have low
frequency (removing the “long tail”). We utilized “removeSparseTerms” to
remove any sparse terms in out document-term matrix. We set the maximal
allowed sparsity of 95%. Such reduced our terms into 802 terms instead
of about 32571 terms. Then we built TF IDF weights matrix as our final
step for data analysis.

    DTM_train = removeSparseTerms(DTM_train, 0.95)
    DTM_train 

    ## <<DocumentTermMatrix (documents: 2500, terms: 802)>>
    ## Non-/sparse entries: 283186/1721814
    ## Sparsity           : 86%
    ## Maximal term length: 24
    ## Weighting          : term frequency (tf)

    # construct TF IDF weights -- might be useful if we wanted to use these
    # as features in a predictive model
    tfidf_train = weightTfIdf(DTM_train)

PCA
---

Before we dive into the model, we decided to do PCA in order to reduce
the dimensionality of our data set. We dropped all zeros in order to
make our process smooth. The “prcomp” function automatically chose 785
(columns) rather than 2500 (rows) because it automatically chooses the
lower number between the two.

    # Now PCA on term frequencies
    tfidf_matix = as.matrix(tfidf_train) # make it into a matrix since prcomp requires matrix format. 
    summary(colSums(tfidf_matix))

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   0.000   4.514   6.029   6.749   8.111  29.607

    scrub_cols = which(colSums(tfidf_matix) == 0) # drops all zeros
    tfidf_matix = tfidf_matix[,-scrub_cols]

    pca_train = prcomp(tfidf_matix, scale=TRUE) # since without "rank" parameter, it automatically select the lower value btw nrow and ncol. 
    #summary(pca_train) 

    # Look at the loadings
    pca_train$rotation[order(abs(pca_train$rotation[,1]),decreasing=TRUE),1][1:25]

    ##     beijing       china     chinese      chinas       share     million 
    ## -0.14235799 -0.13615984 -0.12356205 -0.11744223  0.11622822  0.11419658 
    ##    analysts    earnings     quarter     percent      leader     analyst 
    ##  0.11090428  0.10930980  0.10907596  0.10539498 -0.10444837  0.10433585 
    ##    beijings     profits      profit        hong   political   communist 
    ## -0.10364432  0.10280410  0.10188136 -0.09821782 -0.09714371 -0.09647188 
    ##      cchina    official        kong   officials        rose  government 
    ## -0.09445094 -0.09358866 -0.09343287 -0.09332476  0.09036083 -0.08974060 
    ##       human 
    ## -0.08837110

    pca_train$rotation[order(abs(pca_train$rotation[,2]),decreasing=TRUE),2][1:25]

    ##               corp     communications                new          companies 
    ##        -0.11798420        -0.11317581        -0.11192299        -0.10817292 
    ##            company               deal               will           internet 
    ##        -0.10792766        -0.10029516        -0.09955620        -0.09784312 
    ##           forecast            beijing             chinas          customers 
    ##         0.09702771         0.09683071         0.09579163        -0.09483727 
    ##            percent           services             profit telecommunications 
    ##         0.09258526        -0.09093179         0.09046046        -0.08908398 
    ##            network              china            chinese                inc 
    ##        -0.08885564         0.08837686         0.08751040        -0.08571284 
    ##           industry           networks            results               rise 
    ##        -0.08515680        -0.08412059         0.08377678         0.08367041 
    ##            figures 
    ##         0.08272540

As expected, the graph below shows that the first component is the
highest. However, the components after the first component are gradually
decreasing. This is because our data set is so big that the components
after the first component don’t have much difference. In other words,
the weight distribution of each components are small compared to that of
the example in our class which has total 50 components.

    head(pca_train$x[,1:2])

    ##     
    ## Docs       PC1       PC2
    ##    1 -1.168643 -4.453972
    ##    2 -1.437397 -4.909173
    ##    3 -1.962232 -2.241976
    ##    4 -3.245998 -3.010290
    ##    5 -2.652355 -3.571162
    ##    6 -2.060551 -2.374588

    # plot PCA components' variances 
    plot(pca_train)

![](Figs/unnamed-chunk-31-1.png) The graph below looks very messy. This
is happening because we are trying to represent the whole data using
only the first and second components. Since there are 785 components in
total, the significance of the first and second components are
comparably small.

    plot(pca_train$x[,1:2], xlab="PCA 1 direction", ylab="PCA 2 direction", bty="n",
         type='n'); text(pca_train$x[,1:2], labels = 1:length(articles_train), cex=0.5)

![](Figs/unnamed-chunk-32-1.png)

    # Let's check 2002 and 2036 -> looks like the article is about communications
    content(articles_train[[2002]])

    ##  [1] "An obscure part of the new telecommunications law could restrict how phone companies use confidential customer data to peddle everything from calling plans and caller I.D. to Internet access and credit cards."                                                                                               
    ##  [2] "The law pits consumer advocates who fear an onslaught of telemarketers and a loss of personal privacy against local, long-distance and cellular carriers wanting to offer their customers one-stop shopping in the new communications age."                                                                     
    ##  [3] "The data, which include billing records and calling patterns, are taking on added importance as local and long-distance companies, cable-TV operators and others brace to get into each other's business under the new telecom law."                                                                            
    ##  [4] "\"Everybody wants to use these data -- subject to the law -- for their marketing efforts, given that it's a much more competitive environment now,\" said attorney Alfred Mamlet of Steptoe &amp; Johnson. \"There are new technologies and new markets for the companies.\""                                   
    ##  [5] "The Federal Communications Commission is drafting rules to spell out the limits set by Congress on the use of \"customer proprietary network information.\" CPNI details when calls are made, the destination, the frequency and length, the number and type of phone lines ordered, and the price of the bill."
    ##  [6] "Few curbs existed before the new telecom law. The new FCC rules -- which stem from a provision in the law pushed by Rep. Edward Markey, D-Mass., -- are expected in early 1997."                                                                                                                                
    ##  [7] "The agency must decide what form of customer approval a carrier must receive before using the data for marketing."                                                                                                                                                                                              
    ##  [8] "The rules will determine, for example, what if any okay is needed for a carrier to use a customer's long-distance calling pattern to pitch a cellular service if a customer is seen to make plenty of calls from the road."                                                                                     
    ##  [9] "Many phone companies want the FCC to avoid stringent rules requiring detailed customer approval. Industry executives argue that consumers would benefit from flexibile rules that let companies target a customer's communications needs."                                                                      
    ## [10] "\"It would give us the opportunity to tailor their package of services to what they need and what they want,\" said James Spurlock, AT&amp;T Corp.'s director of federal government affairs."                                                                                                                   
    ## [11] "But consumer and privacy groups fear the data could fall into the wrong hands without tough curbs and clear approval."                                                                                                                                                                                          
    ## [12] "They also fear an explosion in telemarketing: Companies could use CPNI to market a vast array of products and services unrelated to the phone service a customer actually receives."                                                                                                                            
    ## [13] "\"When consumers sign up for telehone service, they don't expect the information to be used to market non-phone services such as credit cards or investment information,\" said John Windhausen, general counsel for the Competition Policy Institute (CPI), a consumer advocacy group."                        
    ## [14] "Companies already use the information. Long-distance carriers pitch cheaper plans based on a customer's calling habits. The marketing is expected to heat up."                                                                                                                                                  
    ## [15] "Under contention at the FCC is whether a company can use the data derived from its long-distance business to pitch local or cellular service, without prior customer assent."                                                                                                                                   
    ## [16] "The telecom law lets carriers use CPNI without prior approval when supplying the service a customer ordered."                                                                                                                                                                                                   
    ## [17] "The FCC has proposed to classify phone service under three categories: local, long distance and cellular. CPNI from one could not be used to market another without a customer's okay."                                                                                                                         
    ## [18] "A number of phone companies, including several regional Baby Bell companies, have asked the FCC for just one broad category that would give them greater marketing flexibility."                                                                                                                                
    ## [19] "Texas phone regulators, by contrast, propose categories based on \"the exact services (the customer) has ordered.\""                                                                                                                                                                                            
    ## [20] "The FCC also has proposed requiring phone companies to notify customers of their right to restrict access to CPNI."                                                                                                                                                                                             
    ## [21] "Under contention is whether the notification should be oral or written, such as a notice stuffed into a bill or posted in the \"white pages\" phone directory."                                                                                                                                                 
    ## [22] "Consumer advocates, privacy groups and state regulators want advance written approval for use of the information."                                                                                                                                                                                              
    ## [23] "Some companies -- AT&amp;T, several of the Bells and GTE Corp. -- suggest that no response to a detailed notification about a customer's CPNI rights should amount to a customer's blessing."

    content(articles_train[[2036]])

    ##  [1] "Regulators set aside a chunk of airwaves Thursday to let schools, businesses, communities and others bypass phone lines and send video images, data and voice over their own local wireless computer networks."                                                                                                  
    ##  [2] "The Federal Communications Commission's decision, for example, will allow a school to create a high-speed wireless network among classrooms that could then hook up to the World Wide Web, the multimedia portion of the Internet."                                                                              
    ##  [3] "That way, the school can avoid the costs of rewiring a building with high-capacity phone lines for computer use. Drilling through walls with asbestos can be expensive."                                                                                                                                         
    ##  [4] "\"In many buildings, including schools, a wireless connection will be a cost-effective alternative to pulling wire through walls and ceilings,\" said Commissioner Susan Ness."                                                                                                                                  
    ##  [5] "Hospitals, community groups, companies and libraries also could create local high-speed networks in a building, or link up with computers and printers in nearby facilities or communities."                                                                                                                     
    ##  [6] "Users of the new spectrum will not need an FCC license, just like users of baby monitors and cordless phones that also operate over the radio spectrum."                                                                                                                                                         
    ##  [7] "And users will be able to cram more data on a high-speed wireless network than over a traditional phone line."                                                                                                                                                                                                   
    ##  [8] "Computers equipped with antennas are expected to allow consumers, businesses, hospitals and others to create the networks. Now that the FCC has set aside the spectrum, companies are set to produce the needed technology. The equipment, when it is available, must receive FCC approval."                     
    ##  [9] "\"Companies can now go ahead and build products for use in the spectrum,\" said Eric DeSilva, an attorney representing the Wireless Information Networks Forum. The consortium is made up of Lucent Technologies Inc., International Business Machines Corp. and other companies promoting wireless networks."   
    ## [10] "Government and industry officials said potential applications abound."                                                                                                                                                                                                                                           
    ## [11] "Hospitals staffers could receive on-the-spot patient data or X-rays over a wireless network throughout the building. Or a neighbourhood group could communicate within a community over the airwaves via computer."                                                                                              
    ## [12] "The FCC set power limits on the different spectrum bands that will be used so that existing users of the airwaves -- such as satellites and high-powered government radar systems -- will not face interference."                                                                                                
    ## [13] "Operators over the lowest spectrum band will be restricted to indoor use. Users of the middle band will be able to operate over a wider area, such as a college campus. And those using the highest band will be able to operate over several kilometres, such as within a community or with a nearby community."

In order to choose the number of components, we checked the variances of
each components and created an elbow plot. Since the variance between
200 components and 785 components is small (we thought it is not worthy
to take hundreds more components to improve small amount), we decided to
choose 200 components. By using PCA, we could reduce the dimension into
25% of the entire components.

    # std dev of each PCs
    std_dev <- pca_train$sdev

    # Variances of each PCs
    pca_var <- std_dev^2
    # check first 10 variance
    pca_var[1:10]

    ##  [1] 14.451386  9.565554  7.451499  7.300913  6.575546  6.313443  5.485331
    ##  [8]  5.356479  5.038364  4.850376

    # We want to find the components which explain the maximum variance.
    # Higher variance retains more information 

    # To compute the proportion of variance explained by each component, 
    # we simply divide the variance by sum of total variance.

    # proportion of variance explained
    prop_var <- pca_var / sum(pca_var)
    prop_var[1:10]

    ##  [1] 0.018409409 0.012185419 0.009492355 0.009300526 0.008376492 0.008042602
    ##  [7] 0.006987683 0.006823541 0.006418299 0.006178823

    plot(prop_var, xlab = "Principal Component",
                 ylab = "Proportion of Variance Explained",
                 type = "b")

![](Figs/unnamed-chunk-33-1.png) \#\# Naive Bayes Classification With
200 components that we achieved from previous PCA process, we used
C50train data to build Naive Bayes Classification model. Note that we
also added “pseudo-count” into our trainng data in order to avoid any
zero probability in our C50test set.

    author_names <- c()

    for (i in seq(1, length(fileNames))){
      name <- strsplit(fileNames[i], split = "/")[[1]][8]
      author_names <- append(author_names, name)
    }

    pca_df <- as.data.frame(pca_train$x[,1:200])
    pca_df <- cbind("Authors" = as.factor(author_names), pca_df)

    x_nB <- pca_df[,2:201]
    y_nB <- pca_df[,1]

    tr = 0.8
    n = nrow(pca_df)
    d = ncol(pca_df)
    train_set = sort(sample.int(n, floor(tr*n)))
    test_set = setdiff(1:n, train_set)

    X_train = x_nB + 1/d # smoothing
    y_train = y_nB
    #X_test = x_nB[test_set,]
    #y_test = y_nB[test_set]

    nb_model <- naiveBayes(X_train, y_train)
    #nb_model
    #yhat_train <- predict(nb_model, X_test) # 0.682 
    #confusionMatrix(yhat_train, y_test)

We then loaded the real test data set (C50test). Since our model was
fitted by the data set from data cleaning and PCA, we also did the same
process on our C50test data set. One thing to note is that the graph
below shows the first component of our C50test data set is little higher
than our C50train data set while the second component is little lower
than our C50train data set. And the rest components share similar
behaviors.

    # load the test data 
    fileNamesTest <- Sys.glob("/Users/macintosh/Documents/R studio/ReutersC50/C50test/*/*.txt")
    articles_Test = lapply(fileNamesTest, readerPlain)

    mynamesTest = fileNamesTest %>%
        { strsplit(., '/', fixed=TRUE) } %>%
        { lapply(., tail, n=2) } %>%
        { lapply(., paste0, collapse = '') } %>%
        unlist

    names(articles_Test) = mynamesTest 

    documents_raw_Test = Corpus(VectorSource(articles_Test))

    my_documents_Test = documents_raw_Test %>%
      tm_map(content_transformer(tolower))  %>%             # make everything lowercase
      tm_map(content_transformer(removeNumbers)) %>%        # remove numbers
      tm_map(content_transformer(removePunctuation)) %>%    # remove punctuation
      tm_map(content_transformer(stripWhitespace))          # remove excess white-space

    ## Warning in tm_map.SimpleCorpus(., content_transformer(tolower)): transformation
    ## drops documents

    ## Warning in tm_map.SimpleCorpus(., content_transformer(removeNumbers)):
    ## transformation drops documents

    ## Warning in tm_map.SimpleCorpus(., content_transformer(removePunctuation)):
    ## transformation drops documents

    ## Warning in tm_map.SimpleCorpus(., content_transformer(stripWhitespace)):
    ## transformation drops documents

    my_documents_Test = tm_map(my_documents_Test, content_transformer(removeWords), stopwords("en"))

    ## Warning in tm_map.SimpleCorpus(my_documents_Test,
    ## content_transformer(removeWords), : transformation drops documents

    DTM_test = DocumentTermMatrix(my_documents_Test)
    DTM_test = removeSparseTerms(DTM_test, 0.95)
    tfidf_test = weightTfIdf(DTM_test)   

    # Now PCA on term frequencies
    tfidf_test_matix = as.matrix(tfidf_test) # make it into a matrix since prcomp requires matrix format. 
    summary(colSums(tfidf_test_matix))

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   0.000   4.514   5.973   6.653   8.004  33.499

    scrub_cols = which(colSums(tfidf_test_matix) == 0) # drops all zeros
    tfidf_test_matix = tfidf_test_matix[,-scrub_cols]

    pca_test = prcomp(tfidf_test_matix, scale=TRUE)
    plot(pca_test)

![](Figs/unnamed-chunk-35-1.png) And we tested our model with C50test
data. We also added “pseudo-count” as before. We utilized
“confusionMatrix” from “caret” library in order to observe our model’s
accuracy score. We got 0.8788 as our accuracy score. It is quite
impressive that Naive Bayes Classification’s performance on text
classification.

    pca_test_df <- as.data.frame(pca_test$x[,1:200])
    pca_test_df <- cbind("Authors" = as.factor(author_names), pca_test_df)

    x_test_nB <- pca_test_df[,2:201]
    y_test_nB <- pca_test_df[,1]

    #tr = 0.8
    #n = nrow(pca_df)
    #d = ncol(pca_df)
    #train_set = sort(sample.int(n, floor(tr*n)))
    #test_set = setdiff(1:n, train_set)

    X_test = x_nB + 1/d # smoothing
    y_test = y_nB
    #X_test = x_nB[test_set,]
    #y_test = y_nB[test_set]

    # prediction 
    yhat <- predict(nb_model, X_test) # 0.8788  
    confusionMatrix(yhat, y_test) 

    ## Confusion Matrix and Statistics
    ## 
    ##                    Reference
    ## Prediction          AaronPressman AlanCrosby AlexanderSmith BenjaminKangLim
    ##   AaronPressman                48          0              0               0
    ##   AlanCrosby                    0         44              0               0
    ##   AlexanderSmith                0          0             42               0
    ##   BenjaminKangLim               0          0              0              45
    ##   BernardHickey                 0          0              0               0
    ##   BradDorfman                   0          1              0               0
    ##   DarrenSchuettler              0          0              0               0
    ##   DavidLawder                   0          0              0               0
    ##   EdnaFernandes                 0          0              0               0
    ##   EricAuchard                   0          0              0               0
    ##   FumikoFujisaki                0          0              0               0
    ##   GrahamEarnshaw                1          1              0               0
    ##   HeatherScoffield              0          0              0               0
    ##   JaneMacartney                 0          0              0               0
    ##   JanLopatka                    0          2              0               0
    ##   JimGilchrist                  0          0              0               0
    ##   JoeOrtiz                      0          0              2               0
    ##   JohnMastrini                  0          2              0               0
    ##   JonathanBirt                  0          0              0               0
    ##   JoWinterbottom                0          0              0               0
    ##   KarlPenhaul                   0          0              0               1
    ##   KeithWeir                     0          0              0               0
    ##   KevinDrawbaugh                0          0              0               0
    ##   KevinMorrison                 0          0              0               0
    ##   KirstinRidley                 0          0              1               0
    ##   KouroshKarimkhany             0          0              0               0
    ##   LydiaZajc                     0          0              0               0
    ##   LynneO'Donnell                0          0              0               0
    ##   LynnleyBrowning               0          0              0               0
    ##   MarcelMichelson               0          0              0               0
    ##   MarkBendeich                  0          0              0               0
    ##   MartinWolk                    0          0              1               0
    ##   MatthewBunce                  0          0              0               0
    ##   MichaelConnor                 0          0              1               0
    ##   MureDickie                    0          0              0               1
    ##   NickLouth                     0          0              3               1
    ##   PatriciaCommins               0          0              0               0
    ##   PeterHumphrey                 0          0              0               0
    ##   PierreTran                    0          0              0               0
    ##   RobinSidel                    0          0              0               0
    ##   RogerFillion                  1          0              0               0
    ##   SamuelPerry                   0          0              0               0
    ##   SarahDavison                  0          0              0               0
    ##   ScottHillis                   0          0              0               1
    ##   SimonCowell                   0          0              0               0
    ##   TanEeLyn                      0          0              0               0
    ##   TheresePoletti                0          0              0               0
    ##   TimFarrand                    0          0              0               0
    ##   ToddNissen                    0          0              0               0
    ##   WilliamKazer                  0          0              0               1
    ##                    Reference
    ## Prediction          BernardHickey BradDorfman DarrenSchuettler DavidLawder
    ##   AaronPressman                 1           0                0           2
    ##   AlanCrosby                    0           0                0           0
    ##   AlexanderSmith                0           0                0           0
    ##   BenjaminKangLim               0           0                0           0
    ##   BernardHickey                42           0                0           0
    ##   BradDorfman                   0          47                0           0
    ##   DarrenSchuettler              0           0               47           0
    ##   DavidLawder                   0           0                0          39
    ##   EdnaFernandes                 0           0                0           0
    ##   EricAuchard                   0           0                0           0
    ##   FumikoFujisaki                0           0                0           0
    ##   GrahamEarnshaw                0           0                0           0
    ##   HeatherScoffield              0           0                0           0
    ##   JaneMacartney                 0           0                0           0
    ##   JanLopatka                    0           0                0           0
    ##   JimGilchrist                  0           0                0           0
    ##   JoeOrtiz                      0           0                0           0
    ##   JohnMastrini                  0           0                0           1
    ##   JonathanBirt                  0           0                0           0
    ##   JoWinterbottom                0           0                0           0
    ##   KarlPenhaul                   2           0                1           1
    ##   KeithWeir                     0           0                0           0
    ##   KevinDrawbaugh                0           0                0           0
    ##   KevinMorrison                 2           0                0           0
    ##   KirstinRidley                 0           0                0           0
    ##   KouroshKarimkhany             0           0                0           0
    ##   LydiaZajc                     0           0                2           0
    ##   LynneO'Donnell                0           0                0           0
    ##   LynnleyBrowning               0           0                0           0
    ##   MarcelMichelson               0           0                0           0
    ##   MarkBendeich                  1           0                0           0
    ##   MartinWolk                    0           1                0           0
    ##   MatthewBunce                  0           0                0           0
    ##   MichaelConnor                 0           0                0           1
    ##   MureDickie                    0           0                0           0
    ##   NickLouth                     0           0                0           0
    ##   PatriciaCommins               0           0                0           0
    ##   PeterHumphrey                 0           0                0           0
    ##   PierreTran                    0           0                0           1
    ##   RobinSidel                    0           0                0           0
    ##   RogerFillion                  0           0                0           0
    ##   SamuelPerry                   0           1                0           1
    ##   SarahDavison                  0           0                0           0
    ##   ScottHillis                   0           0                0           0
    ##   SimonCowell                   0           0                0           0
    ##   TanEeLyn                      0           0                0           0
    ##   TheresePoletti                1           0                0           2
    ##   TimFarrand                    1           0                0           0
    ##   ToddNissen                    0           1                0           2
    ##   WilliamKazer                  0           0                0           0
    ##                    Reference
    ## Prediction          EdnaFernandes EricAuchard FumikoFujisaki GrahamEarnshaw
    ##   AaronPressman                 1           0              0              0
    ##   AlanCrosby                    0           0              0              0
    ##   AlexanderSmith                0           0              0              0
    ##   BenjaminKangLim               0           0              0              0
    ##   BernardHickey                 0           0              0              0
    ##   BradDorfman                   0           0              0              1
    ##   DarrenSchuettler              0           0              0              0
    ##   DavidLawder                   0           0              0              0
    ##   EdnaFernandes                44           0              0              0
    ##   EricAuchard                   0          40              0              0
    ##   FumikoFujisaki                0           0             48              0
    ##   GrahamEarnshaw                0           0              2             43
    ##   HeatherScoffield              0           0              0              0
    ##   JaneMacartney                 0           0              0              0
    ##   JanLopatka                    0           0              0              0
    ##   JimGilchrist                  0           0              0              0
    ##   JoeOrtiz                      0           0              0              0
    ##   JohnMastrini                  0           0              0              0
    ##   JonathanBirt                  0           0              0              0
    ##   JoWinterbottom                1           0              0              0
    ##   KarlPenhaul                   0           0              0              0
    ##   KeithWeir                     1           0              0              0
    ##   KevinDrawbaugh                0           0              0              0
    ##   KevinMorrison                 0           0              0              0
    ##   KirstinRidley                 0           0              0              0
    ##   KouroshKarimkhany             0           1              0              0
    ##   LydiaZajc                     0           0              0              0
    ##   LynneO'Donnell                0           0              0              0
    ##   LynnleyBrowning               0           0              0              1
    ##   MarcelMichelson               0           0              0              0
    ##   MarkBendeich                  0           0              0              0
    ##   MartinWolk                    0           0              0              0
    ##   MatthewBunce                  0           0              0              0
    ##   MichaelConnor                 0           0              0              1
    ##   MureDickie                    0           0              0              0
    ##   NickLouth                     0           2              0              0
    ##   PatriciaCommins               0           0              0              0
    ##   PeterHumphrey                 0           0              0              0
    ##   PierreTran                    0           0              0              0
    ##   RobinSidel                    0           0              0              0
    ##   RogerFillion                  0           0              0              0
    ##   SamuelPerry                   0           2              0              1
    ##   SarahDavison                  0           0              0              0
    ##   ScottHillis                   0           0              0              0
    ##   SimonCowell                   0           0              0              0
    ##   TanEeLyn                      0           0              0              0
    ##   TheresePoletti                0           5              0              0
    ##   TimFarrand                    3           0              0              0
    ##   ToddNissen                    0           0              0              0
    ##   WilliamKazer                  0           0              0              3
    ##                    Reference
    ## Prediction          HeatherScoffield JaneMacartney JanLopatka JimGilchrist
    ##   AaronPressman                    1             0          0            1
    ##   AlanCrosby                       0             0          0            0
    ##   AlexanderSmith                   0             0          0            0
    ##   BenjaminKangLim                  0             3          0            0
    ##   BernardHickey                    0             0          0            0
    ##   BradDorfman                      0             0          0            0
    ##   DarrenSchuettler                 0             0          0            0
    ##   DavidLawder                      0             0          0            0
    ##   EdnaFernandes                    0             0          0            0
    ##   EricAuchard                      0             0          0            0
    ##   FumikoFujisaki                   0             0          0            0
    ##   GrahamEarnshaw                   0             1          0            0
    ##   HeatherScoffield                47             0          0            0
    ##   JaneMacartney                    0            39          0            0
    ##   JanLopatka                       0             0         42            0
    ##   JimGilchrist                     0             0          0           48
    ##   JoeOrtiz                         0             0          0            0
    ##   JohnMastrini                     0             0          5            0
    ##   JonathanBirt                     0             0          0            0
    ##   JoWinterbottom                   0             0          0            0
    ##   KarlPenhaul                      2             0          0            0
    ##   KeithWeir                        0             0          0            0
    ##   KevinDrawbaugh                   0             0          0            0
    ##   KevinMorrison                    0             0          0            1
    ##   KirstinRidley                    0             0          0            0
    ##   KouroshKarimkhany                0             0          0            0
    ##   LydiaZajc                        0             0          0            0
    ##   LynneO'Donnell                   0             0          0            0
    ##   LynnleyBrowning                  0             1          0            0
    ##   MarcelMichelson                  0             0          0            0
    ##   MarkBendeich                     0             0          0            0
    ##   MartinWolk                       0             0          0            0
    ##   MatthewBunce                     0             0          3            0
    ##   MichaelConnor                    0             0          0            0
    ##   MureDickie                       0             3          0            0
    ##   NickLouth                        0             0          0            0
    ##   PatriciaCommins                  0             0          0            0
    ##   PeterHumphrey                    0             0          0            0
    ##   PierreTran                       0             0          0            0
    ##   RobinSidel                       0             0          0            0
    ##   RogerFillion                     0             0          0            0
    ##   SamuelPerry                      0             0          0            0
    ##   SarahDavison                     0             0          0            0
    ##   ScottHillis                      0             1          0            0
    ##   SimonCowell                      0             0          0            0
    ##   TanEeLyn                         0             1          0            0
    ##   TheresePoletti                   0             0          0            0
    ##   TimFarrand                       0             0          0            0
    ##   ToddNissen                       0             0          0            0
    ##   WilliamKazer                     0             1          0            0
    ##                    Reference
    ## Prediction          JoeOrtiz JohnMastrini JonathanBirt JoWinterbottom
    ##   AaronPressman            0            0            1              0
    ##   AlanCrosby               0            0            0              0
    ##   AlexanderSmith           1            0            0              1
    ##   BenjaminKangLim          0            0            0              0
    ##   BernardHickey            0            0            0              0
    ##   BradDorfman              0            0            0              0
    ##   DarrenSchuettler         0            0            0              0
    ##   DavidLawder              0            0            0              0
    ##   EdnaFernandes            0            0            0              0
    ##   EricAuchard              0            0            0              0
    ##   FumikoFujisaki           0            0            0              0
    ##   GrahamEarnshaw           0            0            0              0
    ##   HeatherScoffield         0            0            0              0
    ##   JaneMacartney            0            0            0              0
    ##   JanLopatka               0            2            0              0
    ##   JimGilchrist             0            0            0              0
    ##   JoeOrtiz                44            0            0              1
    ##   JohnMastrini             0           43            0              0
    ##   JonathanBirt             0            0           44              1
    ##   JoWinterbottom           0            0            1             45
    ##   KarlPenhaul              0            0            0              0
    ##   KeithWeir                1            0            0              0
    ##   KevinDrawbaugh           0            1            0              0
    ##   KevinMorrison            0            0            0              0
    ##   KirstinRidley            0            0            0              0
    ##   KouroshKarimkhany        0            0            0              0
    ##   LydiaZajc                0            0            0              0
    ##   LynneO'Donnell           0            0            0              0
    ##   LynnleyBrowning          0            0            0              0
    ##   MarcelMichelson          0            0            0              0
    ##   MarkBendeich             0            0            0              0
    ##   MartinWolk               0            0            0              0
    ##   MatthewBunce             0            0            0              0
    ##   MichaelConnor            0            0            0              0
    ##   MureDickie               0            0            0              0
    ##   NickLouth                0            0            0              0
    ##   PatriciaCommins          0            0            0              0
    ##   PeterHumphrey            0            0            0              0
    ##   PierreTran               1            0            0              0
    ##   RobinSidel               0            0            0              0
    ##   RogerFillion             0            0            0              0
    ##   SamuelPerry              1            1            0              0
    ##   SarahDavison             1            3            0              0
    ##   ScottHillis              0            0            0              0
    ##   SimonCowell              1            0            0              0
    ##   TanEeLyn                 0            0            0              0
    ##   TheresePoletti           0            0            0              0
    ##   TimFarrand               0            0            4              2
    ##   ToddNissen               0            0            0              0
    ##   WilliamKazer             0            0            0              0
    ##                    Reference
    ## Prediction          KarlPenhaul KeithWeir KevinDrawbaugh KevinMorrison
    ##   AaronPressman               0         0              0             0
    ##   AlanCrosby                  0         0              0             0
    ##   AlexanderSmith              0         0              0             0
    ##   BenjaminKangLim             0         0              0             0
    ##   BernardHickey               0         0              0             6
    ##   BradDorfman                 0         0              0             0
    ##   DarrenSchuettler            0         0              0             0
    ##   DavidLawder                 0         0              0             0
    ##   EdnaFernandes               0         1              0             0
    ##   EricAuchard                 0         0              0             0
    ##   FumikoFujisaki              0         0              0             0
    ##   GrahamEarnshaw              0         0              0             0
    ##   HeatherScoffield            0         0              0             0
    ##   JaneMacartney               0         0              0             0
    ##   JanLopatka                  0         0              0             0
    ##   JimGilchrist                0         0              0             0
    ##   JoeOrtiz                    0         0              0             0
    ##   JohnMastrini                0         0              0             0
    ##   JonathanBirt                0         2              0             0
    ##   JoWinterbottom              0         0              0             0
    ##   KarlPenhaul                45         0              0             0
    ##   KeithWeir                   0        44              0             0
    ##   KevinDrawbaugh              0         0             50             0
    ##   KevinMorrison               0         0              0            41
    ##   KirstinRidley               0         1              0             0
    ##   KouroshKarimkhany           0         0              0             0
    ##   LydiaZajc                   0         0              0             0
    ##   LynneO'Donnell              0         0              0             0
    ##   LynnleyBrowning             1         0              0             0
    ##   MarcelMichelson             0         0              0             0
    ##   MarkBendeich                0         0              0             2
    ##   MartinWolk                  0         0              0             0
    ##   MatthewBunce                2         0              0             0
    ##   MichaelConnor               0         0              0             0
    ##   MureDickie                  0         0              0             0
    ##   NickLouth                   0         2              0             0
    ##   PatriciaCommins             0         0              0             0
    ##   PeterHumphrey               0         0              0             0
    ##   PierreTran                  0         0              0             0
    ##   RobinSidel                  0         0              0             0
    ##   RogerFillion                0         0              0             0
    ##   SamuelPerry                 0         0              0             1
    ##   SarahDavison                1         0              0             0
    ##   ScottHillis                 0         0              0             0
    ##   SimonCowell                 0         0              0             0
    ##   TanEeLyn                    0         0              0             0
    ##   TheresePoletti              0         0              0             0
    ##   TimFarrand                  0         0              0             0
    ##   ToddNissen                  0         0              0             0
    ##   WilliamKazer                1         0              0             0
    ##                    Reference
    ## Prediction          KirstinRidley KouroshKarimkhany LydiaZajc LynneO'Donnell
    ##   AaronPressman                 3                 0         0              0
    ##   AlanCrosby                    0                 0         0              0
    ##   AlexanderSmith                1                 0         0              0
    ##   BenjaminKangLim               0                 0         0              0
    ##   BernardHickey                 0                 0         0              0
    ##   BradDorfman                   0                 0         0              0
    ##   DarrenSchuettler              0                 0         0              0
    ##   DavidLawder                   0                 0         0              0
    ##   EdnaFernandes                 0                 0         0              0
    ##   EricAuchard                   0                 1         0              0
    ##   FumikoFujisaki                0                 0         0              0
    ##   GrahamEarnshaw                0                 0         0              0
    ##   HeatherScoffield              0                 0         0              0
    ##   JaneMacartney                 0                 0         0              0
    ##   JanLopatka                    0                 0         0              0
    ##   JimGilchrist                  0                 0         0              0
    ##   JoeOrtiz                      0                 0         0              0
    ##   JohnMastrini                  0                 0         0              0
    ##   JonathanBirt                  0                 0         0              0
    ##   JoWinterbottom                2                 0         0              0
    ##   KarlPenhaul                   0                 0         2              0
    ##   KeithWeir                     0                 0         0              0
    ##   KevinDrawbaugh                0                 0         0              0
    ##   KevinMorrison                 0                 0         0              0
    ##   KirstinRidley                38                 0         0              0
    ##   KouroshKarimkhany             0                47         0              0
    ##   LydiaZajc                     0                 0        44              0
    ##   LynneO'Donnell                0                 0         0             49
    ##   LynnleyBrowning               0                 0         0              0
    ##   MarcelMichelson               0                 0         0              0
    ##   MarkBendeich                  0                 0         0              0
    ##   MartinWolk                    0                 1         2              0
    ##   MatthewBunce                  0                 0         0              0
    ##   MichaelConnor                 1                 0         1              0
    ##   MureDickie                    0                 0         0              0
    ##   NickLouth                     2                 0         0              0
    ##   PatriciaCommins               0                 0         0              0
    ##   PeterHumphrey                 0                 0         0              0
    ##   PierreTran                    0                 0         0              0
    ##   RobinSidel                    0                 0         0              0
    ##   RogerFillion                  0                 0         0              0
    ##   SamuelPerry                   1                 0         0              0
    ##   SarahDavison                  0                 0         0              0
    ##   ScottHillis                   0                 0         0              0
    ##   SimonCowell                   0                 0         0              0
    ##   TanEeLyn                      0                 0         0              1
    ##   TheresePoletti                0                 1         1              0
    ##   TimFarrand                    2                 0         0              0
    ##   ToddNissen                    0                 0         0              0
    ##   WilliamKazer                  0                 0         0              0
    ##                    Reference
    ## Prediction          LynnleyBrowning MarcelMichelson MarkBendeich MartinWolk
    ##   AaronPressman                   0               1            0          0
    ##   AlanCrosby                      0               0            0          0
    ##   AlexanderSmith                  0               0            0          0
    ##   BenjaminKangLim                 0               0            0          0
    ##   BernardHickey                   0               0            0          0
    ##   BradDorfman                     0               0            0          0
    ##   DarrenSchuettler                0               0            0          0
    ##   DavidLawder                     0               0            0          0
    ##   EdnaFernandes                   0               0            0          0
    ##   EricAuchard                     0               0            0          0
    ##   FumikoFujisaki                  0               0            0          0
    ##   GrahamEarnshaw                  0               0            0          0
    ##   HeatherScoffield                0               0            0          0
    ##   JaneMacartney                   0               0            0          0
    ##   JanLopatka                      0               0            0          0
    ##   JimGilchrist                    0               0            0          0
    ##   JoeOrtiz                        0               0            0          0
    ##   JohnMastrini                    0               0            0          0
    ##   JonathanBirt                    0               0            0          0
    ##   JoWinterbottom                  0               0            0          0
    ##   KarlPenhaul                     0               1            0          0
    ##   KeithWeir                       0               0            0          0
    ##   KevinDrawbaugh                  0               0            0          0
    ##   KevinMorrison                   0               0            2          0
    ##   KirstinRidley                   0               0            0          0
    ##   KouroshKarimkhany               0               0            0          0
    ##   LydiaZajc                       0               0            0          0
    ##   LynneO'Donnell                  0               0            0          0
    ##   LynnleyBrowning                50               0            0          0
    ##   MarcelMichelson                 0              47            0          0
    ##   MarkBendeich                    0               0           47          0
    ##   MartinWolk                      0               0            0         46
    ##   MatthewBunce                    0               0            0          0
    ##   MichaelConnor                   0               0            0          0
    ##   MureDickie                      0               0            0          0
    ##   NickLouth                       0               0            0          0
    ##   PatriciaCommins                 0               0            1          0
    ##   PeterHumphrey                   0               0            0          0
    ##   PierreTran                      0               0            0          0
    ##   RobinSidel                      0               0            0          0
    ##   RogerFillion                    0               0            0          0
    ##   SamuelPerry                     0               1            0          1
    ##   SarahDavison                    0               0            0          0
    ##   ScottHillis                     0               0            0          1
    ##   SimonCowell                     0               0            0          0
    ##   TanEeLyn                        0               0            0          0
    ##   TheresePoletti                  0               0            0          2
    ##   TimFarrand                      0               0            0          0
    ##   ToddNissen                      0               0            0          0
    ##   WilliamKazer                    0               0            0          0
    ##                    Reference
    ## Prediction          MatthewBunce MichaelConnor MureDickie NickLouth
    ##   AaronPressman                0             1          0         0
    ##   AlanCrosby                   0             0          0         0
    ##   AlexanderSmith               0             0          0         0
    ##   BenjaminKangLim              0             0          1         0
    ##   BernardHickey                0             0          0         0
    ##   BradDorfman                  0             0          0         1
    ##   DarrenSchuettler             0             0          0         0
    ##   DavidLawder                  0             0          0         0
    ##   EdnaFernandes                0             0          0         0
    ##   EricAuchard                  0             0          0         0
    ##   FumikoFujisaki               0             0          0         0
    ##   GrahamEarnshaw               0             0          0         0
    ##   HeatherScoffield             0             0          0         0
    ##   JaneMacartney                0             0          2         0
    ##   JanLopatka                   0             0          0         0
    ##   JimGilchrist                 0             0          0         0
    ##   JoeOrtiz                     0             0          0         0
    ##   JohnMastrini                 1             0          0         0
    ##   JonathanBirt                 0             0          0         0
    ##   JoWinterbottom               0             0          0         0
    ##   KarlPenhaul                  2             0          1         0
    ##   KeithWeir                    0             0          0         0
    ##   KevinDrawbaugh               0             5          0         0
    ##   KevinMorrison                0             0          0         0
    ##   KirstinRidley                0             0          0         0
    ##   KouroshKarimkhany            0             0          0         0
    ##   LydiaZajc                    0             0          0         0
    ##   LynneO'Donnell               0             0          0         0
    ##   LynnleyBrowning              0             0          0         0
    ##   MarcelMichelson              0             0          0         0
    ##   MarkBendeich                 0             0          0         0
    ##   MartinWolk                   0             0          0         0
    ##   MatthewBunce                47             0          0         0
    ##   MichaelConnor                0            42          0         1
    ##   MureDickie                   0             0         40         0
    ##   NickLouth                    0             0          1        48
    ##   PatriciaCommins              0             0          0         0
    ##   PeterHumphrey                0             0          2         0
    ##   PierreTran                   0             0          0         0
    ##   RobinSidel                   0             0          0         0
    ##   RogerFillion                 0             0          0         0
    ##   SamuelPerry                  0             0          0         0
    ##   SarahDavison                 0             0          0         0
    ##   ScottHillis                  0             0          1         0
    ##   SimonCowell                  0             0          0         0
    ##   TanEeLyn                     0             0          0         0
    ##   TheresePoletti               0             2          0         0
    ##   TimFarrand                   0             0          0         0
    ##   ToddNissen                   0             0          0         0
    ##   WilliamKazer                 0             0          2         0
    ##                    Reference
    ## Prediction          PatriciaCommins PeterHumphrey PierreTran RobinSidel
    ##   AaronPressman                   0             0          0          0
    ##   AlanCrosby                      0             0          1          0
    ##   AlexanderSmith                  0             0          0          0
    ##   BenjaminKangLim                 0             1          0          0
    ##   BernardHickey                   0             0          0          0
    ##   BradDorfman                     1             0          0          1
    ##   DarrenSchuettler                0             0          0          0
    ##   DavidLawder                     0             0          0          0
    ##   EdnaFernandes                   0             0          0          0
    ##   EricAuchard                     1             0          0          0
    ##   FumikoFujisaki                  0             0          0          0
    ##   GrahamEarnshaw                  0             0          0          0
    ##   HeatherScoffield                0             0          0          0
    ##   JaneMacartney                   0             0          0          0
    ##   JanLopatka                      0             0          0          0
    ##   JimGilchrist                    0             0          0          0
    ##   JoeOrtiz                        0             0          0          0
    ##   JohnMastrini                    0             0          0          0
    ##   JonathanBirt                    1             0          0          0
    ##   JoWinterbottom                  0             0          0          0
    ##   KarlPenhaul                     0             0          0          0
    ##   KeithWeir                       0             0          0          0
    ##   KevinDrawbaugh                  2             0          0          0
    ##   KevinMorrison                   0             0          0          0
    ##   KirstinRidley                   0             0          0          0
    ##   KouroshKarimkhany               0             0          0          0
    ##   LydiaZajc                       0             0          0          0
    ##   LynneO'Donnell                  0             0          0          0
    ##   LynnleyBrowning                 0             0          0          0
    ##   MarcelMichelson                 0             0          4          0
    ##   MarkBendeich                    0             0          0          0
    ##   MartinWolk                      1             0          0          0
    ##   MatthewBunce                    0             0          0          0
    ##   MichaelConnor                   0             0          0          0
    ##   MureDickie                      0             1          0          0
    ##   NickLouth                       0             0          0          0
    ##   PatriciaCommins                42             0          0          0
    ##   PeterHumphrey                   0            46          0          0
    ##   PierreTran                      0             0         45          0
    ##   RobinSidel                      0             0          0         49
    ##   RogerFillion                    0             0          0          0
    ##   SamuelPerry                     0             0          0          0
    ##   SarahDavison                    0             0          0          0
    ##   ScottHillis                     0             0          0          0
    ##   SimonCowell                     0             0          0          0
    ##   TanEeLyn                        0             2          0          0
    ##   TheresePoletti                  2             0          0          0
    ##   TimFarrand                      0             0          0          0
    ##   ToddNissen                      0             0          0          0
    ##   WilliamKazer                    0             0          0          0
    ##                    Reference
    ## Prediction          RogerFillion SamuelPerry SarahDavison ScottHillis
    ##   AaronPressman                0           0            0           0
    ##   AlanCrosby                   0           0            0           1
    ##   AlexanderSmith               0           0            0           0
    ##   BenjaminKangLim              0           0            0           3
    ##   BernardHickey                0           0            0           0
    ##   BradDorfman                  0           0            0           0
    ##   DarrenSchuettler             1           0            0           0
    ##   DavidLawder                  0           0            0           0
    ##   EdnaFernandes                0           0            0           0
    ##   EricAuchard                  0           2            0           0
    ##   FumikoFujisaki               0           0            0           0
    ##   GrahamEarnshaw               0           0            1           0
    ##   HeatherScoffield             0           0            0           0
    ##   JaneMacartney                0           0            0           1
    ##   JanLopatka                   0           0            0           0
    ##   JimGilchrist                 0           0            1           0
    ##   JoeOrtiz                     0           0            0           0
    ##   JohnMastrini                 0           0            0           0
    ##   JonathanBirt                 0           0            0           0
    ##   JoWinterbottom               0           0            0           0
    ##   KarlPenhaul                  0           0            0           0
    ##   KeithWeir                    0           0            0           0
    ##   KevinDrawbaugh               0           1            0           0
    ##   KevinMorrison                0           0            0           0
    ##   KirstinRidley                0           0            0           0
    ##   KouroshKarimkhany            0           1            0           0
    ##   LydiaZajc                    0           0            0           0
    ##   LynneO'Donnell               0           0            0           0
    ##   LynnleyBrowning              0           0            0           0
    ##   MarcelMichelson              0           0            0           0
    ##   MarkBendeich                 0           0            0           0
    ##   MartinWolk                   0           0            0           0
    ##   MatthewBunce                 0           0            0           0
    ##   MichaelConnor                0           0            0           0
    ##   MureDickie                   0           0            0           3
    ##   NickLouth                    1           0            0           0
    ##   PatriciaCommins              0           0            0           0
    ##   PeterHumphrey                0           0            0           4
    ##   PierreTran                   0           0            0           0
    ##   RobinSidel                   0           0            1           0
    ##   RogerFillion                48           0            0           0
    ##   SamuelPerry                  0          43            0           1
    ##   SarahDavison                 0           0           45           0
    ##   ScottHillis                  0           0            1          34
    ##   SimonCowell                  0           0            0           0
    ##   TanEeLyn                     0           0            1           1
    ##   TheresePoletti               0           3            0           1
    ##   TimFarrand                   0           0            0           0
    ##   ToddNissen                   0           0            0           0
    ##   WilliamKazer                 0           0            0           1
    ##                    Reference
    ## Prediction          SimonCowell TanEeLyn TheresePoletti TimFarrand ToddNissen
    ##   AaronPressman               2        0              0          1          0
    ##   AlanCrosby                  0        0              0          0          0
    ##   AlexanderSmith              1        0              0          1          0
    ##   BenjaminKangLim             0        0              0          0          0
    ##   BernardHickey               0        0              0          0          0
    ##   BradDorfman                 0        0              0          0          1
    ##   DarrenSchuettler            0        0              0          0          0
    ##   DavidLawder                 0        0              0          0          8
    ##   EdnaFernandes               1        0              0          0          0
    ##   EricAuchard                 0        0              3          0          0
    ##   FumikoFujisaki              0        0              0          0          0
    ##   GrahamEarnshaw              0        0              0          0          0
    ##   HeatherScoffield            0        0              0          0          0
    ##   JaneMacartney               0        1              0          0          0
    ##   JanLopatka                  0        1              0          0          0
    ##   JimGilchrist                0        3              0          0          0
    ##   JoeOrtiz                    1        0              0          0          0
    ##   JohnMastrini                0        0              0          0          0
    ##   JonathanBirt                0        0              0          0          0
    ##   JoWinterbottom              0        0              0          0          0
    ##   KarlPenhaul                 2        0              0          1          0
    ##   KeithWeir                   0        0              0          0          0
    ##   KevinDrawbaugh              1        0              1          0          2
    ##   KevinMorrison               0        0              0          0          0
    ##   KirstinRidley               1        0              0          0          0
    ##   KouroshKarimkhany           0        0              1          0          0
    ##   LydiaZajc                   0        0              0          0          0
    ##   LynneO'Donnell              0        1              0          0          0
    ##   LynnleyBrowning             0        0              0          0          0
    ##   MarcelMichelson             0        0              0          0          0
    ##   MarkBendeich                0        1              0          0          0
    ##   MartinWolk                  0        0              0          1          0
    ##   MatthewBunce                0        0              0          0          0
    ##   MichaelConnor               0        0              0          0          0
    ##   MureDickie                  0        2              0          0          0
    ##   NickLouth                   0        0              0          0          1
    ##   PatriciaCommins             0        0              0          0          0
    ##   PeterHumphrey               0       10              0          0          0
    ##   PierreTran                  0        0              0          0          0
    ##   RobinSidel                  0        0              0          0          0
    ##   RogerFillion                0        0              0          0          0
    ##   SamuelPerry                 0        0              0          0          0
    ##   SarahDavison                0        0              0          0          0
    ##   ScottHillis                 0        0              0          0          0
    ##   SimonCowell                41        0              0          0          0
    ##   TanEeLyn                    0       31              0          0          0
    ##   TheresePoletti              0        0             45          0          4
    ##   TimFarrand                  0        0              0         46          0
    ##   ToddNissen                  0        0              0          0         34
    ##   WilliamKazer                0        0              0          0          0
    ##                    Reference
    ## Prediction          WilliamKazer
    ##   AaronPressman                0
    ##   AlanCrosby                   0
    ##   AlexanderSmith               0
    ##   BenjaminKangLim              2
    ##   BernardHickey                0
    ##   BradDorfman                  0
    ##   DarrenSchuettler             0
    ##   DavidLawder                  0
    ##   EdnaFernandes                0
    ##   EricAuchard                  0
    ##   FumikoFujisaki               0
    ##   GrahamEarnshaw               2
    ##   HeatherScoffield             0
    ##   JaneMacartney                1
    ##   JanLopatka                   0
    ##   JimGilchrist                 0
    ##   JoeOrtiz                     0
    ##   JohnMastrini                 0
    ##   JonathanBirt                 0
    ##   JoWinterbottom               0
    ##   KarlPenhaul                  0
    ##   KeithWeir                    0
    ##   KevinDrawbaugh               0
    ##   KevinMorrison                0
    ##   KirstinRidley                0
    ##   KouroshKarimkhany            0
    ##   LydiaZajc                    0
    ##   LynneO'Donnell               0
    ##   LynnleyBrowning              0
    ##   MarcelMichelson              0
    ##   MarkBendeich                 0
    ##   MartinWolk                   0
    ##   MatthewBunce                 0
    ##   MichaelConnor                0
    ##   MureDickie                   1
    ##   NickLouth                    1
    ##   PatriciaCommins              0
    ##   PeterHumphrey                0
    ##   PierreTran                   0
    ##   RobinSidel                   0
    ##   RogerFillion                 0
    ##   SamuelPerry                  0
    ##   SarahDavison                 0
    ##   ScottHillis                  1
    ##   SimonCowell                  0
    ##   TanEeLyn                     0
    ##   TheresePoletti               0
    ##   TimFarrand                   0
    ##   ToddNissen                   0
    ##   WilliamKazer                42
    ## 
    ## Overall Statistics
    ##                                           
    ##                Accuracy : 0.8788          
    ##                  95% CI : (0.8654, 0.8913)
    ##     No Information Rate : 0.02            
    ##     P-Value [Acc > NIR] : < 2.2e-16       
    ##                                           
    ##                   Kappa : 0.8763          
    ##                                           
    ##  Mcnemar's Test P-Value : NA              
    ## 
    ## Statistics by Class:
    ## 
    ##                      Class: AaronPressman Class: AlanCrosby
    ## Sensitivity                        0.9600            0.8800
    ## Specificity                        0.9939            0.9992
    ## Pos Pred Value                     0.7619            0.9565
    ## Neg Pred Value                     0.9992            0.9976
    ## Prevalence                         0.0200            0.0200
    ## Detection Rate                     0.0192            0.0176
    ## Detection Prevalence               0.0252            0.0184
    ## Balanced Accuracy                  0.9769            0.9396
    ##                      Class: AlexanderSmith Class: BenjaminKangLim
    ## Sensitivity                         0.8400                 0.9000
    ## Specificity                         0.9980                 0.9959
    ## Pos Pred Value                      0.8936                 0.8182
    ## Neg Pred Value                      0.9967                 0.9980
    ## Prevalence                          0.0200                 0.0200
    ## Detection Rate                      0.0168                 0.0180
    ## Detection Prevalence                0.0188                 0.0220
    ## Balanced Accuracy                   0.9190                 0.9480
    ##                      Class: BernardHickey Class: BradDorfman
    ## Sensitivity                        0.8400             0.9400
    ## Specificity                        0.9976             0.9976
    ## Pos Pred Value                     0.8750             0.8868
    ## Neg Pred Value                     0.9967             0.9988
    ## Prevalence                         0.0200             0.0200
    ## Detection Rate                     0.0168             0.0188
    ## Detection Prevalence               0.0192             0.0212
    ## Balanced Accuracy                  0.9188             0.9688
    ##                      Class: DarrenSchuettler Class: DavidLawder
    ## Sensitivity                           0.9400             0.7800
    ## Specificity                           0.9996             0.9967
    ## Pos Pred Value                        0.9792             0.8298
    ## Neg Pred Value                        0.9988             0.9955
    ## Prevalence                            0.0200             0.0200
    ## Detection Rate                        0.0188             0.0156
    ## Detection Prevalence                  0.0192             0.0188
    ## Balanced Accuracy                     0.9698             0.8884
    ##                      Class: EdnaFernandes Class: EricAuchard
    ## Sensitivity                        0.8800             0.8000
    ## Specificity                        0.9992             0.9971
    ## Pos Pred Value                     0.9565             0.8511
    ## Neg Pred Value                     0.9976             0.9959
    ## Prevalence                         0.0200             0.0200
    ## Detection Rate                     0.0176             0.0160
    ## Detection Prevalence               0.0184             0.0188
    ## Balanced Accuracy                  0.9396             0.8986
    ##                      Class: FumikoFujisaki Class: GrahamEarnshaw
    ## Sensitivity                         0.9600                0.8600
    ## Specificity                         1.0000                0.9967
    ## Pos Pred Value                      1.0000                0.8431
    ## Neg Pred Value                      0.9992                0.9971
    ## Prevalence                          0.0200                0.0200
    ## Detection Rate                      0.0192                0.0172
    ## Detection Prevalence                0.0192                0.0204
    ## Balanced Accuracy                   0.9800                0.9284
    ##                      Class: HeatherScoffield Class: JaneMacartney
    ## Sensitivity                           0.9400               0.7800
    ## Specificity                           1.0000               0.9980
    ## Pos Pred Value                        1.0000               0.8864
    ## Neg Pred Value                        0.9988               0.9955
    ## Prevalence                            0.0200               0.0200
    ## Detection Rate                        0.0188               0.0156
    ## Detection Prevalence                  0.0188               0.0176
    ## Balanced Accuracy                     0.9700               0.8890
    ##                      Class: JanLopatka Class: JimGilchrist Class: JoeOrtiz
    ## Sensitivity                     0.8400              0.9600          0.8800
    ## Specificity                     0.9980              0.9984          0.9984
    ## Pos Pred Value                  0.8936              0.9231          0.9167
    ## Neg Pred Value                  0.9967              0.9992          0.9976
    ## Prevalence                      0.0200              0.0200          0.0200
    ## Detection Rate                  0.0168              0.0192          0.0176
    ## Detection Prevalence            0.0188              0.0208          0.0192
    ## Balanced Accuracy               0.9190              0.9792          0.9392
    ##                      Class: JohnMastrini Class: JonathanBirt
    ## Sensitivity                       0.8600              0.8800
    ## Specificity                       0.9963              0.9984
    ## Pos Pred Value                    0.8269              0.9167
    ## Neg Pred Value                    0.9971              0.9976
    ## Prevalence                        0.0200              0.0200
    ## Detection Rate                    0.0172              0.0176
    ## Detection Prevalence              0.0208              0.0192
    ## Balanced Accuracy                 0.9282              0.9392
    ##                      Class: JoWinterbottom Class: KarlPenhaul Class: KeithWeir
    ## Sensitivity                         0.9000             0.9000           0.8800
    ## Specificity                         0.9984             0.9935           0.9992
    ## Pos Pred Value                      0.9184             0.7377           0.9565
    ## Neg Pred Value                      0.9980             0.9979           0.9976
    ## Prevalence                          0.0200             0.0200           0.0200
    ## Detection Rate                      0.0180             0.0180           0.0176
    ## Detection Prevalence                0.0196             0.0244           0.0184
    ## Balanced Accuracy                   0.9492             0.9467           0.9396
    ##                      Class: KevinDrawbaugh Class: KevinMorrison
    ## Sensitivity                         1.0000               0.8200
    ## Specificity                         0.9947               0.9980
    ## Pos Pred Value                      0.7937               0.8913
    ## Neg Pred Value                      1.0000               0.9963
    ## Prevalence                          0.0200               0.0200
    ## Detection Rate                      0.0200               0.0164
    ## Detection Prevalence                0.0252               0.0184
    ## Balanced Accuracy                   0.9973               0.9090
    ##                      Class: KirstinRidley Class: KouroshKarimkhany
    ## Sensitivity                        0.7600                   0.9400
    ## Specificity                        0.9988                   0.9988
    ## Pos Pred Value                     0.9268                   0.9400
    ## Neg Pred Value                     0.9951                   0.9988
    ## Prevalence                         0.0200                   0.0200
    ## Detection Rate                     0.0152                   0.0188
    ## Detection Prevalence               0.0164                   0.0200
    ## Balanced Accuracy                  0.8794                   0.9694
    ##                      Class: LydiaZajc Class: LynneO'Donnell
    ## Sensitivity                    0.8800                0.9800
    ## Specificity                    0.9992                0.9996
    ## Pos Pred Value                 0.9565                0.9800
    ## Neg Pred Value                 0.9976                0.9996
    ## Prevalence                     0.0200                0.0200
    ## Detection Rate                 0.0176                0.0196
    ## Detection Prevalence           0.0184                0.0200
    ## Balanced Accuracy              0.9396                0.9898
    ##                      Class: LynnleyBrowning Class: MarcelMichelson
    ## Sensitivity                          1.0000                 0.9400
    ## Specificity                          0.9988                 0.9984
    ## Pos Pred Value                       0.9434                 0.9216
    ## Neg Pred Value                       1.0000                 0.9988
    ## Prevalence                           0.0200                 0.0200
    ## Detection Rate                       0.0200                 0.0188
    ## Detection Prevalence                 0.0212                 0.0204
    ## Balanced Accuracy                    0.9994                 0.9692
    ##                      Class: MarkBendeich Class: MartinWolk Class: MatthewBunce
    ## Sensitivity                       0.9400            0.9200              0.9400
    ## Specificity                       0.9984            0.9971              0.9980
    ## Pos Pred Value                    0.9216            0.8679              0.9038
    ## Neg Pred Value                    0.9988            0.9984              0.9988
    ## Prevalence                        0.0200            0.0200              0.0200
    ## Detection Rate                    0.0188            0.0184              0.0188
    ## Detection Prevalence              0.0204            0.0212              0.0208
    ## Balanced Accuracy                 0.9692            0.9586              0.9690
    ##                      Class: MichaelConnor Class: MureDickie Class: NickLouth
    ## Sensitivity                        0.8400            0.8000           0.9600
    ## Specificity                        0.9976            0.9955           0.9943
    ## Pos Pred Value                     0.8750            0.7843           0.7742
    ## Neg Pred Value                     0.9967            0.9959           0.9992
    ## Prevalence                         0.0200            0.0200           0.0200
    ## Detection Rate                     0.0168            0.0160           0.0192
    ## Detection Prevalence               0.0192            0.0204           0.0248
    ## Balanced Accuracy                  0.9188            0.8978           0.9771
    ##                      Class: PatriciaCommins Class: PeterHumphrey
    ## Sensitivity                          0.8400               0.9200
    ## Specificity                          0.9996               0.9935
    ## Pos Pred Value                       0.9767               0.7419
    ## Neg Pred Value                       0.9967               0.9984
    ## Prevalence                           0.0200               0.0200
    ## Detection Rate                       0.0168               0.0184
    ## Detection Prevalence                 0.0172               0.0248
    ## Balanced Accuracy                    0.9198               0.9567
    ##                      Class: PierreTran Class: RobinSidel Class: RogerFillion
    ## Sensitivity                     0.9000            0.9800              0.9600
    ## Specificity                     0.9992            0.9996              0.9996
    ## Pos Pred Value                  0.9574            0.9800              0.9796
    ## Neg Pred Value                  0.9980            0.9996              0.9992
    ## Prevalence                      0.0200            0.0200              0.0200
    ## Detection Rate                  0.0180            0.0196              0.0192
    ## Detection Prevalence            0.0188            0.0200              0.0196
    ## Balanced Accuracy               0.9496            0.9898              0.9798
    ##                      Class: SamuelPerry Class: SarahDavison Class: ScottHillis
    ## Sensitivity                      0.8600               0.900             0.6800
    ## Specificity                      0.9951               0.998             0.9976
    ## Pos Pred Value                   0.7818               0.900             0.8500
    ## Neg Pred Value                   0.9971               0.998             0.9935
    ## Prevalence                       0.0200               0.020             0.0200
    ## Detection Rate                   0.0172               0.018             0.0136
    ## Detection Prevalence             0.0220               0.020             0.0160
    ## Balanced Accuracy                0.9276               0.949             0.8388
    ##                      Class: SimonCowell Class: TanEeLyn Class: TheresePoletti
    ## Sensitivity                      0.8200          0.6200                0.9000
    ## Specificity                      0.9996          0.9976                0.9902
    ## Pos Pred Value                   0.9762          0.8378                0.6522
    ## Neg Pred Value                   0.9963          0.9923                0.9979
    ## Prevalence                       0.0200          0.0200                0.0200
    ## Detection Rate                   0.0164          0.0124                0.0180
    ## Detection Prevalence             0.0168          0.0148                0.0276
    ## Balanced Accuracy                0.9098          0.8088                0.9451
    ##                      Class: TimFarrand Class: ToddNissen Class: WilliamKazer
    ## Sensitivity                     0.9200            0.6800              0.8400
    ## Specificity                     0.9951            0.9988              0.9963
    ## Pos Pred Value                  0.7931            0.9189              0.8235
    ## Neg Pred Value                  0.9984            0.9935              0.9967
    ## Prevalence                      0.0200            0.0200              0.0200
    ## Detection Rate                  0.0184            0.0136              0.0168
    ## Detection Prevalence            0.0232            0.0148              0.0204
    ## Balanced Accuracy               0.9576            0.8394              0.9182

Association rule mining
-----------------------

Since our data file is text file, we utilized “read.transactions”
function from “arule” library to convert our text data into transaction
data with dropping duplicates at the same time. As a result, we now have
9835 transactions (rows) with 169 unique food names (columns).

    if (!require("arules")) install.packages('arules', repos="http://cran.us.r-project.org")

    ## Loading required package: arules

    ## 
    ## Attaching package: 'arules'

    ## The following object is masked from 'package:tm':
    ## 
    ##     inspect

    ## The following objects are masked from 'package:mosaic':
    ## 
    ##     inspect, lhs, rhs

    ## The following object is masked from 'package:dplyr':
    ## 
    ##     recode

    ## The following objects are masked from 'package:base':
    ## 
    ##     abbreviate, write

    library(arules)
    library(tidyverse)
    library(arulesViz)

    ## Loading required package: grid

    ## Registered S3 methods overwritten by 'registry':
    ##   method               from 
    ##   print.registry_field proxy
    ##   print.registry_entry proxy

    ## Registered S3 method overwritten by 'seriation':
    ##   method         from 
    ##   reorder.hclust gclus

    # load the data using arule
    transactions <- arules::read.transactions(
      file="groceries.txt",
      format = c("basket"),
      sep = ",",
      cols =NULL,
      rm.duplicates = 1,
      skip = 0
    )

    #check 
    head(transactions@itemInfo$labels)

    ## [1] "abrasive cleaner" "artif. sweetener" "baby cosmetics"   "baby food"       
    ## [5] "bags"             "baking powder"

    print(paste("There are ", transactions@data@Dim[2], "transactions with ", transactions@data@Dim[1], "items."))

    ## [1] "There are  9835 transactions with  169 items."

Among those 169 food names, the most frequent items are “whole milk”,
“other vegetables”, “rolls/buns”, “soda”, and “yogurt”.

    summary(transactions)

    ## transactions as itemMatrix in sparse format with
    ##  9835 rows (elements/itemsets/transactions) and
    ##  169 columns (items) and a density of 0.02609146 
    ## 
    ## most frequent items:
    ##       whole milk other vegetables       rolls/buns             soda 
    ##             2513             1903             1809             1715 
    ##           yogurt          (Other) 
    ##             1372            34055 
    ## 
    ## element (itemset/transaction) length distribution:
    ## sizes
    ##    1    2    3    4    5    6    7    8    9   10   11   12   13   14   15   16 
    ## 2159 1643 1299 1005  855  645  545  438  350  246  182  117   78   77   55   46 
    ##   17   18   19   20   21   22   23   24   26   27   28   29   32 
    ##   29   14   14    9   11    4    6    1    1    1    1    3    1 
    ## 
    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   1.000   2.000   3.000   4.409   6.000  32.000 
    ## 
    ## includes extended item information - examples:
    ##             labels
    ## 1 abrasive cleaner
    ## 2 artif. sweetener
    ## 3   baby cosmetics

The bar graph below shows the items that have frequency above 10%
support. As we expected, we got “whole milk” as the highest, followed by
“other vegetables” and “rolls/buns”.

    itemFrequencyPlot(transactions, support = 0.1, main = "item frequency plot above support 10%")

![](Figs/unnamed-chunk-39-1.png) The graph below shows top 30 items with
highest item frequency.

    itemFrequencyPlot(transactions, topN=30, main = "Top 30 Item Frequency")

![](Figs/unnamed-chunk-40-1.png) We ran the “apriori” function. When we
inspected, we could observe that “bottled water”, “tropical fruit”,
“root vegetables”, “soda”, “yogurt”, “rolls/buns”, “other vegetables”
and “whole milk” have empty Left Hand Side (LHS). This means that these
items are so popular items that these item is most likely to be
purchased no matter what conditional probability of LHS. It is also
worthy to note that the lift values of these popular items are 1.

    # Run apriori
    itemrules = apriori(transactions, parameter=list(support=.005, confidence=.1, maxlen=5))

    ## Apriori
    ## 
    ## Parameter specification:
    ##  confidence minval smax arem  aval originalSupport maxtime support minlen
    ##         0.1    0.1    1 none FALSE            TRUE       5   0.005      1
    ##  maxlen target  ext
    ##       5  rules TRUE
    ## 
    ## Algorithmic control:
    ##  filter tree heap memopt load sort verbose
    ##     0.1 TRUE TRUE  FALSE TRUE    2    TRUE
    ## 
    ## Absolute minimum support count: 49 
    ## 
    ## set item appearances ...[0 item(s)] done [0.00s].
    ## set transactions ...[169 item(s), 9835 transaction(s)] done [0.00s].
    ## sorting and recoding items ... [120 item(s)] done [0.00s].
    ## creating transaction tree ... done [0.00s].
    ## checking subsets of size 1 2 3 4 done [0.00s].
    ## writing ... [1582 rule(s)] done [0.00s].
    ## creating S4 object  ... done [0.00s].

    inspect(itemrules)

    ##        lhs                           rhs                            support confidence    coverage      lift count
    ## [1]    {}                         => {bottled water}            0.110523640  0.1105236 1.000000000 1.0000000  1087
    ## [2]    {}                         => {tropical fruit}           0.104931368  0.1049314 1.000000000 1.0000000  1032
    ## [3]    {}                         => {root vegetables}          0.108998475  0.1089985 1.000000000 1.0000000  1072
    ## [4]    {}                         => {soda}                     0.174377224  0.1743772 1.000000000 1.0000000  1715
    ## [5]    {}                         => {yogurt}                   0.139501779  0.1395018 1.000000000 1.0000000  1372
    ## [6]    {}                         => {rolls/buns}               0.183934926  0.1839349 1.000000000 1.0000000  1809
    ## [7]    {}                         => {other vegetables}         0.193492628  0.1934926 1.000000000 1.0000000  1903
    ## [8]    {}                         => {whole milk}               0.255516014  0.2555160 1.000000000 1.0000000  2513
    ## [9]    {cake bar}                 => {whole milk}               0.005592272  0.4230769 0.013218099 1.6557746    55
    ## [10]   {dishes}                   => {other vegetables}         0.005998983  0.3410405 0.017590239 1.7625502    59
    ## [11]   {dishes}                   => {whole milk}               0.005287239  0.3005780 0.017590239 1.1763569    52
    ## [12]   {mustard}                  => {whole milk}               0.005185562  0.4322034 0.011997966 1.6914924    51
    ## [13]   {pot plants}               => {whole milk}               0.006914082  0.4000000 0.017285206 1.5654596    68
    ## [14]   {chewing gum}              => {soda}                     0.005388917  0.2560386 0.021047280 1.4683033    53
    ## [15]   {chewing gum}              => {whole milk}               0.005083884  0.2415459 0.021047280 0.9453259    50
    ## [16]   {canned fish}              => {other vegetables}         0.005083884  0.3378378 0.015048297 1.7459985    50
    ## [17]   {pasta}                    => {whole milk}               0.006100661  0.4054054 0.015048297 1.5866145    60
    ## [18]   {herbs}                    => {root vegetables}          0.007015760  0.4312500 0.016268429 3.9564774    69
    ## [19]   {herbs}                    => {other vegetables}         0.007727504  0.4750000 0.016268429 2.4548739    76
    ## [20]   {herbs}                    => {whole milk}               0.007727504  0.4750000 0.016268429 1.8589833    76
    ## [21]   {processed cheese}         => {soda}                     0.005287239  0.3190184 0.016573462 1.8294729    52
    ## [22]   {processed cheese}         => {other vegetables}         0.005490595  0.3312883 0.016573462 1.7121497    54
    ## [23]   {processed cheese}         => {whole milk}               0.007015760  0.4233129 0.016573462 1.6566981    69
    ## [24]   {semi-finished bread}      => {other vegetables}         0.005185562  0.2931034 0.017691917 1.5148042    51
    ## [25]   {semi-finished bread}      => {whole milk}               0.007117438  0.4022989 0.017691917 1.5744565    70
    ## [26]   {beverages}                => {yogurt}                   0.005490595  0.2109375 0.026029487 1.5120775    54
    ## [27]   {beverages}                => {rolls/buns}               0.005388917  0.2070312 0.026029487 1.1255679    53
    ## [28]   {beverages}                => {other vegetables}         0.005185562  0.1992188 0.026029487 1.0295935    51
    ## [29]   {beverages}                => {whole milk}               0.006812405  0.2617188 0.026029487 1.0242753    67
    ## [30]   {ice cream}                => {soda}                     0.006100661  0.2439024 0.025012710 1.3987058    60
    ## [31]   {ice cream}                => {other vegetables}         0.005083884  0.2032520 0.025012710 1.0504381    50
    ## [32]   {ice cream}                => {whole milk}               0.005897306  0.2357724 0.025012710 0.9227303    58
    ## [33]   {detergent}                => {other vegetables}         0.006405694  0.3333333 0.019217082 1.7227185    63
    ## [34]   {detergent}                => {whole milk}               0.008947636  0.4656085 0.019217082 1.8222281    88
    ## [35]   {pickled vegetables}       => {other vegetables}         0.006405694  0.3579545 0.017895272 1.8499648    63
    ## [36]   {pickled vegetables}       => {whole milk}               0.007117438  0.3977273 0.017895272 1.5565650    70
    ## [37]   {baking powder}            => {other vegetables}         0.007320793  0.4137931 0.017691917 2.1385471    72
    ## [38]   {baking powder}            => {whole milk}               0.009252669  0.5229885 0.017691917 2.0467935    91
    ## [39]   {flour}                    => {other vegetables}         0.006304016  0.3625731 0.017386884 1.8738342    62
    ## [40]   {flour}                    => {whole milk}               0.008439248  0.4853801 0.017386884 1.8996074    83
    ## [41]   {soft cheese}              => {yogurt}                   0.005998983  0.3511905 0.017081851 2.5174623    59
    ## [42]   {soft cheese}              => {rolls/buns}               0.005388917  0.3154762 0.017081851 1.7151511    53
    ## [43]   {soft cheese}              => {other vegetables}         0.007117438  0.4166667 0.017081851 2.1533981    70
    ## [44]   {soft cheese}              => {whole milk}               0.007524148  0.4404762 0.017081851 1.7238692    74
    ## [45]   {specialty bar}            => {soda}                     0.007219115  0.2639405 0.027351296 1.5136181    71
    ## [46]   {specialty bar}            => {rolls/buns}               0.005592272  0.2044610 0.027351296 1.1115940    55
    ## [47]   {specialty bar}            => {other vegetables}         0.005592272  0.2044610 0.027351296 1.0566861    55
    ## [48]   {specialty bar}            => {whole milk}               0.006507372  0.2379182 0.027351296 0.9311284    64
    ## [49]   {misc. beverages}          => {bottled water}            0.005287239  0.1863799 0.028368073 1.6863354    52
    ## [50]   {misc. beverages}          => {soda}                     0.007320793  0.2580645 0.028368073 1.4799210    72
    ## [51]   {misc. beverages}          => {other vegetables}         0.005592272  0.1971326 0.028368073 1.0188120    55
    ## [52]   {misc. beverages}          => {whole milk}               0.007015760  0.2473118 0.028368073 0.9678917    69
    ## [53]   {grapes}                   => {tropical fruit}           0.006100661  0.2727273 0.022369090 2.5991015    60
    ## [54]   {grapes}                   => {other vegetables}         0.009049314  0.4045455 0.022369090 2.0907538    89
    ## [55]   {grapes}                   => {whole milk}               0.007320793  0.3272727 0.022369090 1.2808306    72
    ## [56]   {cat food}                 => {yogurt}                   0.006202339  0.2663755 0.023284189 1.9094778    61
    ## [57]   {cat food}                 => {other vegetables}         0.006507372  0.2794760 0.023284189 1.4443753    64
    ## [58]   {cat food}                 => {whole milk}               0.008845958  0.3799127 0.023284189 1.4868448    87
    ## [59]   {specialty chocolate}      => {soda}                     0.006304016  0.2073579 0.030401627 1.1891338    62
    ## [60]   {specialty chocolate}      => {rolls/buns}               0.005592272  0.1839465 0.030401627 1.0000629    55
    ## [61]   {specialty chocolate}      => {other vegetables}         0.006100661  0.2006689 0.030401627 1.0370881    60
    ## [62]   {specialty chocolate}      => {whole milk}               0.008032537  0.2642140 0.030401627 1.0340410    79
    ## [63]   {meat}                     => {sausage}                  0.005287239  0.2047244 0.025826131 2.1790742    52
    ## [64]   {meat}                     => {root vegetables}          0.005083884  0.1968504 0.025826131 1.8059922    50
    ## [65]   {meat}                     => {soda}                     0.005490595  0.2125984 0.025826131 1.2191869    54
    ## [66]   {meat}                     => {yogurt}                   0.005287239  0.2047244 0.025826131 1.4675398    52
    ## [67]   {meat}                     => {rolls/buns}               0.006914082  0.2677165 0.025826131 1.4554959    68
    ## [68]   {meat}                     => {other vegetables}         0.009964413  0.3858268 0.025826131 1.9940128    98
    ## [69]   {meat}                     => {whole milk}               0.009964413  0.3858268 0.025826131 1.5099906    98
    ## [70]   {frozen meals}             => {tropical fruit}           0.005490595  0.1935484 0.028368073 1.8445236    54
    ## [71]   {frozen meals}             => {soda}                     0.006202339  0.2186380 0.028368073 1.2538220    61
    ## [72]   {frozen meals}             => {yogurt}                   0.006202339  0.2186380 0.028368073 1.5672774    61
    ## [73]   {frozen meals}             => {other vegetables}         0.007524148  0.2652330 0.028368073 1.3707653    74
    ## [74]   {frozen meals}             => {whole milk}               0.009862735  0.3476703 0.028368073 1.3606593    97
    ## [75]   {hard cheese}              => {sausage}                  0.005185562  0.2116183 0.024504321 2.2524519    51
    ## [76]   {hard cheese}              => {root vegetables}          0.005592272  0.2282158 0.024504321 2.0937519    55
    ## [77]   {hard cheese}              => {yogurt}                   0.006405694  0.2614108 0.024504321 1.8738886    63
    ## [78]   {hard cheese}              => {rolls/buns}               0.005897306  0.2406639 0.024504321 1.3084187    58
    ## [79]   {hard cheese}              => {other vegetables}         0.009456024  0.3858921 0.024504321 1.9943505    93
    ## [80]   {hard cheese}              => {whole milk}               0.010066090  0.4107884 0.024504321 1.6076815    99
    ## [81]   {butter milk}              => {pip fruit}                0.005083884  0.1818182 0.027961362 2.4034702    50
    ## [82]   {butter milk}              => {tropical fruit}           0.005490595  0.1963636 0.027961362 1.8713531    54
    ## [83]   {butter milk}              => {root vegetables}          0.005083884  0.1818182 0.027961362 1.6680801    50
    ## [84]   {butter milk}              => {yogurt}                   0.008540925  0.3054545 0.027961362 2.1896104    84
    ## [85]   {butter milk}              => {rolls/buns}               0.007625826  0.2727273 0.027961362 1.4827378    75
    ## [86]   {butter milk}              => {other vegetables}         0.010371124  0.3709091 0.027961362 1.9169159   102
    ## [87]   {butter milk}              => {whole milk}               0.011591256  0.4145455 0.027961362 1.6223854   114
    ## [88]   {candy}                    => {tropical fruit}           0.005388917  0.1802721 0.029893238 1.7180002    53
    ## [89]   {candy}                    => {soda}                     0.008642603  0.2891156 0.029893238 1.6579897    85
    ## [90]   {candy}                    => {yogurt}                   0.005490595  0.1836735 0.029893238 1.3166389    54
    ## [91]   {candy}                    => {rolls/buns}               0.007117438  0.2380952 0.029893238 1.2944537    70
    ## [92]   {candy}                    => {other vegetables}         0.006914082  0.2312925 0.029893238 1.1953557    68
    ## [93]   {candy}                    => {whole milk}               0.008235892  0.2755102 0.029893238 1.0782502    81
    ## [94]   {ham}                      => {white bread}              0.005083884  0.1953125 0.026029487 4.6398513    50
    ## [95]   {white bread}              => {ham}                      0.005083884  0.1207729 0.042094560 4.6398513    50
    ## [96]   {ham}                      => {tropical fruit}           0.005388917  0.2070312 0.026029487 1.9730158    53
    ## [97]   {ham}                      => {yogurt}                   0.006710727  0.2578125 0.026029487 1.8480947    66
    ## [98]   {ham}                      => {rolls/buns}               0.006914082  0.2656250 0.026029487 1.4441249    68
    ## [99]   {ham}                      => {other vegetables}         0.009150991  0.3515625 0.026029487 1.8169297    90
    ## [100]  {ham}                      => {whole milk}               0.011489578  0.4414062 0.026029487 1.7275091   113
    ## [101]  {sliced cheese}            => {sausage}                  0.007015760  0.2863071 0.024504321 3.0474349    69
    ## [102]  {sliced cheese}            => {tropical fruit}           0.005287239  0.2157676 0.024504321 2.0562739    52
    ## [103]  {sliced cheese}            => {root vegetables}          0.005592272  0.2282158 0.024504321 2.0937519    55
    ## [104]  {sliced cheese}            => {soda}                     0.005083884  0.2074689 0.024504321 1.1897705    50
    ## [105]  {sliced cheese}            => {yogurt}                   0.008032537  0.3278008 0.024504321 2.3497968    79
    ## [106]  {sliced cheese}            => {rolls/buns}               0.007625826  0.3112033 0.024504321 1.6919208    75
    ## [107]  {sliced cheese}            => {other vegetables}         0.009049314  0.3692946 0.024504321 1.9085720    89
    ## [108]  {sliced cheese}            => {whole milk}               0.010777834  0.4398340 0.024504321 1.7213560   106
    ## [109]  {UHT-milk}                 => {bottled water}            0.007320793  0.2188450 0.033451957 1.9800740    72
    ## [110]  {UHT-milk}                 => {soda}                     0.007625826  0.2279635 0.033451957 1.3073010    75
    ## [111]  {UHT-milk}                 => {yogurt}                   0.007422471  0.2218845 0.033451957 1.5905496    73
    ## [112]  {UHT-milk}                 => {rolls/buns}               0.006405694  0.1914894 0.033451957 1.0410712    63
    ## [113]  {UHT-milk}                 => {other vegetables}         0.008134215  0.2431611 0.033451957 1.2566944    80
    ## [114]  {oil}                      => {root vegetables}          0.007015760  0.2500000 0.028063040 2.2936101    69
    ## [115]  {oil}                      => {yogurt}                   0.005287239  0.1884058 0.028063040 1.3505620    52
    ## [116]  {oil}                      => {rolls/buns}               0.005083884  0.1811594 0.028063040 0.9849104    50
    ## [117]  {oil}                      => {other vegetables}         0.009964413  0.3550725 0.028063040 1.8350697    98
    ## [118]  {oil}                      => {whole milk}               0.011286223  0.4021739 0.028063040 1.5739675   111
    ## [119]  {onions}                   => {whipped/sour cream}       0.005083884  0.1639344 0.031011693 2.2869434    50
    ## [120]  {onions}                   => {citrus fruit}             0.005592272  0.1803279 0.031011693 2.1787771    55
    ## [121]  {onions}                   => {bottled water}            0.005897306  0.1901639 0.031011693 1.7205725    58
    ## [122]  {onions}                   => {tropical fruit}           0.005693950  0.1836066 0.031011693 1.7497776    56
    ## [123]  {onions}                   => {root vegetables}          0.009456024  0.3049180 0.031011693 2.7974523    93
    ## [124]  {onions}                   => {soda}                     0.005287239  0.1704918 0.031011693 0.9777183    52
    ## [125]  {onions}                   => {yogurt}                   0.007219115  0.2327869 0.031011693 1.6687019    71
    ## [126]  {onions}                   => {rolls/buns}               0.006812405  0.2196721 0.031011693 1.1942927    67
    ## [127]  {onions}                   => {other vegetables}         0.014234875  0.4590164 0.031011693 2.3722681   140
    ## [128]  {onions}                   => {whole milk}               0.012099644  0.3901639 0.031011693 1.5269647   119
    ## [129]  {berries}                  => {whipped/sour cream}       0.009049314  0.2721713 0.033248602 3.7968855    89
    ## [130]  {whipped/sour cream}       => {berries}                  0.009049314  0.1262411 0.071682766 3.7968855    89
    ## [131]  {berries}                  => {citrus fruit}             0.005388917  0.1620795 0.033248602 1.9582948    53
    ## [132]  {berries}                  => {tropical fruit}           0.006710727  0.2018349 0.033248602 1.9234941    66
    ## [133]  {berries}                  => {root vegetables}          0.006609049  0.1987768 0.033248602 1.8236655    65
    ## [134]  {berries}                  => {soda}                     0.007320793  0.2201835 0.033248602 1.2626849    72
    ## [135]  {berries}                  => {yogurt}                   0.010574479  0.3180428 0.033248602 2.2798477   104
    ## [136]  {berries}                  => {rolls/buns}               0.006609049  0.1987768 0.033248602 1.0806907    65
    ## [137]  {berries}                  => {other vegetables}         0.010269446  0.3088685 0.033248602 1.5962805   101
    ## [138]  {berries}                  => {whole milk}               0.011794611  0.3547401 0.033248602 1.3883281   116
    ## [139]  {hamburger meat}           => {sausage}                  0.005185562  0.1559633 0.033248602 1.6600639    51
    ## [140]  {hamburger meat}           => {root vegetables}          0.006202339  0.1865443 0.033248602 1.7114399    61
    ## [141]  {hamburger meat}           => {soda}                     0.005795628  0.1743119 0.033248602 0.9996255    57
    ## [142]  {hamburger meat}           => {yogurt}                   0.006507372  0.1957187 0.033248602 1.4029832    64
    ## [143]  {hamburger meat}           => {rolls/buns}               0.008642603  0.2599388 0.033248602 1.4132109    85
    ## [144]  {hamburger meat}           => {other vegetables}         0.013828165  0.4159021 0.033248602 2.1494470   136
    ## [145]  {hamburger meat}           => {whole milk}               0.014743264  0.4434251 0.033248602 1.7354101   145
    ## [146]  {hygiene articles}         => {napkins}                  0.006100661  0.1851852 0.032943569 3.5364977    60
    ## [147]  {napkins}                  => {hygiene articles}         0.006100661  0.1165049 0.052364006 3.5364977    60
    ## [148]  {hygiene articles}         => {citrus fruit}             0.005287239  0.1604938 0.032943569 1.9391361    52
    ## [149]  {hygiene articles}         => {shopping bags}            0.005185562  0.1574074 0.032943569 1.5976283    51
    ## [150]  {hygiene articles}         => {bottled water}            0.005693950  0.1728395 0.032943569 1.5638239    56
    ## [151]  {hygiene articles}         => {tropical fruit}           0.006710727  0.2037037 0.032943569 1.9413042    66
    ## [152]  {hygiene articles}         => {root vegetables}          0.005388917  0.1635802 0.032943569 1.5007572    53
    ## [153]  {hygiene articles}         => {soda}                     0.007015760  0.2129630 0.032943569 1.2212774    69
    ## [154]  {hygiene articles}         => {yogurt}                   0.007320793  0.2222222 0.032943569 1.5929705    72
    ## [155]  {hygiene articles}         => {rolls/buns}               0.005897306  0.1790123 0.032943569 0.9732374    58
    ## [156]  {hygiene articles}         => {other vegetables}         0.009557702  0.2901235 0.032943569 1.4994032    94
    ## [157]  {hygiene articles}         => {whole milk}               0.012811388  0.3888889 0.032943569 1.5219746   126
    ## [158]  {salty snack}              => {fruit/vegetable juice}    0.005998983  0.1586022 0.037824098 2.1938849    59
    ## [159]  {salty snack}              => {whipped/sour cream}       0.005185562  0.1370968 0.037824098 1.9125486    51
    ## [160]  {salty snack}              => {pastry}                   0.005185562  0.1370968 0.037824098 1.5409677    51
    ## [161]  {salty snack}              => {shopping bags}            0.005998983  0.1586022 0.037824098 1.6097545    59
    ## [162]  {salty snack}              => {sausage}                  0.005287239  0.1397849 0.037824098 1.4878625    52
    ## [163]  {salty snack}              => {tropical fruit}           0.005592272  0.1478495 0.037824098 1.4090111    55
    ## [164]  {salty snack}              => {soda}                     0.009354347  0.2473118 0.037824098 1.4182576    92
    ## [165]  {salty snack}              => {yogurt}                   0.006202339  0.1639785 0.037824098 1.1754581    61
    ## [166]  {salty snack}              => {other vegetables}         0.010777834  0.2849462 0.037824098 1.4726465   106
    ## [167]  {salty snack}              => {whole milk}               0.011184545  0.2956989 0.037824098 1.1572618   110
    ## [168]  {sugar}                    => {margarine}                0.005490595  0.1621622 0.033858668 2.7688626    54
    ## [169]  {sugar}                    => {pastry}                   0.005185562  0.1531532 0.033858668 1.7214414    51
    ## [170]  {sugar}                    => {root vegetables}          0.006405694  0.1891892 0.033858668 1.7357049    63
    ## [171]  {sugar}                    => {soda}                     0.007320793  0.2162162 0.033858668 1.2399338    72
    ## [172]  {sugar}                    => {yogurt}                   0.006914082  0.2042042 0.033858668 1.4638107    68
    ## [173]  {sugar}                    => {rolls/buns}               0.007015760  0.2072072 0.033858668 1.1265245    69
    ## [174]  {sugar}                    => {other vegetables}         0.010777834  0.3183183 0.033858668 1.6451186   106
    ## [175]  {sugar}                    => {whole milk}               0.015048297  0.4444444 0.033858668 1.7393996   148
    ## [176]  {waffles}                  => {chocolate}                0.005795628  0.1507937 0.038434164 3.0390483    57
    ## [177]  {chocolate}                => {waffles}                  0.005795628  0.1168033 0.049618709 3.0390483    57
    ## [178]  {waffles}                  => {whipped/sour cream}       0.005083884  0.1322751 0.038434164 1.8452850    50
    ## [179]  {waffles}                  => {pastry}                   0.007015760  0.1825397 0.038434164 2.0517460    69
    ## [180]  {waffles}                  => {shopping bags}            0.005490595  0.1428571 0.038434164 1.4499484    54
    ## [181]  {waffles}                  => {tropical fruit}           0.006100661  0.1587302 0.038434164 1.5127046    60
    ## [182]  {waffles}                  => {root vegetables}          0.006609049  0.1719577 0.038434164 1.5776154    65
    ## [183]  {waffles}                  => {soda}                     0.009557702  0.2486772 0.038434164 1.4260879    94
    ## [184]  {waffles}                  => {yogurt}                   0.007524148  0.1957672 0.038434164 1.4033312    74
    ## [185]  {waffles}                  => {rolls/buns}               0.009150991  0.2380952 0.038434164 1.2944537    90
    ## [186]  {waffles}                  => {other vegetables}         0.010066090  0.2619048 0.038434164 1.3535645    99
    ## [187]  {waffles}                  => {whole milk}               0.012709710  0.3306878 0.038434164 1.2941961   125
    ## [188]  {long life bakery product} => {chocolate}                0.005287239  0.1413043 0.037417387 2.8478038    52
    ## [189]  {chocolate}                => {long life bakery product} 0.005287239  0.1065574 0.049618709 2.8478038    52
    ## [190]  {long life bakery product} => {fruit/vegetable juice}    0.006202339  0.1657609 0.037417387 2.2929088    61
    ## [191]  {long life bakery product} => {whipped/sour cream}       0.005795628  0.1548913 0.037417387 2.1607886    57
    ## [192]  {long life bakery product} => {pastry}                   0.005897306  0.1576087 0.037417387 1.7715217    58
    ## [193]  {long life bakery product} => {shopping bags}            0.005388917  0.1440217 0.037417387 1.4617686    53
    ## [194]  {long life bakery product} => {sausage}                  0.005388917  0.1440217 0.037417387 1.5329587    53
    ## [195]  {long life bakery product} => {tropical fruit}           0.006304016  0.1684783 0.037417387 1.6056044    62
    ## [196]  {long life bakery product} => {root vegetables}          0.005287239  0.1413043 0.037417387 1.2963883    52
    ## [197]  {long life bakery product} => {soda}                     0.007625826  0.2038043 0.037417387 1.1687555    75
    ## [198]  {long life bakery product} => {yogurt}                   0.008744281  0.2336957 0.037417387 1.6752163    86
    ## [199]  {long life bakery product} => {rolls/buns}               0.007930859  0.2119565 0.037417387 1.1523452    78
    ## [200]  {long life bakery product} => {other vegetables}         0.010676157  0.2853261 0.037417387 1.4746096   105
    ## [201]  {long life bakery product} => {whole milk}               0.013523132  0.3614130 0.037417387 1.4144438   133
    ## [202]  {dessert}                  => {curd}                     0.005185562  0.1397260 0.037112354 2.6225295    51
    ## [203]  {dessert}                  => {fruit/vegetable juice}    0.005998983  0.1616438 0.037112354 2.2359594    59
    ## [204]  {dessert}                  => {pastry}                   0.005388917  0.1452055 0.037112354 1.6321096    53
    ## [205]  {dessert}                  => {shopping bags}            0.006202339  0.1671233 0.037112354 1.6962410    61
    ## [206]  {dessert}                  => {sausage}                  0.005897306  0.1589041 0.037112354 1.6913657    58
    ## [207]  {dessert}                  => {bottled water}            0.005185562  0.1397260 0.037112354 1.2642185    51
    ## [208]  {dessert}                  => {tropical fruit}           0.006304016  0.1698630 0.037112354 1.6188011    62
    ## [209]  {dessert}                  => {root vegetables}          0.005795628  0.1561644 0.037112354 1.4327208    57
    ## [210]  {dessert}                  => {soda}                     0.009862735  0.2657534 0.037112354 1.5240145    97
    ## [211]  {dessert}                  => {yogurt}                   0.009862735  0.2657534 0.037112354 1.9050182    97
    ## [212]  {dessert}                  => {rolls/buns}               0.006812405  0.1835616 0.037112354 0.9979706    67
    ## [213]  {dessert}                  => {other vegetables}         0.011591256  0.3123288 0.037112354 1.6141636   114
    ## [214]  {dessert}                  => {whole milk}               0.013726487  0.3698630 0.037112354 1.4475140   135
    ## [215]  {canned beer}              => {shopping bags}            0.011387900  0.1465969 0.077681749 1.4879052   112
    ## [216]  {shopping bags}            => {canned beer}              0.011387900  0.1155831 0.098525674 1.4879052   112
    ## [217]  {canned beer}              => {bottled water}            0.008032537  0.1034031 0.077681749 0.9355749    79
    ## [218]  {canned beer}              => {soda}                     0.013828165  0.1780105 0.077681749 1.0208356   136
    ## [219]  {canned beer}              => {rolls/buns}               0.011286223  0.1452880 0.077681749 0.7898878   111
    ## [220]  {canned beer}              => {other vegetables}         0.009049314  0.1164921 0.077681749 0.6020495    89
    ## [221]  {canned beer}              => {whole milk}               0.008845958  0.1138743 0.077681749 0.4456642    87
    ## [222]  {cream cheese}             => {curd}                     0.005083884  0.1282051 0.039654296 2.4062928    50
    ## [223]  {cream cheese}             => {domestic eggs}            0.005083884  0.1282051 0.039654296 2.0206690    50
    ## [224]  {cream cheese}             => {fruit/vegetable juice}    0.005693950  0.1435897 0.039654296 1.9862238    56
    ## [225]  {cream cheese}             => {whipped/sour cream}       0.006405694  0.1615385 0.039654296 2.2535188    63
    ## [226]  {cream cheese}             => {pip fruit}                0.006100661  0.1538462 0.039654296 2.0337055    60
    ## [227]  {cream cheese}             => {citrus fruit}             0.005693950  0.1435897 0.039654296 1.7348957    56
    ## [228]  {cream cheese}             => {shopping bags}            0.005592272  0.1410256 0.039654296 1.4313593    55
    ## [229]  {cream cheese}             => {sausage}                  0.005592272  0.1410256 0.039654296 1.5010684    55
    ## [230]  {cream cheese}             => {bottled water}            0.005897306  0.1487179 0.039654296 1.3455759    58
    ## [231]  {cream cheese}             => {tropical fruit}           0.007219115  0.1820513 0.039654296 1.7349558    71
    ## [232]  {cream cheese}             => {root vegetables}          0.007524148  0.1897436 0.039654296 1.7407912    74
    ## [233]  {cream cheese}             => {soda}                     0.006812405  0.1717949 0.039654296 0.9851910    67
    ## [234]  {cream cheese}             => {yogurt}                   0.012404677  0.3128205 0.039654296 2.2424123   122
    ## [235]  {cream cheese}             => {rolls/buns}               0.009964413  0.2512821 0.039654296 1.3661465    98
    ## [236]  {cream cheese}             => {other vegetables}         0.013726487  0.3461538 0.039654296 1.7889769   135
    ## [237]  {cream cheese}             => {whole milk}               0.016471784  0.4153846 0.039654296 1.6256696   162
    ## [238]  {chicken}                  => {frozen vegetables}        0.006710727  0.1563981 0.042907982 3.2519564    66
    ## [239]  {frozen vegetables}        => {chicken}                  0.006710727  0.1395349 0.048093543 3.2519564    66
    ## [240]  {chicken}                  => {pork}                     0.005795628  0.1350711 0.042907982 2.3428998    57
    ## [241]  {pork}                     => {chicken}                  0.005795628  0.1005291 0.057651246 2.3428998    57
    ## [242]  {chicken}                  => {butter}                   0.005795628  0.1350711 0.042907982 2.4374755    57
    ## [243]  {butter}                   => {chicken}                  0.005795628  0.1045872 0.055414337 2.4374755    57
    ## [244]  {chicken}                  => {newspapers}               0.005185562  0.1208531 0.042907982 1.5141274    51
    ## [245]  {chicken}                  => {domestic eggs}            0.006202339  0.1445498 0.042907982 2.2782803    61
    ## [246]  {chicken}                  => {whipped/sour cream}       0.007219115  0.1682464 0.042907982 2.3470976    71
    ## [247]  {whipped/sour cream}       => {chicken}                  0.007219115  0.1007092 0.071682766 2.3470976    71
    ## [248]  {chicken}                  => {citrus fruit}             0.006914082  0.1611374 0.042907982 1.9469124    68
    ## [249]  {chicken}                  => {sausage}                  0.005287239  0.1232227 0.042907982 1.3115755    52
    ## [250]  {chicken}                  => {bottled water}            0.005287239  0.1232227 0.042907982 1.1148995    52
    ## [251]  {chicken}                  => {tropical fruit}           0.006405694  0.1492891 0.042907982 1.4227309    63
    ## [252]  {chicken}                  => {root vegetables}          0.010879512  0.2535545 0.042907982 2.3262206   107
    ## [253]  {chicken}                  => {soda}                     0.008337570  0.1943128 0.042907982 1.1143244    82
    ## [254]  {chicken}                  => {yogurt}                   0.008337570  0.1943128 0.042907982 1.3929055    82
    ## [255]  {chicken}                  => {rolls/buns}               0.009659380  0.2251185 0.042907982 1.2239029    95
    ## [256]  {chicken}                  => {other vegetables}         0.017895272  0.4170616 0.042907982 2.1554393   176
    ## [257]  {chicken}                  => {whole milk}               0.017590239  0.4099526 0.042907982 1.6044106   173
    ## [258]  {white bread}              => {frankfurter}              0.005185562  0.1231884 0.042094560 2.0888931    51
    ## [259]  {white bread}              => {domestic eggs}            0.005795628  0.1376812 0.042094560 2.1700228    57
    ## [260]  {white bread}              => {fruit/vegetable juice}    0.007422471  0.1763285 0.042094560 2.4390869    73
    ## [261]  {fruit/vegetable juice}    => {white bread}              0.007422471  0.1026723 0.072292832 2.4390869    73
    ## [262]  {white bread}              => {whipped/sour cream}       0.005490595  0.1304348 0.042094560 1.8196115    54
    ## [263]  {white bread}              => {pip fruit}                0.006609049  0.1570048 0.042094560 2.0754604    65
    ## [264]  {white bread}              => {pastry}                   0.005592272  0.1328502 0.042094560 1.4932367    55
    ## [265]  {white bread}              => {shopping bags}            0.007422471  0.1763285 0.042094560 1.7896706    73
    ## [266]  {white bread}              => {sausage}                  0.007219115  0.1714976 0.042094560 1.8254099    71
    ## [267]  {white bread}              => {tropical fruit}           0.008744281  0.2077295 0.042094560 1.9796699    86
    ## [268]  {white bread}              => {root vegetables}          0.007930859  0.1884058 0.042094560 1.7285177    78
    ## [269]  {white bread}              => {soda}                     0.010269446  0.2439614 0.042094560 1.3990437   101
    ## [270]  {white bread}              => {yogurt}                   0.009049314  0.2149758 0.042094560 1.5410258    89
    ## [271]  {white bread}              => {rolls/buns}               0.006507372  0.1545894 0.042094560 0.8404569    64
    ## [272]  {white bread}              => {other vegetables}         0.013726487  0.3260870 0.042094560 1.6852681   135
    ## [273]  {white bread}              => {whole milk}               0.017081851  0.4057971 0.042094560 1.5881474   168
    ## [274]  {chocolate}                => {butter}                   0.006202339  0.1250000 0.049618709 2.2557339    61
    ## [275]  {butter}                   => {chocolate}                0.006202339  0.1119266 0.055414337 2.2557339    61
    ## [276]  {chocolate}                => {newspapers}               0.005490595  0.1106557 0.049618709 1.3863684    54
    ## [277]  {chocolate}                => {fruit/vegetable juice}    0.006812405  0.1372951 0.049618709 1.8991521    67
    ## [278]  {chocolate}                => {pip fruit}                0.006100661  0.1229508 0.049618709 1.6252975    60
    ## [279]  {chocolate}                => {pastry}                   0.008032537  0.1618852 0.049618709 1.8195902    79
    ## [280]  {chocolate}                => {citrus fruit}             0.006405694  0.1290984 0.049618709 1.5598064    63
    ## [281]  {chocolate}                => {shopping bags}            0.008134215  0.1639344 0.049618709 1.6638752    80
    ## [282]  {chocolate}                => {sausage}                  0.006609049  0.1331967 0.049618709 1.4177378    65
    ## [283]  {chocolate}                => {bottled water}            0.005795628  0.1168033 0.049618709 1.0568172    57
    ## [284]  {chocolate}                => {tropical fruit}           0.008134215  0.1639344 0.049618709 1.5623014    80
    ## [285]  {chocolate}                => {root vegetables}          0.006405694  0.1290984 0.049618709 1.1844052    63
    ## [286]  {chocolate}                => {soda}                     0.013523132  0.2725410 0.049618709 1.5629391   133
    ## [287]  {chocolate}                => {yogurt}                   0.009252669  0.1864754 0.049618709 1.3367242    91
    ## [288]  {chocolate}                => {rolls/buns}               0.011794611  0.2377049 0.049618709 1.2923316   116
    ## [289]  {chocolate}                => {other vegetables}         0.012709710  0.2561475 0.049618709 1.3238103   125
    ## [290]  {chocolate}                => {whole milk}               0.016675140  0.3360656 0.049618709 1.3152427   164
    ## [291]  {coffee}                   => {fruit/vegetable juice}    0.005998983  0.1033275 0.058057956 1.4292910    59
    ## [292]  {coffee}                   => {whipped/sour cream}       0.006100661  0.1050788 0.058057956 1.4658866    60
    ## [293]  {coffee}                   => {pip fruit}                0.006914082  0.1190893 0.058057956 1.5742519    68
    ## [294]  {coffee}                   => {pastry}                   0.006914082  0.1190893 0.058057956 1.3385639    68
    ## [295]  {coffee}                   => {citrus fruit}             0.006405694  0.1103327 0.058057956 1.3330744    63
    ## [296]  {coffee}                   => {shopping bags}            0.009354347  0.1611208 0.058057956 1.6353183    92
    ## [297]  {coffee}                   => {sausage}                  0.006914082  0.1190893 0.058057956 1.2675795    68
    ## [298]  {coffee}                   => {bottled water}            0.007320793  0.1260946 0.058057956 1.1408833    72
    ## [299]  {coffee}                   => {tropical fruit}           0.007117438  0.1225919 0.058057956 1.1683060    70
    ## [300]  {coffee}                   => {root vegetables}          0.007320793  0.1260946 0.058057956 1.1568471    72
    ## [301]  {coffee}                   => {soda}                     0.009964413  0.1716287 0.058057956 0.9842382    98
    ## [302]  {coffee}                   => {yogurt}                   0.009761057  0.1681261 0.058057956 1.2051896    96
    ## [303]  {coffee}                   => {rolls/buns}               0.010981190  0.1891419 0.058057956 1.0283085   108
    ## [304]  {coffee}                   => {other vegetables}         0.013421454  0.2311734 0.058057956 1.1947400   132
    ## [305]  {coffee}                   => {whole milk}               0.018708693  0.3222417 0.058057956 1.2611408   184
    ## [306]  {frozen vegetables}        => {pork}                     0.006405694  0.1331924 0.048093543 2.3103124    63
    ## [307]  {pork}                     => {frozen vegetables}        0.006405694  0.1111111 0.057651246 2.3103124    63
    ## [308]  {frozen vegetables}        => {frankfurter}              0.005083884  0.1057082 0.048093543 1.7924838    50
    ## [309]  {frozen vegetables}        => {margarine}                0.005083884  0.1057082 0.048093543 1.8049316    50
    ## [310]  {frozen vegetables}        => {butter}                   0.005795628  0.1205074 0.048093543 2.1746611    57
    ## [311]  {butter}                   => {frozen vegetables}        0.005795628  0.1045872 0.055414337 2.1746611    57
    ## [312]  {frozen vegetables}        => {domestic eggs}            0.005185562  0.1078224 0.048093543 1.6994125    51
    ## [313]  {frozen vegetables}        => {fruit/vegetable juice}    0.007829181  0.1627907 0.048093543 2.2518235    77
    ## [314]  {fruit/vegetable juice}    => {frozen vegetables}        0.007829181  0.1082982 0.072292832 2.2518235    77
    ## [315]  {frozen vegetables}        => {whipped/sour cream}       0.007930859  0.1649049 0.048093543 2.3004813    78
    ## [316]  {whipped/sour cream}       => {frozen vegetables}        0.007930859  0.1106383 0.071682766 2.3004813    78
    ## [317]  {frozen vegetables}        => {pip fruit}                0.007320793  0.1522199 0.048093543 2.0122076    72
    ## [318]  {frozen vegetables}        => {citrus fruit}             0.006609049  0.1374207 0.048093543 1.6603597    65
    ## [319]  {frozen vegetables}        => {sausage}                  0.005998983  0.1247357 0.048093543 1.3276795    59
    ## [320]  {frozen vegetables}        => {bottled water}            0.006202339  0.1289641 0.048093543 1.1668459    61
    ## [321]  {frozen vegetables}        => {tropical fruit}           0.008744281  0.1818182 0.048093543 1.7327343    86
    ## [322]  {frozen vegetables}        => {root vegetables}          0.011591256  0.2410148 0.048093543 2.2111759   114
    ## [323]  {root vegetables}          => {frozen vegetables}        0.011591256  0.1063433 0.108998475 2.2111759   114
    ## [324]  {frozen vegetables}        => {soda}                     0.008642603  0.1797040 0.048093543 1.0305475    85
    ## [325]  {frozen vegetables}        => {yogurt}                   0.012404677  0.2579281 0.048093543 1.8489235   122
    ## [326]  {frozen vegetables}        => {rolls/buns}               0.010167768  0.2114165 0.048093543 1.1494092   100
    ## [327]  {frozen vegetables}        => {other vegetables}         0.017793594  0.3699789 0.048093543 1.9121083   175
    ## [328]  {frozen vegetables}        => {whole milk}               0.020437214  0.4249471 0.048093543 1.6630940   201
    ## [329]  {beef}                     => {pork}                     0.007625826  0.1453488 0.052465684 2.5211743    75
    ## [330]  {pork}                     => {beef}                     0.007625826  0.1322751 0.057651246 2.5211743    75
    ## [331]  {beef}                     => {margarine}                0.006202339  0.1182171 0.052465684 2.0185152    61
    ## [332]  {margarine}                => {beef}                     0.006202339  0.1059028 0.058566345 2.0185152    61
    ## [333]  {beef}                     => {butter}                   0.005795628  0.1104651 0.052465684 1.9934393    57
    ## [334]  {butter}                   => {beef}                     0.005795628  0.1045872 0.055414337 1.9934393    57
    ## [335]  {beef}                     => {newspapers}               0.006405694  0.1220930 0.052465684 1.5296623    63
    ## [336]  {beef}                     => {domestic eggs}            0.005998983  0.1143411 0.052465684 1.8021548    59
    ## [337]  {beef}                     => {whipped/sour cream}       0.006710727  0.1279070 0.052465684 1.7843477    66
    ## [338]  {beef}                     => {pastry}                   0.006304016  0.1201550 0.052465684 1.3505426    62
    ## [339]  {beef}                     => {citrus fruit}             0.008439248  0.1608527 0.052465684 1.9434723    83
    ## [340]  {citrus fruit}             => {beef}                     0.008439248  0.1019656 0.082765633 1.9434723    83
    ## [341]  {beef}                     => {sausage}                  0.005592272  0.1065891 0.052465684 1.1345284    55
    ## [342]  {beef}                     => {bottled water}            0.006202339  0.1182171 0.052465684 1.0696088    61
    ## [343]  {beef}                     => {tropical fruit}           0.007625826  0.1453488 0.052465684 1.3851801    75
    ## [344]  {beef}                     => {root vegetables}          0.017386884  0.3313953 0.052465684 3.0403668   171
    ## [345]  {root vegetables}          => {beef}                     0.017386884  0.1595149 0.108998475 3.0403668   171
    ## [346]  {beef}                     => {soda}                     0.008134215  0.1550388 0.052465684 0.8890998    80
    ## [347]  {beef}                     => {yogurt}                   0.011692933  0.2228682 0.052465684 1.5976012   115
    ## [348]  {beef}                     => {rolls/buns}               0.013624809  0.2596899 0.052465684 1.4118576   134
    ## [349]  {beef}                     => {other vegetables}         0.019725470  0.3759690 0.052465684 1.9430662   194
    ## [350]  {other vegetables}         => {beef}                     0.019725470  0.1019443 0.193492628 1.9430662   194
    ## [351]  {beef}                     => {whole milk}               0.021250635  0.4050388 0.052465684 1.5851795   209
    ## [352]  {curd}                     => {margarine}                0.006304016  0.1183206 0.053279105 2.0202833    62
    ## [353]  {margarine}                => {curd}                     0.006304016  0.1076389 0.058566345 2.0202833    62
    ## [354]  {curd}                     => {butter}                   0.006812405  0.1278626 0.053279105 2.3073920    67
    ## [355]  {butter}                   => {curd}                     0.006812405  0.1229358 0.055414337 2.3073920    67
    ## [356]  {curd}                     => {newspapers}               0.005693950  0.1068702 0.053279105 1.3389410    56
    ## [357]  {curd}                     => {domestic eggs}            0.006507372  0.1221374 0.053279105 1.9250343    64
    ## [358]  {domestic eggs}            => {curd}                     0.006507372  0.1025641 0.063446873 1.9250343    64
    ## [359]  {curd}                     => {whipped/sour cream}       0.010472801  0.1965649 0.053279105 2.7421499   103
    ## [360]  {whipped/sour cream}       => {curd}                     0.010472801  0.1460993 0.071682766 2.7421499   103
    ## [361]  {curd}                     => {pip fruit}                0.007829181  0.1469466 0.053279105 1.9424993    77
    ## [362]  {pip fruit}                => {curd}                     0.007829181  0.1034946 0.075648195 1.9424993    77
    ## [363]  {curd}                     => {pastry}                   0.007524148  0.1412214 0.053279105 1.5873282    74
    ## [364]  {curd}                     => {citrus fruit}             0.007117438  0.1335878 0.053279105 1.6140490    70
    ## [365]  {curd}                     => {shopping bags}            0.005388917  0.1011450 0.053279105 1.0265856    53
    ## [366]  {curd}                     => {sausage}                  0.007625826  0.1431298 0.053279105 1.5234646    75
    ## [367]  {curd}                     => {bottled water}            0.006100661  0.1145038 0.053279105 1.0360120    60
    ## [368]  {curd}                     => {tropical fruit}           0.010269446  0.1927481 0.053279105 1.8368968   101
    ## [369]  {curd}                     => {root vegetables}          0.010879512  0.2041985 0.053279105 1.8734067   107
    ## [370]  {curd}                     => {soda}                     0.008134215  0.1526718 0.053279105 0.8755258    80
    ## [371]  {curd}                     => {yogurt}                   0.017285206  0.3244275 0.053279105 2.3256154   170
    ## [372]  {yogurt}                   => {curd}                     0.017285206  0.1239067 0.139501779 2.3256154   170
    ## [373]  {curd}                     => {rolls/buns}               0.010066090  0.1889313 0.053279105 1.0271638    99
    ## [374]  {curd}                     => {other vegetables}         0.017183528  0.3225191 0.053279105 1.6668288   169
    ## [375]  {curd}                     => {whole milk}               0.026131164  0.4904580 0.053279105 1.9194805   257
    ## [376]  {whole milk}               => {curd}                     0.026131164  0.1022682 0.255516014 1.9194805   257
    ## [377]  {napkins}                  => {newspapers}               0.006202339  0.1184466 0.052364006 1.4839775    61
    ## [378]  {napkins}                  => {domestic eggs}            0.005998983  0.1145631 0.052364006 1.8056541    59
    ## [379]  {napkins}                  => {fruit/vegetable juice}    0.006914082  0.1320388 0.052364006 1.8264444    68
    ## [380]  {napkins}                  => {whipped/sour cream}       0.007219115  0.1378641 0.052364006 1.9232528    71
    ## [381]  {whipped/sour cream}       => {napkins}                  0.007219115  0.1007092 0.071682766 1.9232528    71
    ## [382]  {napkins}                  => {pip fruit}                0.006710727  0.1281553 0.052364006 1.6940965    66
    ## [383]  {napkins}                  => {pastry}                   0.007015760  0.1339806 0.052364006 1.5059417    69
    ## [384]  {napkins}                  => {citrus fruit}             0.007625826  0.1456311 0.052364006 1.7595596    75
    ## [385]  {napkins}                  => {shopping bags}            0.007219115  0.1378641 0.052364006 1.3992706    71
    ## [386]  {napkins}                  => {sausage}                  0.006710727  0.1281553 0.052364006 1.3640777    66
    ## [387]  {napkins}                  => {bottled water}            0.008642603  0.1650485 0.052364006 1.4933325    85
    ## [388]  {napkins}                  => {tropical fruit}           0.010066090  0.1922330 0.052364006 1.8319880    99
    ## [389]  {napkins}                  => {root vegetables}          0.009964413  0.1902913 0.052364006 1.7458158    98
    ## [390]  {napkins}                  => {soda}                     0.011997966  0.2291262 0.052364006 1.3139687   118
    ## [391]  {napkins}                  => {yogurt}                   0.012302999  0.2349515 0.052364006 1.6842183   121
    ## [392]  {napkins}                  => {rolls/buns}               0.011692933  0.2233010 0.052364006 1.2140216   115
    ## [393]  {napkins}                  => {other vegetables}         0.014438231  0.2757282 0.052364006 1.4250060   142
    ## [394]  {napkins}                  => {whole milk}               0.019725470  0.3766990 0.052364006 1.4742678   194
    ## [395]  {pork}                     => {frankfurter}              0.005897306  0.1022928 0.057651246 1.7345679    58
    ## [396]  {frankfurter}              => {pork}                     0.005897306  0.1000000 0.058973055 1.7345679    58
    ## [397]  {pork}                     => {margarine}                0.006405694  0.1111111 0.057651246 1.8971836    63
    ## [398]  {margarine}                => {pork}                     0.006405694  0.1093750 0.058566345 1.8971836    63
    ## [399]  {pork}                     => {newspapers}               0.006609049  0.1146384 0.057651246 1.4362664    65
    ## [400]  {pork}                     => {whipped/sour cream}       0.008235892  0.1428571 0.057651246 1.9929078    81
    ## [401]  {whipped/sour cream}       => {pork}                     0.008235892  0.1148936 0.071682766 1.9929078    81
    ## [402]  {pork}                     => {pip fruit}                0.006100661  0.1058201 0.057651246 1.3988451    60
    ## [403]  {pork}                     => {pastry}                   0.006304016  0.1093474 0.057651246 1.2290653    62
    ## [404]  {pork}                     => {citrus fruit}             0.006507372  0.1128748 0.057651246 1.3637880    64
    ## [405]  {pork}                     => {shopping bags}            0.006405694  0.1111111 0.057651246 1.1277376    63
    ## [406]  {pork}                     => {sausage}                  0.006507372  0.1128748 0.057651246 1.2014323    64
    ## [407]  {pork}                     => {bottled water}            0.007422471  0.1287478 0.057651246 1.1648892    73
    ## [408]  {pork}                     => {tropical fruit}           0.008540925  0.1481481 0.057651246 1.4118576    84
    ## [409]  {pork}                     => {root vegetables}          0.013624809  0.2363316 0.057651246 2.1682099   134
    ## [410]  {root vegetables}          => {pork}                     0.013624809  0.1250000 0.108998475 2.1682099   134
    ## [411]  {pork}                     => {soda}                     0.011896289  0.2063492 0.057651246 1.1833495   117
    ## [412]  {pork}                     => {yogurt}                   0.009557702  0.1657848 0.057651246 1.1884066    94
    ## [413]  {pork}                     => {rolls/buns}               0.011286223  0.1957672 0.057651246 1.0643286   111
    ## [414]  {pork}                     => {other vegetables}         0.021657346  0.3756614 0.057651246 1.9414764   213
    ## [415]  {other vegetables}         => {pork}                     0.021657346  0.1119285 0.193492628 1.9414764   213
    ## [416]  {pork}                     => {whole milk}               0.022165735  0.3844797 0.057651246 1.5047187   218
    ## [417]  {frankfurter}              => {brown bread}              0.007117438  0.1206897 0.058973055 1.8604745    70
    ## [418]  {brown bread}              => {frankfurter}              0.007117438  0.1097179 0.064870361 1.8604745    70
    ## [419]  {frankfurter}              => {margarine}                0.006405694  0.1086207 0.058973055 1.8546606    63
    ## [420]  {margarine}                => {frankfurter}              0.006405694  0.1093750 0.058566345 1.8546606    63
    ## [421]  {frankfurter}              => {domestic eggs}            0.007015760  0.1189655 0.058973055 1.8750414    69
    ## [422]  {domestic eggs}            => {frankfurter}              0.007015760  0.1105769 0.063446873 1.8750414    69
    ## [423]  {frankfurter}              => {whipped/sour cream}       0.006202339  0.1051724 0.058973055 1.4671925    61
    ## [424]  {frankfurter}              => {pip fruit}                0.007219115  0.1224138 0.058973055 1.6181985    71
    ## [425]  {frankfurter}              => {pastry}                   0.008337570  0.1413793 0.058973055 1.5891034    82
    ## [426]  {frankfurter}              => {citrus fruit}             0.006507372  0.1103448 0.058973055 1.3332204    64
    ## [427]  {frankfurter}              => {shopping bags}            0.008235892  0.1396552 0.058973055 1.4174496    81
    ## [428]  {frankfurter}              => {sausage}                  0.010066090  0.1706897 0.058973055 1.8168103    99
    ## [429]  {sausage}                  => {frankfurter}              0.010066090  0.1071429 0.093950178 1.8168103    99
    ## [430]  {frankfurter}              => {bottled water}            0.007320793  0.1241379 0.058973055 1.1231799    72
    ## [431]  {frankfurter}              => {tropical fruit}           0.009456024  0.1603448 0.058973055 1.5280924    93
    ## [432]  {frankfurter}              => {root vegetables}          0.010167768  0.1724138 0.058973055 1.5818001   100
    ## [433]  {frankfurter}              => {soda}                     0.011286223  0.1913793 0.058973055 1.0975018   111
    ## [434]  {frankfurter}              => {yogurt}                   0.011184545  0.1896552 0.058973055 1.3595179   110
    ## [435]  {frankfurter}              => {rolls/buns}               0.019217082  0.3258621 0.058973055 1.7716161   189
    ## [436]  {rolls/buns}               => {frankfurter}              0.019217082  0.1044776 0.183934926 1.7716161   189
    ## [437]  {frankfurter}              => {other vegetables}         0.016471784  0.2793103 0.058973055 1.4435193   162
    ## [438]  {frankfurter}              => {whole milk}               0.020538892  0.3482759 0.058973055 1.3630295   202
    ## [439]  {margarine}                => {bottled beer}             0.006100661  0.1041667 0.058566345 1.2935343    60
    ## [440]  {butter}                   => {bottled beer}             0.005795628  0.1045872 0.055414337 1.2987559    57
    ## [441]  {bottled beer}             => {bottled water}            0.015760041  0.1957071 0.080528724 1.7707259   155
    ## [442]  {bottled water}            => {bottled beer}             0.015760041  0.1425943 0.110523640 1.7707259   155
    ## [443]  {bottled beer}             => {tropical fruit}           0.008235892  0.1022727 0.080528724 0.9746631    81
    ## [444]  {bottled beer}             => {root vegetables}          0.009659380  0.1199495 0.080528724 1.1004695    95
    ## [445]  {bottled beer}             => {soda}                     0.016980173  0.2108586 0.080528724 1.2092094   167
    ## [446]  {bottled beer}             => {yogurt}                   0.009252669  0.1148990 0.080528724 0.8236382    91
    ## [447]  {bottled beer}             => {rolls/buns}               0.013624809  0.1691919 0.080528724 0.9198466   134
    ## [448]  {bottled beer}             => {other vegetables}         0.016166751  0.2007576 0.080528724 1.0375464   159
    ## [449]  {bottled beer}             => {whole milk}               0.020437214  0.2537879 0.080528724 0.9932367   201
    ## [450]  {brown bread}              => {margarine}                0.006507372  0.1003135 0.064870361 1.7128178    64
    ## [451]  {margarine}                => {brown bread}              0.006507372  0.1111111 0.058566345 1.7128178    64
    ## [452]  {butter}                   => {brown bread}              0.005795628  0.1045872 0.055414337 1.6122487    57
    ## [453]  {brown bread}              => {newspapers}               0.007625826  0.1175549 0.064870361 1.4728051    75
    ## [454]  {brown bread}              => {domestic eggs}            0.006812405  0.1050157 0.064870361 1.6551749    67
    ## [455]  {domestic eggs}            => {brown bread}              0.006812405  0.1073718 0.063446873 1.6551749    67
    ## [456]  {brown bread}              => {fruit/vegetable juice}    0.008337570  0.1285266 0.064870361 1.7778615    82
    ## [457]  {fruit/vegetable juice}    => {brown bread}              0.008337570  0.1153305 0.072292832 1.7778615    82
    ## [458]  {brown bread}              => {pip fruit}                0.007625826  0.1175549 0.064870361 1.5539678    75
    ## [459]  {pip fruit}                => {brown bread}              0.007625826  0.1008065 0.075648195 1.5539678    75
    ## [460]  {brown bread}              => {pastry}                   0.009659380  0.1489028 0.064870361 1.6736677    95
    ## [461]  {pastry}                   => {brown bread}              0.009659380  0.1085714 0.088967972 1.6736677    95
    ## [462]  {brown bread}              => {citrus fruit}             0.008337570  0.1285266 0.064870361 1.5528987    82
    ## [463]  {citrus fruit}             => {brown bread}              0.008337570  0.1007371 0.082765633 1.5528987    82
    ## [464]  {brown bread}              => {shopping bags}            0.009252669  0.1426332 0.064870361 1.4476758    91
    ## [465]  {brown bread}              => {sausage}                  0.010676157  0.1645768 0.064870361 1.7517455   105
    ## [466]  {sausage}                  => {brown bread}              0.010676157  0.1136364 0.093950178 1.7517455   105
    ## [467]  {brown bread}              => {bottled water}            0.008235892  0.1269592 0.064870361 1.1487067    81
    ## [468]  {brown bread}              => {tropical fruit}           0.010676157  0.1645768 0.064870361 1.5684233   105
    ## [469]  {tropical fruit}           => {brown bread}              0.010676157  0.1017442 0.104931368 1.5684233   105
    ## [470]  {brown bread}              => {root vegetables}          0.010167768  0.1567398 0.064870361 1.4380000   100
    ## [471]  {brown bread}              => {soda}                     0.012608033  0.1943574 0.064870361 1.1145800   124
    ## [472]  {brown bread}              => {yogurt}                   0.014539908  0.2241379 0.064870361 1.6067030   143
    ## [473]  {yogurt}                   => {brown bread}              0.014539908  0.1042274 0.139501779 1.6067030   143
    ## [474]  {brown bread}              => {rolls/buns}               0.012608033  0.1943574 0.064870361 1.0566637   124
    ## [475]  {brown bread}              => {other vegetables}         0.018708693  0.2884013 0.064870361 1.4905025   184
    ## [476]  {brown bread}              => {whole milk}               0.025216065  0.3887147 0.064870361 1.5212930   248
    ## [477]  {margarine}                => {butter}                   0.006710727  0.1145833 0.058566345 2.0677561    66
    ## [478]  {butter}                   => {margarine}                0.006710727  0.1211009 0.055414337 2.0677561    66
    ## [479]  {margarine}                => {newspapers}               0.007117438  0.1215278 0.058566345 1.5225805    70
    ## [480]  {margarine}                => {domestic eggs}            0.008337570  0.1423611 0.058566345 2.2437845    82
    ## [481]  {domestic eggs}            => {margarine}                0.008337570  0.1314103 0.063446873 2.2437845    82
    ## [482]  {margarine}                => {fruit/vegetable juice}    0.006202339  0.1059028 0.058566345 1.4649140    61
    ## [483]  {margarine}                => {whipped/sour cream}       0.006812405  0.1163194 0.058566345 1.6226975    67
    ## [484]  {margarine}                => {pip fruit}                0.008540925  0.1458333 0.058566345 1.9277834    84
    ## [485]  {pip fruit}                => {margarine}                0.008540925  0.1129032 0.075648195 1.9277834    84
    ## [486]  {margarine}                => {pastry}                   0.006812405  0.1163194 0.058566345 1.3074306    67
    ## [487]  {margarine}                => {citrus fruit}             0.007930859  0.1354167 0.058566345 1.6361461    78
    ## [488]  {margarine}                => {sausage}                  0.007117438  0.1215278 0.058566345 1.2935343    70
    ## [489]  {margarine}                => {bottled water}            0.010269446  0.1753472 0.058566345 1.5865133   101
    ## [490]  {margarine}                => {tropical fruit}           0.009354347  0.1597222 0.058566345 1.5221590    92
    ## [491]  {margarine}                => {root vegetables}          0.011082867  0.1892361 0.058566345 1.7361354   109
    ## [492]  {root vegetables}          => {margarine}                0.011082867  0.1016791 0.108998475 1.7361354   109
    ## [493]  {margarine}                => {soda}                     0.010167768  0.1736111 0.058566345 0.9956066   100
    ## [494]  {margarine}                => {yogurt}                   0.014234875  0.2430556 0.058566345 1.7423115   140
    ## [495]  {yogurt}                   => {margarine}                0.014234875  0.1020408 0.139501779 1.7423115   140
    ## [496]  {margarine}                => {rolls/buns}               0.014743264  0.2517361 0.058566345 1.3686151   145
    ## [497]  {margarine}                => {other vegetables}         0.019725470  0.3368056 0.058566345 1.7406635   194
    ## [498]  {other vegetables}         => {margarine}                0.019725470  0.1019443 0.193492628 1.7406635   194
    ## [499]  {margarine}                => {whole milk}               0.024199288  0.4131944 0.058566345 1.6170980   238
    ## [500]  {butter}                   => {newspapers}               0.005795628  0.1045872 0.055414337 1.3103372    57
    ## [501]  {butter}                   => {domestic eggs}            0.009659380  0.1743119 0.055414337 2.7473683    95
    ## [502]  {domestic eggs}            => {butter}                   0.009659380  0.1522436 0.063446873 2.7473683    95
    ## [503]  {butter}                   => {fruit/vegetable juice}    0.008032537  0.1449541 0.055414337 2.0050968    79
    ## [504]  {fruit/vegetable juice}    => {butter}                   0.008032537  0.1111111 0.072292832 2.0050968    79
    ## [505]  {butter}                   => {whipped/sour cream}       0.010167768  0.1834862 0.055414337 2.5596981   100
    ## [506]  {whipped/sour cream}       => {butter}                   0.010167768  0.1418440 0.071682766 2.5596981   100
    ## [507]  {butter}                   => {pip fruit}                0.007320793  0.1321101 0.055414337 1.7463747    72
    ## [508]  {butter}                   => {pastry}                   0.007625826  0.1376147 0.055414337 1.5467890    75
    ## [509]  {butter}                   => {citrus fruit}             0.009150991  0.1651376 0.055414337 1.9952438    90
    ## [510]  {citrus fruit}             => {butter}                   0.009150991  0.1105651 0.082765633 1.9952438    90
    ## [511]  {butter}                   => {sausage}                  0.008642603  0.1559633 0.055414337 1.6600639    85
    ## [512]  {butter}                   => {bottled water}            0.008947636  0.1614679 0.055414337 1.4609353    88
    ## [513]  {butter}                   => {tropical fruit}           0.009964413  0.1798165 0.055414337 1.7136583    98
    ## [514]  {butter}                   => {root vegetables}          0.012913066  0.2330275 0.055414337 2.1378971   127
    ## [515]  {root vegetables}          => {butter}                   0.012913066  0.1184701 0.108998475 2.1378971   127
    ## [516]  {butter}                   => {soda}                     0.008845958  0.1596330 0.055414337 0.9154465    87
    ## [517]  {butter}                   => {yogurt}                   0.014641586  0.2642202 0.055414337 1.8940273   144
    ## [518]  {yogurt}                   => {butter}                   0.014641586  0.1049563 0.139501779 1.8940273   144
    ## [519]  {butter}                   => {rolls/buns}               0.013421454  0.2422018 0.055414337 1.3167800   132
    ## [520]  {butter}                   => {other vegetables}         0.020030503  0.3614679 0.055414337 1.8681223   197
    ## [521]  {other vegetables}         => {butter}                   0.020030503  0.1035208 0.193492628 1.8681223   197
    ## [522]  {butter}                   => {whole milk}               0.027554652  0.4972477 0.055414337 1.9460530   271
    ## [523]  {whole milk}               => {butter}                   0.027554652  0.1078392 0.255516014 1.9460530   271
    ## [524]  {domestic eggs}            => {newspapers}               0.006914082  0.1089744 0.063446873 1.3653030    68
    ## [525]  {newspapers}               => {fruit/vegetable juice}    0.008235892  0.1031847 0.079816980 1.4273160    81
    ## [526]  {fruit/vegetable juice}    => {newspapers}               0.008235892  0.1139241 0.072292832 1.4273160    81
    ## [527]  {whipped/sour cream}       => {newspapers}               0.007219115  0.1007092 0.071682766 1.2617518    71
    ## [528]  {newspapers}               => {pastry}                   0.008439248  0.1057325 0.079816980 1.1884331    83
    ## [529]  {newspapers}               => {citrus fruit}             0.008337570  0.1044586 0.079816980 1.2621011    82
    ## [530]  {citrus fruit}             => {newspapers}               0.008337570  0.1007371 0.082765633 1.2621011    82
    ## [531]  {newspapers}               => {sausage}                  0.008032537  0.1006369 0.079816980 1.0711735    79
    ## [532]  {newspapers}               => {bottled water}            0.011286223  0.1414013 0.079816980 1.2793758   111
    ## [533]  {bottled water}            => {newspapers}               0.011286223  0.1021159 0.110523640 1.2793758   111
    ## [534]  {newspapers}               => {tropical fruit}           0.011794611  0.1477707 0.079816980 1.4082605   116
    ## [535]  {tropical fruit}           => {newspapers}               0.011794611  0.1124031 0.104931368 1.4082605   116
    ## [536]  {newspapers}               => {root vegetables}          0.011489578  0.1439490 0.079816980 1.3206519   113
    ## [537]  {root vegetables}          => {newspapers}               0.011489578  0.1054104 0.108998475 1.3206519   113
    ## [538]  {newspapers}               => {soda}                     0.014641586  0.1834395 0.079816980 1.0519693   144
    ## [539]  {newspapers}               => {yogurt}                   0.015353330  0.1923567 0.079816980 1.3788834   151
    ## [540]  {yogurt}                   => {newspapers}               0.015353330  0.1100583 0.139501779 1.3788834   151
    ## [541]  {newspapers}               => {rolls/buns}               0.019725470  0.2471338 0.079816980 1.3435934   194
    ## [542]  {rolls/buns}               => {newspapers}               0.019725470  0.1072416 0.183934926 1.3435934   194
    ## [543]  {newspapers}               => {other vegetables}         0.019318760  0.2420382 0.079816980 1.2508912   190
    ## [544]  {newspapers}               => {whole milk}               0.027351296  0.3426752 0.079816980 1.3411103   269
    ## [545]  {whole milk}               => {newspapers}               0.027351296  0.1070434 0.255516014 1.3411103   269
    ## [546]  {domestic eggs}            => {fruit/vegetable juice}    0.008032537  0.1266026 0.063446873 1.7512464    79
    ## [547]  {fruit/vegetable juice}    => {domestic eggs}            0.008032537  0.1111111 0.072292832 1.7512464    79
    ## [548]  {domestic eggs}            => {whipped/sour cream}       0.009964413  0.1570513 0.063446873 2.1909211    98
    ## [549]  {whipped/sour cream}       => {domestic eggs}            0.009964413  0.1390071 0.071682766 2.1909211    98
    ## [550]  {domestic eggs}            => {pip fruit}                0.008642603  0.1362179 0.063446873 1.8006768    85
    ## [551]  {pip fruit}                => {domestic eggs}            0.008642603  0.1142473 0.075648195 1.8006768    85
    ## [552]  {domestic eggs}            => {pastry}                   0.009049314  0.1426282 0.063446873 1.6031410    89
    ## [553]  {pastry}                   => {domestic eggs}            0.009049314  0.1017143 0.088967972 1.6031410    89
    ## [554]  {domestic eggs}            => {citrus fruit}             0.010371124  0.1634615 0.063446873 1.9749929   102
    ## [555]  {citrus fruit}             => {domestic eggs}            0.010371124  0.1253071 0.082765633 1.9749929   102
    ## [556]  {domestic eggs}            => {shopping bags}            0.009049314  0.1426282 0.063446873 1.4476248    89
    ## [557]  {domestic eggs}            => {sausage}                  0.009557702  0.1506410 0.063446873 1.6034139    94
    ## [558]  {sausage}                  => {domestic eggs}            0.009557702  0.1017316 0.093950178 1.6034139    94
    ## [559]  {domestic eggs}            => {bottled water}            0.009150991  0.1442308 0.063446873 1.3049766    90
    ## [560]  {domestic eggs}            => {tropical fruit}           0.011387900  0.1794872 0.063446873 1.7105198   112
    ## [561]  {tropical fruit}           => {domestic eggs}            0.011387900  0.1085271 0.104931368 1.7105198   112
    ## [562]  {domestic eggs}            => {root vegetables}          0.014336553  0.2259615 0.063446873 2.0730706   141
    ## [563]  {root vegetables}          => {domestic eggs}            0.014336553  0.1315299 0.108998475 2.0730706   141
    ## [564]  {domestic eggs}            => {soda}                     0.012404677  0.1955128 0.063446873 1.1212062   122
    ## [565]  {domestic eggs}            => {yogurt}                   0.014336553  0.2259615 0.063446873 1.6197753   141
    ## [566]  {yogurt}                   => {domestic eggs}            0.014336553  0.1027697 0.139501779 1.6197753   141
    ## [567]  {domestic eggs}            => {rolls/buns}               0.015658363  0.2467949 0.063446873 1.3417510   154
    ## [568]  {domestic eggs}            => {other vegetables}         0.022267412  0.3509615 0.063446873 1.8138238   219
    ## [569]  {other vegetables}         => {domestic eggs}            0.022267412  0.1150815 0.193492628 1.8138238   219
    ## [570]  {domestic eggs}            => {whole milk}               0.029994916  0.4727564 0.063446873 1.8502027   295
    ## [571]  {whole milk}               => {domestic eggs}            0.029994916  0.1173896 0.255516014 1.8502027   295
    ## [572]  {fruit/vegetable juice}    => {whipped/sour cream}       0.009049314  0.1251758 0.072292832 1.7462469    89
    ## [573]  {whipped/sour cream}       => {fruit/vegetable juice}    0.009049314  0.1262411 0.071682766 1.7462469    89
    ## [574]  {fruit/vegetable juice}    => {pip fruit}                0.009557702  0.1322082 0.072292832 1.7476710    94
    ## [575]  {pip fruit}                => {fruit/vegetable juice}    0.009557702  0.1263441 0.075648195 1.7476710    94
    ## [576]  {fruit/vegetable juice}    => {pastry}                   0.008540925  0.1181435 0.072292832 1.3279325    84
    ## [577]  {fruit/vegetable juice}    => {citrus fruit}             0.010371124  0.1434599 0.072292832 1.7333271   102
    ## [578]  {citrus fruit}             => {fruit/vegetable juice}    0.010371124  0.1253071 0.082765633 1.7333271   102
    ## [579]  {fruit/vegetable juice}    => {shopping bags}            0.010676157  0.1476793 0.072292832 1.4988918   105
    ## [580]  {shopping bags}            => {fruit/vegetable juice}    0.010676157  0.1083591 0.098525674 1.4988918   105
    ## [581]  {fruit/vegetable juice}    => {sausage}                  0.010066090  0.1392405 0.072292832 1.4820675    99
    ## [582]  {sausage}                  => {fruit/vegetable juice}    0.010066090  0.1071429 0.093950178 1.4820675    99
    ## [583]  {fruit/vegetable juice}    => {bottled water}            0.014234875  0.1969058 0.072292832 1.7815715   140
    ## [584]  {bottled water}            => {fruit/vegetable juice}    0.014234875  0.1287948 0.110523640 1.7815715   140
    ## [585]  {fruit/vegetable juice}    => {tropical fruit}           0.013726487  0.1898734 0.072292832 1.8095010   135
    ## [586]  {tropical fruit}           => {fruit/vegetable juice}    0.013726487  0.1308140 0.104931368 1.8095010   135
    ## [587]  {fruit/vegetable juice}    => {root vegetables}          0.011997966  0.1659634 0.072292832 1.5226216   118
    ## [588]  {root vegetables}          => {fruit/vegetable juice}    0.011997966  0.1100746 0.108998475 1.5226216   118
    ## [589]  {fruit/vegetable juice}    => {soda}                     0.018403660  0.2545710 0.072292832 1.4598869   181
    ## [590]  {soda}                     => {fruit/vegetable juice}    0.018403660  0.1055394 0.174377224 1.4598869   181
    ## [591]  {fruit/vegetable juice}    => {yogurt}                   0.018708693  0.2587904 0.072292832 1.8551049   184
    ## [592]  {yogurt}                   => {fruit/vegetable juice}    0.018708693  0.1341108 0.139501779 1.8551049   184
    ## [593]  {fruit/vegetable juice}    => {rolls/buns}               0.014539908  0.2011252 0.072292832 1.0934583   143
    ## [594]  {fruit/vegetable juice}    => {other vegetables}         0.021047280  0.2911392 0.072292832 1.5046529   207
    ## [595]  {other vegetables}         => {fruit/vegetable juice}    0.021047280  0.1087756 0.193492628 1.5046529   207
    ## [596]  {fruit/vegetable juice}    => {whole milk}               0.026639553  0.3684951 0.072292832 1.4421604   262
    ## [597]  {whole milk}               => {fruit/vegetable juice}    0.026639553  0.1042579 0.255516014 1.4421604   262
    ## [598]  {whipped/sour cream}       => {pip fruit}                0.009252669  0.1290780 0.071682766 1.7062934    91
    ## [599]  {pip fruit}                => {whipped/sour cream}       0.009252669  0.1223118 0.075648195 1.7062934    91
    ## [600]  {whipped/sour cream}       => {pastry}                   0.007524148  0.1049645 0.071682766 1.1798014    74
    ## [601]  {whipped/sour cream}       => {citrus fruit}             0.010879512  0.1517730 0.071682766 1.8337690   107
    ## [602]  {citrus fruit}             => {whipped/sour cream}       0.010879512  0.1314496 0.082765633 1.8337690   107
    ## [603]  {whipped/sour cream}       => {shopping bags}            0.007930859  0.1106383 0.071682766 1.1229388    78
    ## [604]  {whipped/sour cream}       => {sausage}                  0.009049314  0.1262411 0.071682766 1.3437030    89
    ## [605]  {whipped/sour cream}       => {bottled water}            0.008744281  0.1219858 0.071682766 1.1037079    86
    ## [606]  {whipped/sour cream}       => {tropical fruit}           0.013828165  0.1929078 0.071682766 1.8384188   136
    ## [607]  {tropical fruit}           => {whipped/sour cream}       0.013828165  0.1317829 0.104931368 1.8384188   136
    ## [608]  {whipped/sour cream}       => {root vegetables}          0.017081851  0.2382979 0.071682766 2.1862496   168
    ## [609]  {root vegetables}          => {whipped/sour cream}       0.017081851  0.1567164 0.108998475 2.1862496   168
    ## [610]  {whipped/sour cream}       => {soda}                     0.011591256  0.1617021 0.071682766 0.9273122   114
    ## [611]  {whipped/sour cream}       => {yogurt}                   0.020742247  0.2893617 0.071682766 2.0742510   204
    ## [612]  {yogurt}                   => {whipped/sour cream}       0.020742247  0.1486880 0.139501779 2.0742510   204
    ## [613]  {whipped/sour cream}       => {rolls/buns}               0.014641586  0.2042553 0.071682766 1.1104760   144
    ## [614]  {whipped/sour cream}       => {other vegetables}         0.028876462  0.4028369 0.071682766 2.0819237   284
    ## [615]  {other vegetables}         => {whipped/sour cream}       0.028876462  0.1492380 0.193492628 2.0819237   284
    ## [616]  {whipped/sour cream}       => {whole milk}               0.032231825  0.4496454 0.071682766 1.7597542   317
    ## [617]  {whole milk}               => {whipped/sour cream}       0.032231825  0.1261441 0.255516014 1.7597542   317
    ## [618]  {pip fruit}                => {pastry}                   0.010676157  0.1411290 0.075648195 1.5862903   105
    ## [619]  {pastry}                   => {pip fruit}                0.010676157  0.1200000 0.088967972 1.5862903   105
    ## [620]  {pip fruit}                => {citrus fruit}             0.013828165  0.1827957 0.075648195 2.2085942   136
    ## [621]  {citrus fruit}             => {pip fruit}                0.013828165  0.1670762 0.082765633 2.2085942   136
    ## [622]  {pip fruit}                => {shopping bags}            0.009354347  0.1236559 0.075648195 1.2550629    92
    ## [623]  {pip fruit}                => {sausage}                  0.010777834  0.1424731 0.075648195 1.5164752   106
    ## [624]  {sausage}                  => {pip fruit}                0.010777834  0.1147186 0.093950178 1.5164752   106
    ## [625]  {pip fruit}                => {bottled water}            0.010574479  0.1397849 0.075648195 1.2647516   104
    ## [626]  {pip fruit}                => {tropical fruit}           0.020437214  0.2701613 0.075648195 2.5746476   201
    ## [627]  {tropical fruit}           => {pip fruit}                0.020437214  0.1947674 0.104931368 2.5746476   201
    ## [628]  {pip fruit}                => {root vegetables}          0.015556685  0.2056452 0.075648195 1.8866793   153
    ## [629]  {root vegetables}          => {pip fruit}                0.015556685  0.1427239 0.108998475 1.8866793   153
    ## [630]  {pip fruit}                => {soda}                     0.013319776  0.1760753 0.075648195 1.0097378   131
    ## [631]  {pip fruit}                => {yogurt}                   0.017996950  0.2379032 0.075648195 1.7053777   177
    ## [632]  {yogurt}                   => {pip fruit}                0.017996950  0.1290087 0.139501779 1.7053777   177
    ## [633]  {pip fruit}                => {rolls/buns}               0.013929842  0.1841398 0.075648195 1.0011138   137
    ## [634]  {pip fruit}                => {other vegetables}         0.026131164  0.3454301 0.075648195 1.7852365   257
    ## [635]  {other vegetables}         => {pip fruit}                0.026131164  0.1350499 0.193492628 1.7852365   257
    ## [636]  {pip fruit}                => {whole milk}               0.030096594  0.3978495 0.075648195 1.5570432   296
    ## [637]  {whole milk}               => {pip fruit}                0.030096594  0.1177875 0.255516014 1.5570432   296
    ## [638]  {pastry}                   => {citrus fruit}             0.009761057  0.1097143 0.088967972 1.3256020    96
    ## [639]  {citrus fruit}             => {pastry}                   0.009761057  0.1179361 0.082765633 1.3256020    96
    ## [640]  {pastry}                   => {shopping bags}            0.011896289  0.1337143 0.088967972 1.3571517   117
    ## [641]  {shopping bags}            => {pastry}                   0.011896289  0.1207430 0.098525674 1.3571517   117
    ## [642]  {pastry}                   => {sausage}                  0.012506355  0.1405714 0.088967972 1.4962338   123
    ## [643]  {sausage}                  => {pastry}                   0.012506355  0.1331169 0.093950178 1.4962338   123
    ## [644]  {pastry}                   => {bottled water}            0.008947636  0.1005714 0.088967972 0.9099540    88
    ## [645]  {pastry}                   => {tropical fruit}           0.013218099  0.1485714 0.088967972 1.4158915   130
    ## [646]  {tropical fruit}           => {pastry}                   0.013218099  0.1259690 0.104931368 1.4158915   130
    ## [647]  {pastry}                   => {root vegetables}          0.010981190  0.1234286 0.088967972 1.1323881   108
    ## [648]  {root vegetables}          => {pastry}                   0.010981190  0.1007463 0.108998475 1.1323881   108
    ## [649]  {pastry}                   => {soda}                     0.021047280  0.2365714 0.088967972 1.3566647   207
    ## [650]  {soda}                     => {pastry}                   0.021047280  0.1206997 0.174377224 1.3566647   207
    ## [651]  {pastry}                   => {yogurt}                   0.017691917  0.1988571 0.088967972 1.4254810   174
    ## [652]  {yogurt}                   => {pastry}                   0.017691917  0.1268222 0.139501779 1.4254810   174
    ## [653]  {pastry}                   => {rolls/buns}               0.020945602  0.2354286 0.088967972 1.2799558   206
    ## [654]  {rolls/buns}               => {pastry}                   0.020945602  0.1138751 0.183934926 1.2799558   206
    ## [655]  {pastry}                   => {other vegetables}         0.022572445  0.2537143 0.088967972 1.3112349   222
    ## [656]  {other vegetables}         => {pastry}                   0.022572445  0.1166579 0.193492628 1.3112349   222
    ## [657]  {pastry}                   => {whole milk}               0.033248602  0.3737143 0.088967972 1.4625865   327
    ## [658]  {whole milk}               => {pastry}                   0.033248602  0.1301234 0.255516014 1.4625865   327
    ## [659]  {citrus fruit}             => {shopping bags}            0.009761057  0.1179361 0.082765633 1.1970090    96
    ## [660]  {citrus fruit}             => {sausage}                  0.011286223  0.1363636 0.082765633 1.4514463   111
    ## [661]  {sausage}                  => {citrus fruit}             0.011286223  0.1201299 0.093950178 1.4514463   111
    ## [662]  {citrus fruit}             => {bottled water}            0.013523132  0.1633907 0.082765633 1.4783323   133
    ## [663]  {bottled water}            => {citrus fruit}             0.013523132  0.1223551 0.110523640 1.4783323   133
    ## [664]  {citrus fruit}             => {tropical fruit}           0.019928826  0.2407862 0.082765633 2.2947022   196
    ## [665]  {tropical fruit}           => {citrus fruit}             0.019928826  0.1899225 0.104931368 2.2947022   196
    ## [666]  {citrus fruit}             => {root vegetables}          0.017691917  0.2137592 0.082765633 1.9611211   174
    ## [667]  {root vegetables}          => {citrus fruit}             0.017691917  0.1623134 0.108998475 1.9611211   174
    ## [668]  {citrus fruit}             => {soda}                     0.012811388  0.1547912 0.082765633 0.8876799   126
    ## [669]  {citrus fruit}             => {yogurt}                   0.021657346  0.2616708 0.082765633 1.8757521   213
    ## [670]  {yogurt}                   => {citrus fruit}             0.021657346  0.1552478 0.139501779 1.8757521   213
    ## [671]  {citrus fruit}             => {rolls/buns}               0.016776817  0.2027027 0.082765633 1.1020349   165
    ## [672]  {citrus fruit}             => {other vegetables}         0.028876462  0.3488943 0.082765633 1.8031403   284
    ## [673]  {other vegetables}         => {citrus fruit}             0.028876462  0.1492380 0.193492628 1.8031403   284
    ## [674]  {citrus fruit}             => {whole milk}               0.030503305  0.3685504 0.082765633 1.4423768   300
    ## [675]  {whole milk}               => {citrus fruit}             0.030503305  0.1193792 0.255516014 1.4423768   300
    ## [676]  {shopping bags}            => {sausage}                  0.015658363  0.1589267 0.098525674 1.6916065   154
    ## [677]  {sausage}                  => {shopping bags}            0.015658363  0.1666667 0.093950178 1.6916065   154
    ## [678]  {shopping bags}            => {bottled water}            0.010981190  0.1114551 0.098525674 1.0084278   108
    ## [679]  {shopping bags}            => {tropical fruit}           0.013523132  0.1372549 0.098525674 1.3080445   133
    ## [680]  {tropical fruit}           => {shopping bags}            0.013523132  0.1288760 0.104931368 1.3080445   133
    ## [681]  {shopping bags}            => {root vegetables}          0.012811388  0.1300310 0.098525674 1.1929613   126
    ## [682]  {root vegetables}          => {shopping bags}            0.012811388  0.1175373 0.108998475 1.1929613   126
    ## [683]  {shopping bags}            => {soda}                     0.024605999  0.2497420 0.098525674 1.4321939   242
    ## [684]  {soda}                     => {shopping bags}            0.024605999  0.1411079 0.174377224 1.4321939   242
    ## [685]  {shopping bags}            => {yogurt}                   0.015251652  0.1547988 0.098525674 1.1096544   150
    ## [686]  {yogurt}                   => {shopping bags}            0.015251652  0.1093294 0.139501779 1.1096544   150
    ## [687]  {shopping bags}            => {rolls/buns}               0.019522115  0.1981424 0.098525674 1.0772419   192
    ## [688]  {rolls/buns}               => {shopping bags}            0.019522115  0.1061360 0.183934926 1.0772419   192
    ## [689]  {shopping bags}            => {other vegetables}         0.023182511  0.2352941 0.098525674 1.2160366   228
    ## [690]  {other vegetables}         => {shopping bags}            0.023182511  0.1198108 0.193492628 1.2160366   228
    ## [691]  {shopping bags}            => {whole milk}               0.024504321  0.2487100 0.098525674 0.9733637   241
    ## [692]  {sausage}                  => {bottled water}            0.011997966  0.1277056 0.093950178 1.1554598   118
    ## [693]  {bottled water}            => {sausage}                  0.011997966  0.1085557 0.110523640 1.1554598   118
    ## [694]  {sausage}                  => {tropical fruit}           0.013929842  0.1482684 0.093950178 1.4130036   137
    ## [695]  {tropical fruit}           => {sausage}                  0.013929842  0.1327519 0.104931368 1.4130036   137
    ## [696]  {sausage}                  => {root vegetables}          0.014946619  0.1590909 0.093950178 1.4595700   147
    ## [697]  {root vegetables}          => {sausage}                  0.014946619  0.1371269 0.108998475 1.4595700   147
    ## [698]  {sausage}                  => {soda}                     0.024300966  0.2586580 0.093950178 1.4833245   239
    ## [699]  {soda}                     => {sausage}                  0.024300966  0.1393586 0.174377224 1.4833245   239
    ## [700]  {sausage}                  => {yogurt}                   0.019623793  0.2088745 0.093950178 1.4972889   193
    ## [701]  {yogurt}                   => {sausage}                  0.019623793  0.1406706 0.139501779 1.4972889   193
    ## [702]  {sausage}                  => {rolls/buns}               0.030604982  0.3257576 0.093950178 1.7710480   301
    ## [703]  {rolls/buns}               => {sausage}                  0.030604982  0.1663903 0.183934926 1.7710480   301
    ## [704]  {sausage}                  => {other vegetables}         0.026944586  0.2867965 0.093950178 1.4822091   265
    ## [705]  {other vegetables}         => {sausage}                  0.026944586  0.1392538 0.193492628 1.4822091   265
    ## [706]  {sausage}                  => {whole milk}               0.029893238  0.3181818 0.093950178 1.2452520   294
    ## [707]  {whole milk}               => {sausage}                  0.029893238  0.1169916 0.255516014 1.2452520   294
    ## [708]  {bottled water}            => {tropical fruit}           0.018505338  0.1674333 0.110523640 1.5956459   182
    ## [709]  {tropical fruit}           => {bottled water}            0.018505338  0.1763566 0.104931368 1.5956459   182
    ## [710]  {bottled water}            => {root vegetables}          0.015658363  0.1416743 0.110523640 1.2997827   154
    ## [711]  {root vegetables}          => {bottled water}            0.015658363  0.1436567 0.108998475 1.2997827   154
    ## [712]  {bottled water}            => {soda}                     0.028978139  0.2621895 0.110523640 1.5035766   285
    ## [713]  {soda}                     => {bottled water}            0.028978139  0.1661808 0.174377224 1.5035766   285
    ## [714]  {bottled water}            => {yogurt}                   0.022979156  0.2079117 0.110523640 1.4903873   226
    ## [715]  {yogurt}                   => {bottled water}            0.022979156  0.1647230 0.139501779 1.4903873   226
    ## [716]  {bottled water}            => {rolls/buns}               0.024199288  0.2189512 0.110523640 1.1903734   238
    ## [717]  {rolls/buns}               => {bottled water}            0.024199288  0.1315644 0.183934926 1.1903734   238
    ## [718]  {bottled water}            => {other vegetables}         0.024809354  0.2244710 0.110523640 1.1601012   244
    ## [719]  {other vegetables}         => {bottled water}            0.024809354  0.1282186 0.193492628 1.1601012   244
    ## [720]  {bottled water}            => {whole milk}               0.034367056  0.3109476 0.110523640 1.2169396   338
    ## [721]  {whole milk}               => {bottled water}            0.034367056  0.1345006 0.255516014 1.2169396   338
    ## [722]  {tropical fruit}           => {root vegetables}          0.021047280  0.2005814 0.104931368 1.8402220   207
    ## [723]  {root vegetables}          => {tropical fruit}           0.021047280  0.1930970 0.108998475 1.8402220   207
    ## [724]  {tropical fruit}           => {soda}                     0.020843925  0.1986434 0.104931368 1.1391592   205
    ## [725]  {soda}                     => {tropical fruit}           0.020843925  0.1195335 0.174377224 1.1391592   205
    ## [726]  {tropical fruit}           => {yogurt}                   0.029283172  0.2790698 0.104931368 2.0004746   288
    ## [727]  {yogurt}                   => {tropical fruit}           0.029283172  0.2099125 0.139501779 2.0004746   288
    ## [728]  {tropical fruit}           => {rolls/buns}               0.024605999  0.2344961 0.104931368 1.2748863   242
    ## [729]  {rolls/buns}               => {tropical fruit}           0.024605999  0.1337756 0.183934926 1.2748863   242
    ## [730]  {tropical fruit}           => {other vegetables}         0.035892222  0.3420543 0.104931368 1.7677896   353
    ## [731]  {other vegetables}         => {tropical fruit}           0.035892222  0.1854966 0.193492628 1.7677896   353
    ## [732]  {tropical fruit}           => {whole milk}               0.042297916  0.4031008 0.104931368 1.5775950   416
    ## [733]  {whole milk}               => {tropical fruit}           0.042297916  0.1655392 0.255516014 1.5775950   416
    ## [734]  {root vegetables}          => {soda}                     0.018607016  0.1707090 0.108998475 0.9789636   183
    ## [735]  {soda}                     => {root vegetables}          0.018607016  0.1067055 0.174377224 0.9789636   183
    ## [736]  {root vegetables}          => {yogurt}                   0.025826131  0.2369403 0.108998475 1.6984751   254
    ## [737]  {yogurt}                   => {root vegetables}          0.025826131  0.1851312 0.139501779 1.6984751   254
    ## [738]  {root vegetables}          => {rolls/buns}               0.024300966  0.2229478 0.108998475 1.2121013   239
    ## [739]  {rolls/buns}               => {root vegetables}          0.024300966  0.1321172 0.183934926 1.2121013   239
    ## [740]  {root vegetables}          => {other vegetables}         0.047381800  0.4347015 0.108998475 2.2466049   466
    ## [741]  {other vegetables}         => {root vegetables}          0.047381800  0.2448765 0.193492628 2.2466049   466
    ## [742]  {root vegetables}          => {whole milk}               0.048906965  0.4486940 0.108998475 1.7560310   481
    ## [743]  {whole milk}               => {root vegetables}          0.048906965  0.1914047 0.255516014 1.7560310   481
    ## [744]  {soda}                     => {yogurt}                   0.027351296  0.1568513 0.174377224 1.1243678   269
    ## [745]  {yogurt}                   => {soda}                     0.027351296  0.1960641 0.139501779 1.1243678   269
    ## [746]  {soda}                     => {rolls/buns}               0.038332486  0.2198251 0.174377224 1.1951242   377
    ## [747]  {rolls/buns}               => {soda}                     0.038332486  0.2084024 0.183934926 1.1951242   377
    ## [748]  {soda}                     => {other vegetables}         0.032740214  0.1877551 0.174377224 0.9703476   322
    ## [749]  {other vegetables}         => {soda}                     0.032740214  0.1692065 0.193492628 0.9703476   322
    ## [750]  {soda}                     => {whole milk}               0.040061007  0.2297376 0.174377224 0.8991124   394
    ## [751]  {whole milk}               => {soda}                     0.040061007  0.1567847 0.255516014 0.8991124   394
    ## [752]  {yogurt}                   => {rolls/buns}               0.034367056  0.2463557 0.139501779 1.3393633   338
    ## [753]  {rolls/buns}               => {yogurt}                   0.034367056  0.1868436 0.183934926 1.3393633   338
    ## [754]  {yogurt}                   => {other vegetables}         0.043416370  0.3112245 0.139501779 1.6084566   427
    ## [755]  {other vegetables}         => {yogurt}                   0.043416370  0.2243826 0.193492628 1.6084566   427
    ## [756]  {yogurt}                   => {whole milk}               0.056024403  0.4016035 0.139501779 1.5717351   551
    ## [757]  {whole milk}               => {yogurt}                   0.056024403  0.2192598 0.255516014 1.5717351   551
    ## [758]  {rolls/buns}               => {other vegetables}         0.042602949  0.2316197 0.183934926 1.1970465   419
    ## [759]  {other vegetables}         => {rolls/buns}               0.042602949  0.2201787 0.193492628 1.1970465   419
    ## [760]  {rolls/buns}               => {whole milk}               0.056634469  0.3079049 0.183934926 1.2050318   557
    ## [761]  {whole milk}               => {rolls/buns}               0.056634469  0.2216474 0.255516014 1.2050318   557
    ## [762]  {other vegetables}         => {whole milk}               0.074834774  0.3867578 0.193492628 1.5136341   736
    ## [763]  {whole milk}               => {other vegetables}         0.074834774  0.2928770 0.255516014 1.5136341   736
    ## [764]  {oil,                                                                                                      
    ##         other vegetables}         => {whole milk}               0.005083884  0.5102041 0.009964413 1.9967597    50
    ## [765]  {oil,                                                                                                      
    ##         whole milk}               => {other vegetables}         0.005083884  0.4504505 0.011286223 2.3279980    50
    ## [766]  {onions,                                                                                                   
    ##         root vegetables}          => {other vegetables}         0.005693950  0.6021505 0.009456024 3.1120076    56
    ## [767]  {onions,                                                                                                   
    ##         other vegetables}         => {root vegetables}          0.005693950  0.4000000 0.014234875 3.6697761    56
    ## [768]  {other vegetables,                                                                                         
    ##         root vegetables}          => {onions}                   0.005693950  0.1201717 0.047381800 3.8750440    56
    ## [769]  {onions,                                                                                                   
    ##         other vegetables}         => {whole milk}               0.006609049  0.4642857 0.014234875 1.8170513    65
    ## [770]  {onions,                                                                                                   
    ##         whole milk}               => {other vegetables}         0.006609049  0.5462185 0.012099644 2.8229421    65
    ## [771]  {hamburger meat,                                                                                           
    ##         other vegetables}         => {whole milk}               0.006304016  0.4558824 0.013828165 1.7841635    62
    ## [772]  {hamburger meat,                                                                                           
    ##         whole milk}               => {other vegetables}         0.006304016  0.4275862 0.014743264 2.2098320    62
    ## [773]  {hygiene articles,                                                                                         
    ##         other vegetables}         => {whole milk}               0.005185562  0.5425532 0.009557702 2.1233628    51
    ## [774]  {hygiene articles,                                                                                         
    ##         whole milk}               => {other vegetables}         0.005185562  0.4047619 0.012811388 2.0918725    51
    ## [775]  {other vegetables,                                                                                         
    ##         sugar}                    => {whole milk}               0.006304016  0.5849057 0.010777834 2.2891155    62
    ## [776]  {sugar,                                                                                                    
    ##         whole milk}               => {other vegetables}         0.006304016  0.4189189 0.015048297 2.1650381    62
    ## [777]  {long life bakery product,                                                                                 
    ##         other vegetables}         => {whole milk}               0.005693950  0.5333333 0.010676157 2.0872795    56
    ## [778]  {long life bakery product,                                                                                 
    ##         whole milk}               => {other vegetables}         0.005693950  0.4210526 0.013523132 2.1760655    56
    ## [779]  {cream cheese,                                                                                             
    ##         yogurt}                   => {other vegetables}         0.005287239  0.4262295 0.012404677 2.2028204    52
    ## [780]  {cream cheese,                                                                                             
    ##         other vegetables}         => {yogurt}                   0.005287239  0.3851852 0.013726487 2.7611489    52
    ## [781]  {other vegetables,                                                                                         
    ##         yogurt}                   => {cream cheese}             0.005287239  0.1217799 0.043416370 3.0710383    52
    ## [782]  {cream cheese,                                                                                             
    ##         yogurt}                   => {whole milk}               0.006609049  0.5327869 0.012404677 2.0851409    65
    ## [783]  {cream cheese,                                                                                             
    ##         whole milk}               => {yogurt}                   0.006609049  0.4012346 0.016471784 2.8761968    65
    ## [784]  {whole milk,                                                                                               
    ##         yogurt}                   => {cream cheese}             0.006609049  0.1179673 0.056024403 2.9748941    65
    ## [785]  {cream cheese,                                                                                             
    ##         other vegetables}         => {whole milk}               0.006710727  0.4888889 0.013726487 1.9133395    66
    ## [786]  {cream cheese,                                                                                             
    ##         whole milk}               => {other vegetables}         0.006710727  0.4074074 0.016471784 2.1055449    66
    ## [787]  {chicken,                                                                                                  
    ##         root vegetables}          => {other vegetables}         0.005693950  0.5233645 0.010879512 2.7048291    56
    ## [788]  {chicken,                                                                                                  
    ##         other vegetables}         => {root vegetables}          0.005693950  0.3181818 0.017895272 2.9191401    56
    ## [789]  {other vegetables,                                                                                         
    ##         root vegetables}          => {chicken}                  0.005693950  0.1201717 0.047381800 2.8006834    56
    ## [790]  {chicken,                                                                                                  
    ##         root vegetables}          => {whole milk}               0.005998983  0.5514019 0.010879512 2.1579934    59
    ## [791]  {chicken,                                                                                                  
    ##         whole milk}               => {root vegetables}          0.005998983  0.3410405 0.017590239 3.1288554    59
    ## [792]  {root vegetables,                                                                                          
    ##         whole milk}               => {chicken}                  0.005998983  0.1226611 0.048906965 2.8587018    59
    ## [793]  {chicken,                                                                                                  
    ##         rolls/buns}               => {whole milk}               0.005287239  0.5473684 0.009659380 2.1422079    52
    ## [794]  {chicken,                                                                                                  
    ##         whole milk}               => {rolls/buns}               0.005287239  0.3005780 0.017590239 1.6341542    52
    ## [795]  {chicken,                                                                                                  
    ##         other vegetables}         => {whole milk}               0.008439248  0.4715909 0.017895272 1.8456413    83
    ## [796]  {chicken,                                                                                                  
    ##         whole milk}               => {other vegetables}         0.008439248  0.4797688 0.017590239 2.4795197    83
    ## [797]  {other vegetables,                                                                                         
    ##         whole milk}               => {chicken}                  0.008439248  0.1127717 0.074834774 2.6282229    83
    ## [798]  {other vegetables,                                                                                         
    ##         white bread}              => {whole milk}               0.005897306  0.4296296 0.013726487 1.6814196    58
    ## [799]  {white bread,                                                                                              
    ##         whole milk}               => {other vegetables}         0.005897306  0.3452381 0.017081851 1.7842442    58
    ## [800]  {chocolate,                                                                                                
    ##         soda}                     => {whole milk}               0.005083884  0.3759398 0.013523132 1.4712966    50
    ## [801]  {chocolate,                                                                                                
    ##         whole milk}               => {soda}                     0.005083884  0.3048780 0.016675140 1.7483823    50
    ## [802]  {soda,                                                                                                     
    ##         whole milk}               => {chocolate}                0.005083884  0.1269036 0.040061007 2.5575747    50
    ## [803]  {chocolate,                                                                                                
    ##         other vegetables}         => {whole milk}               0.005490595  0.4320000 0.012709710 1.6906964    54
    ## [804]  {chocolate,                                                                                                
    ##         whole milk}               => {other vegetables}         0.005490595  0.3292683 0.016675140 1.7017098    54
    ## [805]  {coffee,                                                                                                   
    ##         yogurt}                   => {whole milk}               0.005083884  0.5208333 0.009761057 2.0383589    50
    ## [806]  {coffee,                                                                                                   
    ##         whole milk}               => {yogurt}                   0.005083884  0.2717391 0.018708693 1.9479259    50
    ## [807]  {coffee,                                                                                                   
    ##         other vegetables}         => {whole milk}               0.006405694  0.4772727 0.013421454 1.8678779    63
    ## [808]  {coffee,                                                                                                   
    ##         whole milk}               => {other vegetables}         0.006405694  0.3423913 0.018708693 1.7695315    63
    ## [809]  {frozen vegetables,                                                                                        
    ##         root vegetables}          => {other vegetables}         0.006100661  0.5263158 0.011591256 2.7200819    60
    ## [810]  {frozen vegetables,                                                                                        
    ##         other vegetables}         => {root vegetables}          0.006100661  0.3428571 0.017793594 3.1455224    60
    ## [811]  {other vegetables,                                                                                         
    ##         root vegetables}          => {frozen vegetables}        0.006100661  0.1287554 0.047381800 2.6771861    60
    ## [812]  {frozen vegetables,                                                                                        
    ##         root vegetables}          => {whole milk}               0.006202339  0.5350877 0.011591256 2.0941455    61
    ## [813]  {frozen vegetables,                                                                                        
    ##         whole milk}               => {root vegetables}          0.006202339  0.3034826 0.020437214 2.7842829    61
    ## [814]  {root vegetables,                                                                                          
    ##         whole milk}               => {frozen vegetables}        0.006202339  0.1268191 0.048906965 2.6369262    61
    ## [815]  {frozen vegetables,                                                                                        
    ##         yogurt}                   => {other vegetables}         0.005287239  0.4262295 0.012404677 2.2028204    52
    ## [816]  {frozen vegetables,                                                                                        
    ##         other vegetables}         => {yogurt}                   0.005287239  0.2971429 0.017793594 2.1300292    52
    ## [817]  {other vegetables,                                                                                         
    ##         yogurt}                   => {frozen vegetables}        0.005287239  0.1217799 0.043416370 2.5321457    52
    ## [818]  {frozen vegetables,                                                                                        
    ##         yogurt}                   => {whole milk}               0.006100661  0.4918033 0.012404677 1.9247454    60
    ## [819]  {frozen vegetables,                                                                                        
    ##         whole milk}               => {yogurt}                   0.006100661  0.2985075 0.020437214 2.1398111    60
    ## [820]  {whole milk,                                                                                               
    ##         yogurt}                   => {frozen vegetables}        0.006100661  0.1088929 0.056024403 2.2641900    60
    ## [821]  {frozen vegetables,                                                                                        
    ##         rolls/buns}               => {whole milk}               0.005083884  0.5000000 0.010167768 1.9568245    50
    ## [822]  {frozen vegetables,                                                                                        
    ##         whole milk}               => {rolls/buns}               0.005083884  0.2487562 0.020437214 1.3524143    50
    ## [823]  {frozen vegetables,                                                                                        
    ##         other vegetables}         => {whole milk}               0.009659380  0.5428571 0.017793594 2.1245523    95
    ## [824]  {frozen vegetables,                                                                                        
    ##         whole milk}               => {other vegetables}         0.009659380  0.4726368 0.020437214 2.4426606    95
    ## [825]  {other vegetables,                                                                                         
    ##         whole milk}               => {frozen vegetables}        0.009659380  0.1290761 0.074834774 2.6838548    95
    ## [826]  {beef,                                                                                                     
    ##         root vegetables}          => {other vegetables}         0.007930859  0.4561404 0.017386884 2.3574043    78
    ## [827]  {beef,                                                                                                     
    ##         other vegetables}         => {root vegetables}          0.007930859  0.4020619 0.019725470 3.6886925    78
    ## [828]  {other vegetables,                                                                                         
    ##         root vegetables}          => {beef}                     0.007930859  0.1673820 0.047381800 3.1903134    78
    ## [829]  {beef,                                                                                                     
    ##         root vegetables}          => {whole milk}               0.008032537  0.4619883 0.017386884 1.8080601    79
    ## [830]  {beef,                                                                                                     
    ##         whole milk}               => {root vegetables}          0.008032537  0.3779904 0.021250635 3.4678506    79
    ## [831]  {root vegetables,                                                                                          
    ##         whole milk}               => {beef}                     0.008032537  0.1642412 0.048906965 3.1304493    79
    ## [832]  {beef,                                                                                                     
    ##         yogurt}                   => {other vegetables}         0.005185562  0.4434783 0.011692933 2.2919646    51
    ## [833]  {beef,                                                                                                     
    ##         other vegetables}         => {yogurt}                   0.005185562  0.2628866 0.019725470 1.8844677    51
    ## [834]  {other vegetables,                                                                                         
    ##         yogurt}                   => {beef}                     0.005185562  0.1194379 0.043416370 2.2764964    51
    ## [835]  {beef,                                                                                                     
    ##         yogurt}                   => {whole milk}               0.006100661  0.5217391 0.011692933 2.0419038    60
    ## [836]  {beef,                                                                                                     
    ##         whole milk}               => {yogurt}                   0.006100661  0.2870813 0.021250635 2.0579045    60
    ## [837]  {whole milk,                                                                                               
    ##         yogurt}                   => {beef}                     0.006100661  0.1088929 0.056024403 2.0755075    60
    ## [838]  {beef,                                                                                                     
    ##         rolls/buns}               => {other vegetables}         0.005795628  0.4253731 0.013624809 2.1983945    57
    ## [839]  {beef,                                                                                                     
    ##         other vegetables}         => {rolls/buns}               0.005795628  0.2938144 0.019725470 1.5973825    57
    ## [840]  {other vegetables,                                                                                         
    ##         rolls/buns}               => {beef}                     0.005795628  0.1360382 0.042602949 2.5928984    57
    ## [841]  {beef,                                                                                                     
    ##         rolls/buns}               => {whole milk}               0.006812405  0.5000000 0.013624809 1.9568245    67
    ## [842]  {beef,                                                                                                     
    ##         whole milk}               => {rolls/buns}               0.006812405  0.3205742 0.021250635 1.7428673    67
    ## [843]  {rolls/buns,                                                                                               
    ##         whole milk}               => {beef}                     0.006812405  0.1202873 0.056634469 2.2926844    67
    ## [844]  {beef,                                                                                                     
    ##         other vegetables}         => {whole milk}               0.009252669  0.4690722 0.019725470 1.8357838    91
    ## [845]  {beef,                                                                                                     
    ##         whole milk}               => {other vegetables}         0.009252669  0.4354067 0.021250635 2.2502495    91
    ## [846]  {other vegetables,                                                                                         
    ##         whole milk}               => {beef}                     0.009252669  0.1236413 0.074834774 2.3566128    91
    ## [847]  {curd,                                                                                                     
    ##         whipped/sour cream}       => {whole milk}               0.005897306  0.5631068 0.010472801 2.2038024    58
    ## [848]  {curd,                                                                                                     
    ##         whole milk}               => {whipped/sour cream}       0.005897306  0.2256809 0.026131164 3.1483291    58
    ## [849]  {whipped/sour cream,                                                                                       
    ##         whole milk}               => {curd}                     0.005897306  0.1829653 0.032231825 3.4340911    58
    ## [850]  {curd,                                                                                                     
    ##         tropical fruit}           => {yogurt}                   0.005287239  0.5148515 0.010269446 3.6906446    52
    ## [851]  {curd,                                                                                                     
    ##         yogurt}                   => {tropical fruit}           0.005287239  0.3058824 0.017285206 2.9150707    52
    ## [852]  {tropical fruit,                                                                                           
    ##         yogurt}                   => {curd}                     0.005287239  0.1805556 0.029283172 3.3888624    52
    ## [853]  {curd,                                                                                                     
    ##         tropical fruit}           => {other vegetables}         0.005287239  0.5148515 0.010269446 2.6608326    52
    ## [854]  {curd,                                                                                                     
    ##         other vegetables}         => {tropical fruit}           0.005287239  0.3076923 0.017183528 2.9323196    52
    ## [855]  {other vegetables,                                                                                         
    ##         tropical fruit}           => {curd}                     0.005287239  0.1473088 0.035892222 2.7648509    52
    ## [856]  {curd,                                                                                                     
    ##         tropical fruit}           => {whole milk}               0.006507372  0.6336634 0.010269446 2.4799360    64
    ## [857]  {curd,                                                                                                     
    ##         whole milk}               => {tropical fruit}           0.006507372  0.2490272 0.026131164 2.3732392    64
    ## [858]  {tropical fruit,                                                                                           
    ##         whole milk}               => {curd}                     0.006507372  0.1538462 0.042297916 2.8875514    64
    ## [859]  {curd,                                                                                                     
    ##         root vegetables}          => {other vegetables}         0.005490595  0.5046729 0.010879512 2.6082280    54
    ## [860]  {curd,                                                                                                     
    ##         other vegetables}         => {root vegetables}          0.005490595  0.3195266 0.017183528 2.9314780    54
    ## [861]  {other vegetables,                                                                                         
    ##         root vegetables}          => {curd}                     0.005490595  0.1158798 0.047381800 2.1749582    54
    ## [862]  {curd,                                                                                                     
    ##         root vegetables}          => {whole milk}               0.006202339  0.5700935 0.010879512 2.2311457    61
    ## [863]  {curd,                                                                                                     
    ##         whole milk}               => {root vegetables}          0.006202339  0.2373541 0.026131164 2.1775909    61
    ## [864]  {root vegetables,                                                                                          
    ##         whole milk}               => {curd}                     0.006202339  0.1268191 0.048906965 2.3802788    61
    ## [865]  {curd,                                                                                                     
    ##         yogurt}                   => {other vegetables}         0.006100661  0.3529412 0.017285206 1.8240549    60
    ## [866]  {curd,                                                                                                     
    ##         other vegetables}         => {yogurt}                   0.006100661  0.3550296 0.017183528 2.5449825    60
    ## [867]  {other vegetables,                                                                                         
    ##         yogurt}                   => {curd}                     0.006100661  0.1405152 0.043416370 2.6373420    60
    ## [868]  {curd,                                                                                                     
    ##         yogurt}                   => {whole milk}               0.010066090  0.5823529 0.017285206 2.2791250    99
    ## [869]  {curd,                                                                                                     
    ##         whole milk}               => {yogurt}                   0.010066090  0.3852140 0.026131164 2.7613555    99
    ## [870]  {whole milk,                                                                                               
    ##         yogurt}                   => {curd}                     0.010066090  0.1796733 0.056024403 3.3723037    99
    ## [871]  {curd,                                                                                                     
    ##         rolls/buns}               => {whole milk}               0.005897306  0.5858586 0.010066090 2.2928449    58
    ## [872]  {curd,                                                                                                     
    ##         whole milk}               => {rolls/buns}               0.005897306  0.2256809 0.026131164 1.2269607    58
    ## [873]  {rolls/buns,                                                                                               
    ##         whole milk}               => {curd}                     0.005897306  0.1041293 0.056634469 1.9544109    58
    ## [874]  {curd,                                                                                                     
    ##         other vegetables}         => {whole milk}               0.009862735  0.5739645 0.017183528 2.2462956    97
    ## [875]  {curd,                                                                                                     
    ##         whole milk}               => {other vegetables}         0.009862735  0.3774319 0.026131164 1.9506268    97
    ## [876]  {other vegetables,                                                                                         
    ##         whole milk}               => {curd}                     0.009862735  0.1317935 0.074834774 2.4736429    97
    ## [877]  {napkins,                                                                                                  
    ##         yogurt}                   => {whole milk}               0.006100661  0.4958678 0.012302999 1.9406524    60
    ## [878]  {napkins,                                                                                                  
    ##         whole milk}               => {yogurt}                   0.006100661  0.3092784 0.019725470 2.2170208    60
    ## [879]  {whole milk,                                                                                               
    ##         yogurt}                   => {napkins}                  0.006100661  0.1088929 0.056024403 2.0795376    60
    ## [880]  {napkins,                                                                                                  
    ##         rolls/buns}               => {whole milk}               0.005287239  0.4521739 0.011692933 1.7696500    52
    ## [881]  {napkins,                                                                                                  
    ##         whole milk}               => {rolls/buns}               0.005287239  0.2680412 0.019725470 1.4572612    52
    ## [882]  {napkins,                                                                                                  
    ##         other vegetables}         => {whole milk}               0.006812405  0.4718310 0.014438231 1.8465809    67
    ## [883]  {napkins,                                                                                                  
    ##         whole milk}               => {other vegetables}         0.006812405  0.3453608 0.019725470 1.7848785    67
    ## [884]  {pork,                                                                                                     
    ##         root vegetables}          => {other vegetables}         0.007015760  0.5149254 0.013624809 2.6612144    69
    ## [885]  {other vegetables,                                                                                         
    ##         pork}                     => {root vegetables}          0.007015760  0.3239437 0.021657346 2.9720018    69
    ## [886]  {other vegetables,                                                                                         
    ##         root vegetables}          => {pork}                     0.007015760  0.1480687 0.047381800 2.5683516    69
    ## [887]  {pork,                                                                                                     
    ##         root vegetables}          => {whole milk}               0.006812405  0.5000000 0.013624809 1.9568245    67
    ## [888]  {pork,                                                                                                     
    ##         whole milk}               => {root vegetables}          0.006812405  0.3073394 0.022165735 2.8196674    67
    ## [889]  {root vegetables,                                                                                          
    ##         whole milk}               => {pork}                     0.006812405  0.1392931 0.048906965 2.4161341    67
    ## [890]  {pork,                                                                                                     
    ##         rolls/buns}               => {other vegetables}         0.005592272  0.4954955 0.011286223 2.5607978    55
    ## [891]  {other vegetables,                                                                                         
    ##         pork}                     => {rolls/buns}               0.005592272  0.2582160 0.021657346 1.4038441    55
    ## [892]  {other vegetables,                                                                                         
    ##         rolls/buns}               => {pork}                     0.005592272  0.1312649 0.042602949 2.2768791    55
    ## [893]  {pork,                                                                                                     
    ##         rolls/buns}               => {whole milk}               0.006202339  0.5495495 0.011286223 2.1507441    61
    ## [894]  {pork,                                                                                                     
    ##         whole milk}               => {rolls/buns}               0.006202339  0.2798165 0.022165735 1.5212799    61
    ## [895]  {rolls/buns,                                                                                               
    ##         whole milk}               => {pork}                     0.006202339  0.1095153 0.056634469 1.8996166    61
    ## [896]  {other vegetables,                                                                                         
    ##         pork}                     => {whole milk}               0.010167768  0.4694836 0.021657346 1.8373939   100
    ## [897]  {pork,                                                                                                     
    ##         whole milk}               => {other vegetables}         0.010167768  0.4587156 0.022165735 2.3707136   100
    ## [898]  {other vegetables,                                                                                         
    ##         whole milk}               => {pork}                     0.010167768  0.1358696 0.074834774 2.3567499   100
    ## [899]  {frankfurter,                                                                                              
    ##         tropical fruit}           => {whole milk}               0.005185562  0.5483871 0.009456024 2.1461946    51
    ## [900]  {frankfurter,                                                                                              
    ##         whole milk}               => {tropical fruit}           0.005185562  0.2524752 0.020538892 2.4060989    51
    ## [901]  {tropical fruit,                                                                                           
    ##         whole milk}               => {frankfurter}              0.005185562  0.1225962 0.042297916 2.0788503    51
    ## [902]  {frankfurter,                                                                                              
    ##         root vegetables}          => {whole milk}               0.005083884  0.5000000 0.010167768 1.9568245    50
    ## [903]  {frankfurter,                                                                                              
    ##         whole milk}               => {root vegetables}          0.005083884  0.2475248 0.020538892 2.2709011    50
    ## [904]  {root vegetables,                                                                                          
    ##         whole milk}               => {frankfurter}              0.005083884  0.1039501 0.048906965 1.7626712    50
    ## [905]  {frankfurter,                                                                                              
    ##         yogurt}                   => {whole milk}               0.006202339  0.5545455 0.011184545 2.1702963    61
    ## [906]  {frankfurter,                                                                                              
    ##         whole milk}               => {yogurt}                   0.006202339  0.3019802 0.020538892 2.1647050    61
    ## [907]  {whole milk,                                                                                               
    ##         yogurt}                   => {frankfurter}              0.006202339  0.1107078 0.056024403 1.8772608    61
    ## [908]  {frankfurter,                                                                                              
    ##         rolls/buns}               => {other vegetables}         0.005592272  0.2910053 0.019217082 1.5039606    55
    ## [909]  {frankfurter,                                                                                              
    ##         other vegetables}         => {rolls/buns}               0.005592272  0.3395062 0.016471784 1.8457950    55
    ## [910]  {other vegetables,                                                                                         
    ##         rolls/buns}               => {frankfurter}              0.005592272  0.1312649 0.042602949 2.2258456    55
    ## [911]  {frankfurter,                                                                                              
    ##         rolls/buns}               => {whole milk}               0.005998983  0.3121693 0.019217082 1.2217211    59
    ## [912]  {frankfurter,                                                                                              
    ##         whole milk}               => {rolls/buns}               0.005998983  0.2920792 0.020538892 1.5879486    59
    ## [913]  {rolls/buns,                                                                                               
    ##         whole milk}               => {frankfurter}              0.005998983  0.1059246 0.056634469 1.7961524    59
    ## [914]  {frankfurter,                                                                                              
    ##         other vegetables}         => {whole milk}               0.007625826  0.4629630 0.016471784 1.8118745    75
    ## [915]  {frankfurter,                                                                                              
    ##         whole milk}               => {other vegetables}         0.007625826  0.3712871 0.020538892 1.9188696    75
    ## [916]  {other vegetables,                                                                                         
    ##         whole milk}               => {frankfurter}              0.007625826  0.1019022 0.074834774 1.7279446    75
    ## [917]  {bottled beer,                                                                                             
    ##         bottled water}            => {soda}                     0.005083884  0.3225806 0.015760041 1.8499013    50
    ## [918]  {bottled beer,                                                                                             
    ##         soda}                     => {bottled water}            0.005083884  0.2994012 0.016980173 2.7089336    50
    ## [919]  {bottled water,                                                                                            
    ##         soda}                     => {bottled beer}             0.005083884  0.1754386 0.028978139 2.1785841    50
    ## [920]  {bottled beer,                                                                                             
    ##         bottled water}            => {whole milk}               0.006100661  0.3870968 0.015760041 1.5149609    60
    ## [921]  {bottled beer,                                                                                             
    ##         whole milk}               => {bottled water}            0.006100661  0.2985075 0.020437214 2.7008472    60
    ## [922]  {bottled water,                                                                                            
    ##         whole milk}               => {bottled beer}             0.006100661  0.1775148 0.034367056 2.2043661    60
    ## [923]  {bottled beer,                                                                                             
    ##         yogurt}                   => {whole milk}               0.005185562  0.5604396 0.009252669 2.1933637    51
    ## [924]  {bottled beer,                                                                                             
    ##         whole milk}               => {yogurt}                   0.005185562  0.2537313 0.020437214 1.8188395    51
    ## [925]  {bottled beer,                                                                                             
    ##         rolls/buns}               => {whole milk}               0.005388917  0.3955224 0.013624809 1.5479358    53
    ## [926]  {bottled beer,                                                                                             
    ##         whole milk}               => {rolls/buns}               0.005388917  0.2636816 0.020437214 1.4335591    53
    ## [927]  {bottled beer,                                                                                             
    ##         other vegetables}         => {whole milk}               0.007625826  0.4716981 0.016166751 1.8460609    75
    ## [928]  {bottled beer,                                                                                             
    ##         whole milk}               => {other vegetables}         0.007625826  0.3731343 0.020437214 1.9284162    75
    ## [929]  {other vegetables,                                                                                         
    ##         whole milk}               => {bottled beer}             0.007625826  0.1019022 0.074834774 1.2654140    75
    ## [930]  {brown bread,                                                                                              
    ##         tropical fruit}           => {whole milk}               0.005693950  0.5333333 0.010676157 2.0872795    56
    ## [931]  {brown bread,                                                                                              
    ##         whole milk}               => {tropical fruit}           0.005693950  0.2258065 0.025216065 2.1519442    56
    ## [932]  {tropical fruit,                                                                                           
    ##         whole milk}               => {brown bread}              0.005693950  0.1346154 0.042297916 2.0751447    56
    ## [933]  {brown bread,                                                                                              
    ##         root vegetables}          => {whole milk}               0.005693950  0.5600000 0.010167768 2.1916435    56
    ## [934]  {brown bread,                                                                                              
    ##         whole milk}               => {root vegetables}          0.005693950  0.2258065 0.025216065 2.0716478    56
    ## [935]  {root vegetables,                                                                                          
    ##         whole milk}               => {brown bread}              0.005693950  0.1164241 0.048906965 1.7947197    56
    ## [936]  {brown bread,                                                                                              
    ##         soda}                     => {whole milk}               0.005083884  0.4032258 0.012608033 1.5780843    50
    ## [937]  {brown bread,                                                                                              
    ##         whole milk}               => {soda}                     0.005083884  0.2016129 0.025216065 1.1561883    50
    ## [938]  {soda,                                                                                                     
    ##         whole milk}               => {brown bread}              0.005083884  0.1269036 0.040061007 1.9562640    50
    ## [939]  {brown bread,                                                                                              
    ##         yogurt}                   => {other vegetables}         0.005185562  0.3566434 0.014539908 1.8431883    51
    ## [940]  {brown bread,                                                                                              
    ##         other vegetables}         => {yogurt}                   0.005185562  0.2771739 0.018708693 1.9868844    51
    ## [941]  {other vegetables,                                                                                         
    ##         yogurt}                   => {brown bread}              0.005185562  0.1194379 0.043416370 1.8411789    51
    ## [942]  {brown bread,                                                                                              
    ##         yogurt}                   => {whole milk}               0.007117438  0.4895105 0.014539908 1.9157723    70
    ## [943]  {brown bread,                                                                                              
    ##         whole milk}               => {yogurt}                   0.007117438  0.2822581 0.025216065 2.0233295    70
    ## [944]  {whole milk,                                                                                               
    ##         yogurt}                   => {brown bread}              0.007117438  0.1270417 0.056024403 1.9583943    70
    ## [945]  {brown bread,                                                                                              
    ##         rolls/buns}               => {whole milk}               0.005287239  0.4193548 0.012608033 1.6412077    52
    ## [946]  {brown bread,                                                                                              
    ##         whole milk}               => {rolls/buns}               0.005287239  0.2096774 0.025216065 1.1399544    52
    ## [947]  {brown bread,                                                                                              
    ##         other vegetables}         => {whole milk}               0.009354347  0.5000000 0.018708693 1.9568245    92
    ## [948]  {brown bread,                                                                                              
    ##         whole milk}               => {other vegetables}         0.009354347  0.3709677 0.025216065 1.9172190    92
    ## [949]  {other vegetables,                                                                                         
    ##         whole milk}               => {brown bread}              0.009354347  0.1250000 0.074834774 1.9269201    92
    ## [950]  {domestic eggs,                                                                                            
    ##         margarine}                => {whole milk}               0.005185562  0.6219512 0.008337570 2.4340988    51
    ## [951]  {margarine,                                                                                                
    ##         whole milk}               => {domestic eggs}            0.005185562  0.2142857 0.024199288 3.3774038    51
    ## [952]  {domestic eggs,                                                                                            
    ##         whole milk}               => {margarine}                0.005185562  0.1728814 0.029994916 2.9518891    51
    ## [953]  {margarine,                                                                                                
    ##         root vegetables}          => {other vegetables}         0.005897306  0.5321101 0.011082867 2.7500277    58
    ## [954]  {margarine,                                                                                                
    ##         other vegetables}         => {root vegetables}          0.005897306  0.2989691 0.019725470 2.7428739    58
    ## [955]  {other vegetables,                                                                                         
    ##         root vegetables}          => {margarine}                0.005897306  0.1244635 0.047381800 2.1251714    58
    ## [956]  {margarine,                                                                                                
    ##         yogurt}                   => {other vegetables}         0.005693950  0.4000000 0.014234875 2.0672622    56
    ## [957]  {margarine,                                                                                                
    ##         other vegetables}         => {yogurt}                   0.005693950  0.2886598 0.019725470 2.0692194    56
    ## [958]  {other vegetables,                                                                                         
    ##         yogurt}                   => {margarine}                0.005693950  0.1311475 0.043416370 2.2392987    56
    ## [959]  {margarine,                                                                                                
    ##         yogurt}                   => {whole milk}               0.007015760  0.4928571 0.014234875 1.9288699    69
    ## [960]  {margarine,                                                                                                
    ##         whole milk}               => {yogurt}                   0.007015760  0.2899160 0.024199288 2.0782241    69
    ## [961]  {whole milk,                                                                                               
    ##         yogurt}                   => {margarine}                0.007015760  0.1252269 0.056024403 2.1382052    69
    ## [962]  {margarine,                                                                                                
    ##         rolls/buns}               => {other vegetables}         0.005185562  0.3517241 0.014743264 1.8177651    51
    ## [963]  {margarine,                                                                                                
    ##         other vegetables}         => {rolls/buns}               0.005185562  0.2628866 0.019725470 1.4292370    51
    ## [964]  {other vegetables,                                                                                         
    ##         rolls/buns}               => {margarine}                0.005185562  0.1217184 0.042602949 2.0782990    51
    ## [965]  {margarine,                                                                                                
    ##         rolls/buns}               => {whole milk}               0.007930859  0.5379310 0.014743264 2.1052733    78
    ## [966]  {margarine,                                                                                                
    ##         whole milk}               => {rolls/buns}               0.007930859  0.3277311 0.024199288 1.7817774    78
    ## [967]  {rolls/buns,                                                                                               
    ##         whole milk}               => {margarine}                0.007930859  0.1400359 0.056634469 2.3910645    78
    ## [968]  {margarine,                                                                                                
    ##         other vegetables}         => {whole milk}               0.009252669  0.4690722 0.019725470 1.8357838    91
    ## [969]  {margarine,                                                                                                
    ##         whole milk}               => {other vegetables}         0.009252669  0.3823529 0.024199288 1.9760595    91
    ## [970]  {other vegetables,                                                                                         
    ##         whole milk}               => {margarine}                0.009252669  0.1236413 0.074834774 2.1111323    91
    ## [971]  {butter,                                                                                                   
    ##         domestic eggs}            => {whole milk}               0.005998983  0.6210526 0.009659380 2.4305820    59
    ## [972]  {butter,                                                                                                   
    ##         whole milk}               => {domestic eggs}            0.005998983  0.2177122 0.027554652 3.4314091    59
    ## [973]  {domestic eggs,                                                                                            
    ##         whole milk}               => {butter}                   0.005998983  0.2000000 0.029994916 3.6091743    59
    ## [974]  {butter,                                                                                                   
    ##         whipped/sour cream}       => {other vegetables}         0.005795628  0.5700000 0.010167768 2.9458487    57
    ## [975]  {butter,                                                                                                   
    ##         other vegetables}         => {whipped/sour cream}       0.005795628  0.2893401 0.020030503 4.0363970    57
    ## [976]  {other vegetables,                                                                                         
    ##         whipped/sour cream}       => {butter}                   0.005795628  0.2007042 0.028876462 3.6218827    57
    ## [977]  {butter,                                                                                                   
    ##         whipped/sour cream}       => {whole milk}               0.006710727  0.6600000 0.010167768 2.5830084    66
    ## [978]  {butter,                                                                                                   
    ##         whole milk}               => {whipped/sour cream}       0.006710727  0.2435424 0.027554652 3.3975033    66
    ## [979]  {whipped/sour cream,                                                                                       
    ##         whole milk}               => {butter}                   0.006710727  0.2082019 0.032231825 3.7571846    66
    ## [980]  {butter,                                                                                                   
    ##         citrus fruit}             => {whole milk}               0.005083884  0.5555556 0.009150991 2.1742495    50
    ## [981]  {butter,                                                                                                   
    ##         whole milk}               => {citrus fruit}             0.005083884  0.1845018 0.027554652 2.2292084    50
    ## [982]  {citrus fruit,                                                                                             
    ##         whole milk}               => {butter}                   0.005083884  0.1666667 0.030503305 3.0076453    50
    ## [983]  {bottled water,                                                                                            
    ##         butter}                   => {whole milk}               0.005388917  0.6022727 0.008947636 2.3570841    53
    ## [984]  {butter,                                                                                                   
    ##         whole milk}               => {bottled water}            0.005388917  0.1955720 0.027554652 1.7695034    53
    ## [985]  {bottled water,                                                                                            
    ##         whole milk}               => {butter}                   0.005388917  0.1568047 0.034367056 2.8296781    53
    ## [986]  {butter,                                                                                                   
    ##         tropical fruit}           => {other vegetables}         0.005490595  0.5510204 0.009964413 2.8477592    54
    ## [987]  {butter,                                                                                                   
    ##         other vegetables}         => {tropical fruit}           0.005490595  0.2741117 0.020030503 2.6122949    54
    ## [988]  {other vegetables,                                                                                         
    ##         tropical fruit}           => {butter}                   0.005490595  0.1529745 0.035892222 2.7605583    54
    ## [989]  {butter,                                                                                                   
    ##         tropical fruit}           => {whole milk}               0.006202339  0.6224490 0.009964413 2.4360468    61
    ## [990]  {butter,                                                                                                   
    ##         whole milk}               => {tropical fruit}           0.006202339  0.2250923 0.027554652 2.1451379    61
    ## [991]  {tropical fruit,                                                                                           
    ##         whole milk}               => {butter}                   0.006202339  0.1466346 0.042297916 2.6461494    61
    ## [992]  {butter,                                                                                                   
    ##         root vegetables}          => {other vegetables}         0.006609049  0.5118110 0.012913066 2.6451190    65
    ## [993]  {butter,                                                                                                   
    ##         other vegetables}         => {root vegetables}          0.006609049  0.3299492 0.020030503 3.0270996    65
    ## [994]  {other vegetables,                                                                                         
    ##         root vegetables}          => {butter}                   0.006609049  0.1394850 0.047381800 2.5171280    65
    ## [995]  {butter,                                                                                                   
    ##         root vegetables}          => {whole milk}               0.008235892  0.6377953 0.012913066 2.4961069    81
    ## [996]  {butter,                                                                                                   
    ##         whole milk}               => {root vegetables}          0.008235892  0.2988930 0.027554652 2.7421759    81
    ## [997]  {root vegetables,                                                                                          
    ##         whole milk}               => {butter}                   0.008235892  0.1683992 0.048906965 3.0389098    81
    ## [998]  {butter,                                                                                                   
    ##         yogurt}                   => {other vegetables}         0.006405694  0.4375000 0.014641586 2.2610681    63
    ## [999]  {butter,                                                                                                   
    ##         other vegetables}         => {yogurt}                   0.006405694  0.3197970 0.020030503 2.2924220    63
    ## [1000] {other vegetables,                                                                                         
    ##         yogurt}                   => {butter}                   0.006405694  0.1475410 0.043416370 2.6625056    63
    ## [1001] {butter,                                                                                                   
    ##         yogurt}                   => {whole milk}               0.009354347  0.6388889 0.014641586 2.5003869    92
    ## [1002] {butter,                                                                                                   
    ##         whole milk}               => {yogurt}                   0.009354347  0.3394834 0.027554652 2.4335417    92
    ## [1003] {whole milk,                                                                                               
    ##         yogurt}                   => {butter}                   0.009354347  0.1669691 0.056024403 3.0131038    92
    ## [1004] {butter,                                                                                                   
    ##         rolls/buns}               => {other vegetables}         0.005693950  0.4242424 0.013421454 2.1925508    56
    ## [1005] {butter,                                                                                                   
    ##         other vegetables}         => {rolls/buns}               0.005693950  0.2842640 0.020030503 1.5454594    56
    ## [1006] {other vegetables,                                                                                         
    ##         rolls/buns}               => {butter}                   0.005693950  0.1336516 0.042602949 2.4118587    56
    ## [1007] {butter,                                                                                                   
    ##         rolls/buns}               => {whole milk}               0.006609049  0.4924242 0.013421454 1.9271757    65
    ## [1008] {butter,                                                                                                   
    ##         whole milk}               => {rolls/buns}               0.006609049  0.2398524 0.027554652 1.3040068    65
    ## [1009] {rolls/buns,                                                                                               
    ##         whole milk}               => {butter}                   0.006609049  0.1166966 0.056634469 2.1058917    65
    ## [1010] {butter,                                                                                                   
    ##         other vegetables}         => {whole milk}               0.011489578  0.5736041 0.020030503 2.2448850   113
    ## [1011] {butter,                                                                                                   
    ##         whole milk}               => {other vegetables}         0.011489578  0.4169742 0.027554652 2.1549874   113
    ## [1012] {other vegetables,                                                                                         
    ##         whole milk}               => {butter}                   0.011489578  0.1535326 0.074834774 2.7706297   113
    ## [1013] {newspapers,                                                                                               
    ##         tropical fruit}           => {whole milk}               0.005083884  0.4310345 0.011794611 1.6869177    50
    ## [1014] {newspapers,                                                                                               
    ##         whole milk}               => {tropical fruit}           0.005083884  0.1858736 0.027351296 1.7713827    50
    ## [1015] {tropical fruit,                                                                                           
    ##         whole milk}               => {newspapers}               0.005083884  0.1201923 0.042297916 1.5058488    50
    ## [1016] {newspapers,                                                                                               
    ##         root vegetables}          => {other vegetables}         0.005998983  0.5221239 0.011489578 2.6984175    59
    ## [1017] {newspapers,                                                                                               
    ##         other vegetables}         => {root vegetables}          0.005998983  0.3105263 0.019318760 2.8489051    59
    ## [1018] {other vegetables,                                                                                         
    ##         root vegetables}          => {newspapers}               0.005998983  0.1266094 0.047381800 1.5862470    59
    ## [1019] {newspapers,                                                                                               
    ##         root vegetables}          => {whole milk}               0.005795628  0.5044248 0.011489578 1.9741415    57
    ## [1020] {newspapers,                                                                                               
    ##         whole milk}               => {root vegetables}          0.005795628  0.2118959 0.027351296 1.9440264    57
    ## [1021] {root vegetables,                                                                                          
    ##         whole milk}               => {newspapers}               0.005795628  0.1185031 0.048906965 1.4846856    57
    ## [1022] {newspapers,                                                                                               
    ##         yogurt}                   => {rolls/buns}               0.005083884  0.3311258 0.015353330 1.8002336    50
    ## [1023] {newspapers,                                                                                               
    ##         rolls/buns}               => {yogurt}                   0.005083884  0.2577320 0.019725470 1.8475174    50
    ## [1024] {rolls/buns,                                                                                               
    ##         yogurt}                   => {newspapers}               0.005083884  0.1479290 0.034367056 1.8533524    50
    ## [1025] {newspapers,                                                                                               
    ##         yogurt}                   => {other vegetables}         0.005592272  0.3642384 0.015353330 1.8824408    55
    ## [1026] {newspapers,                                                                                               
    ##         other vegetables}         => {yogurt}                   0.005592272  0.2894737 0.019318760 2.0750537    55
    ## [1027] {other vegetables,                                                                                         
    ##         yogurt}                   => {newspapers}               0.005592272  0.1288056 0.043416370 1.6137621    55
    ## [1028] {newspapers,                                                                                               
    ##         yogurt}                   => {whole milk}               0.006609049  0.4304636 0.015353330 1.6846834    65
    ## [1029] {newspapers,                                                                                               
    ##         whole milk}               => {yogurt}                   0.006609049  0.2416357 0.027351296 1.7321334    65
    ## [1030] {whole milk,                                                                                               
    ##         yogurt}                   => {newspapers}               0.006609049  0.1179673 0.056024403 1.4779729    65
    ## [1031] {newspapers,                                                                                               
    ##         rolls/buns}               => {other vegetables}         0.005490595  0.2783505 0.019725470 1.4385588    54
    ## [1032] {newspapers,                                                                                               
    ##         other vegetables}         => {rolls/buns}               0.005490595  0.2842105 0.019318760 1.5451689    54
    ## [1033] {other vegetables,                                                                                         
    ##         rolls/buns}               => {newspapers}               0.005490595  0.1288783 0.042602949 1.6146725    54
    ## [1034] {newspapers,                                                                                               
    ##         rolls/buns}               => {whole milk}               0.007625826  0.3865979 0.019725470 1.5130086    75
    ## [1035] {newspapers,                                                                                               
    ##         whole milk}               => {rolls/buns}               0.007625826  0.2788104 0.027351296 1.5158100    75
    ## [1036] {rolls/buns,                                                                                               
    ##         whole milk}               => {newspapers}               0.007625826  0.1346499 0.056634469 1.6869833    75
    ## [1037] {newspapers,                                                                                               
    ##         other vegetables}         => {whole milk}               0.008337570  0.4315789 0.019318760 1.6890485    82
    ## [1038] {newspapers,                                                                                               
    ##         whole milk}               => {other vegetables}         0.008337570  0.3048327 0.027351296 1.5754229    82
    ## [1039] {other vegetables,                                                                                         
    ##         whole milk}               => {newspapers}               0.008337570  0.1114130 0.074834774 1.3958564    82
    ## [1040] {domestic eggs,                                                                                            
    ##         whipped/sour cream}       => {other vegetables}         0.005083884  0.5102041 0.009964413 2.6368141    50
    ## [1041] {domestic eggs,                                                                                            
    ##         other vegetables}         => {whipped/sour cream}       0.005083884  0.2283105 0.022267412 3.1850125    50
    ## [1042] {other vegetables,                                                                                         
    ##         whipped/sour cream}       => {domestic eggs}            0.005083884  0.1760563 0.028876462 2.7748623    50
    ## [1043] {domestic eggs,                                                                                            
    ##         whipped/sour cream}       => {whole milk}               0.005693950  0.5714286 0.009964413 2.2363709    56
    ## [1044] {domestic eggs,                                                                                            
    ##         whole milk}               => {whipped/sour cream}       0.005693950  0.1898305 0.029994916 2.6482029    56
    ## [1045] {whipped/sour cream,                                                                                       
    ##         whole milk}               => {domestic eggs}            0.005693950  0.1766562 0.032231825 2.7843161    56
    ## [1046] {domestic eggs,                                                                                            
    ##         pip fruit}                => {whole milk}               0.005388917  0.6235294 0.008642603 2.4402753    53
    ## [1047] {domestic eggs,                                                                                            
    ##         whole milk}               => {pip fruit}                0.005388917  0.1796610 0.029994916 2.3749544    53
    ## [1048] {pip fruit,                                                                                                
    ##         whole milk}               => {domestic eggs}            0.005388917  0.1790541 0.030096594 2.8221100    53
    ## [1049] {citrus fruit,                                                                                             
    ##         domestic eggs}            => {whole milk}               0.005693950  0.5490196 0.010371124 2.1486701    56
    ## [1050] {domestic eggs,                                                                                            
    ##         whole milk}               => {citrus fruit}             0.005693950  0.1898305 0.029994916 2.2935910    56
    ## [1051] {citrus fruit,                                                                                             
    ##         whole milk}               => {domestic eggs}            0.005693950  0.1866667 0.030503305 2.9420940    56
    ## [1052] {domestic eggs,                                                                                            
    ##         tropical fruit}           => {whole milk}               0.006914082  0.6071429 0.011387900 2.3761441    68
    ## [1053] {domestic eggs,                                                                                            
    ##         whole milk}               => {tropical fruit}           0.006914082  0.2305085 0.029994916 2.1967547    68
    ## [1054] {tropical fruit,                                                                                           
    ##         whole milk}               => {domestic eggs}            0.006914082  0.1634615 0.042297916 2.5763529    68
    ## [1055] {domestic eggs,                                                                                            
    ##         root vegetables}          => {other vegetables}         0.007320793  0.5106383 0.014336553 2.6390582    72
    ## [1056] {domestic eggs,                                                                                            
    ##         other vegetables}         => {root vegetables}          0.007320793  0.3287671 0.022267412 3.0162543    72
    ## [1057] {other vegetables,                                                                                         
    ##         root vegetables}          => {domestic eggs}            0.007320793  0.1545064 0.047381800 2.4352096    72
    ## [1058] {domestic eggs,                                                                                            
    ##         root vegetables}          => {whole milk}               0.008540925  0.5957447 0.014336553 2.3315356    84
    ## [1059] {domestic eggs,                                                                                            
    ##         whole milk}               => {root vegetables}          0.008540925  0.2847458 0.029994916 2.6123830    84
    ## [1060] {root vegetables,                                                                                          
    ##         whole milk}               => {domestic eggs}            0.008540925  0.1746362 0.048906965 2.7524788    84
    ## [1061] {domestic eggs,                                                                                            
    ##         soda}                     => {other vegetables}         0.005083884  0.4098361 0.012404677 2.1180965    50
    ## [1062] {domestic eggs,                                                                                            
    ##         other vegetables}         => {soda}                     0.005083884  0.2283105 0.022267412 1.3092908    50
    ## [1063] {other vegetables,                                                                                         
    ##         soda}                     => {domestic eggs}            0.005083884  0.1552795 0.032740214 2.4473941    50
    ## [1064] {domestic eggs,                                                                                            
    ##         soda}                     => {whole milk}               0.005185562  0.4180328 0.012404677 1.6360336    51
    ## [1065] {domestic eggs,                                                                                            
    ##         whole milk}               => {soda}                     0.005185562  0.1728814 0.029994916 0.9914217    51
    ## [1066] {soda,                                                                                                     
    ##         whole milk}               => {domestic eggs}            0.005185562  0.1294416 0.040061007 2.0401577    51
    ## [1067] {domestic eggs,                                                                                            
    ##         yogurt}                   => {other vegetables}         0.005795628  0.4042553 0.014336553 2.0892544    57
    ## [1068] {domestic eggs,                                                                                            
    ##         other vegetables}         => {yogurt}                   0.005795628  0.2602740 0.022267412 1.8657394    57
    ## [1069] {other vegetables,                                                                                         
    ##         yogurt}                   => {domestic eggs}            0.005795628  0.1334895 0.043416370 2.1039565    57
    ## [1070] {domestic eggs,                                                                                            
    ##         yogurt}                   => {whole milk}               0.007727504  0.5390071 0.014336553 2.1094846    76
    ## [1071] {domestic eggs,                                                                                            
    ##         whole milk}               => {yogurt}                   0.007727504  0.2576271 0.029994916 1.8467658    76
    ## [1072] {whole milk,                                                                                               
    ##         yogurt}                   => {domestic eggs}            0.007727504  0.1379310 0.056024403 2.1739611    76
    ## [1073] {domestic eggs,                                                                                            
    ##         rolls/buns}               => {other vegetables}         0.005897306  0.3766234 0.015658363 1.9464482    58
    ## [1074] {domestic eggs,                                                                                            
    ##         other vegetables}         => {rolls/buns}               0.005897306  0.2648402 0.022267412 1.4398580    58
    ## [1075] {other vegetables,                                                                                         
    ##         rolls/buns}               => {domestic eggs}            0.005897306  0.1384248 0.042602949 2.1817438    58
    ## [1076] {domestic eggs,                                                                                            
    ##         rolls/buns}               => {whole milk}               0.006609049  0.4220779 0.015658363 1.6518648    65
    ## [1077] {domestic eggs,                                                                                            
    ##         whole milk}               => {rolls/buns}               0.006609049  0.2203390 0.029994916 1.1979181    65
    ## [1078] {rolls/buns,                                                                                               
    ##         whole milk}               => {domestic eggs}            0.006609049  0.1166966 0.056634469 1.8392804    65
    ## [1079] {domestic eggs,                                                                                            
    ##         other vegetables}         => {whole milk}               0.012302999  0.5525114 0.022267412 2.1623358   121
    ## [1080] {domestic eggs,                                                                                            
    ##         whole milk}               => {other vegetables}         0.012302999  0.4101695 0.029994916 2.1198197   121
    ## [1081] {other vegetables,                                                                                         
    ##         whole milk}               => {domestic eggs}            0.012302999  0.1644022 0.074834774 2.5911785   121
    ## [1082] {bottled water,                                                                                            
    ##         fruit/vegetable juice}    => {soda}                     0.005185562  0.3642857 0.014234875 2.0890671    51
    ## [1083] {fruit/vegetable juice,                                                                                    
    ##         soda}                     => {bottled water}            0.005185562  0.2817680 0.018403660 2.5493908    51
    ## [1084] {bottled water,                                                                                            
    ##         soda}                     => {fruit/vegetable juice}    0.005185562  0.1789474 0.028978139 2.4753128    51
    ## [1085] {bottled water,                                                                                            
    ##         fruit/vegetable juice}    => {whole milk}               0.005795628  0.4071429 0.014234875 1.5934142    57
    ## [1086] {fruit/vegetable juice,                                                                                    
    ##         whole milk}               => {bottled water}            0.005795628  0.2175573 0.026639553 1.9684228    57
    ## [1087] {bottled water,                                                                                            
    ##         whole milk}               => {fruit/vegetable juice}    0.005795628  0.1686391 0.034367056 2.3327216    57
    ## [1088] {fruit/vegetable juice,                                                                                    
    ##         tropical fruit}           => {other vegetables}         0.006609049  0.4814815 0.013726487 2.4883712    65
    ## [1089] {fruit/vegetable juice,                                                                                    
    ##         other vegetables}         => {tropical fruit}           0.006609049  0.3140097 0.021047280 2.9925242    65
    ## [1090] {other vegetables,                                                                                         
    ##         tropical fruit}           => {fruit/vegetable juice}    0.006609049  0.1841360 0.035892222 2.5470849    65
    ## [1091] {fruit/vegetable juice,                                                                                    
    ##         tropical fruit}           => {whole milk}               0.005998983  0.4370370 0.013726487 1.7104096    59
    ## [1092] {fruit/vegetable juice,                                                                                    
    ##         whole milk}               => {tropical fruit}           0.005998983  0.2251908 0.026639553 2.1460774    59
    ## [1093] {tropical fruit,                                                                                           
    ##         whole milk}               => {fruit/vegetable juice}    0.005998983  0.1418269 0.042297916 1.9618394    59
    ## [1094] {fruit/vegetable juice,                                                                                    
    ##         root vegetables}          => {other vegetables}         0.006609049  0.5508475 0.011997966 2.8468653    65
    ## [1095] {fruit/vegetable juice,                                                                                    
    ##         other vegetables}         => {root vegetables}          0.006609049  0.3140097 0.021047280 2.8808629    65
    ## [1096] {other vegetables,                                                                                         
    ##         root vegetables}          => {fruit/vegetable juice}    0.006609049  0.1394850 0.047381800 1.9294441    65
    ## [1097] {fruit/vegetable juice,                                                                                    
    ##         root vegetables}          => {whole milk}               0.006507372  0.5423729 0.011997966 2.1226571    64
    ## [1098] {fruit/vegetable juice,                                                                                    
    ##         whole milk}               => {root vegetables}          0.006507372  0.2442748 0.026639553 2.2410847    64
    ## [1099] {root vegetables,                                                                                          
    ##         whole milk}               => {fruit/vegetable juice}    0.006507372  0.1330561 0.048906965 1.8405163    64
    ## [1100] {fruit/vegetable juice,                                                                                    
    ##         soda}                     => {yogurt}                   0.005083884  0.2762431 0.018403660 1.9802120    50
    ## [1101] {fruit/vegetable juice,                                                                                    
    ##         yogurt}                   => {soda}                     0.005083884  0.2717391 0.018708693 1.5583407    50
    ## [1102] {soda,                                                                                                     
    ##         yogurt}                   => {fruit/vegetable juice}    0.005083884  0.1858736 0.027351296 2.5711208    50
    ## [1103] {fruit/vegetable juice,                                                                                    
    ##         soda}                     => {whole milk}               0.006100661  0.3314917 0.018403660 1.2973422    60
    ## [1104] {fruit/vegetable juice,                                                                                    
    ##         whole milk}               => {soda}                     0.006100661  0.2290076 0.026639553 1.3132887    60
    ## [1105] {soda,                                                                                                     
    ##         whole milk}               => {fruit/vegetable juice}    0.006100661  0.1522843 0.040061007 2.1064919    60
    ## [1106] {fruit/vegetable juice,                                                                                    
    ##         yogurt}                   => {other vegetables}         0.008235892  0.4402174 0.018708693 2.2751120    81
    ## [1107] {fruit/vegetable juice,                                                                                    
    ##         other vegetables}         => {yogurt}                   0.008235892  0.3913043 0.021047280 2.8050133    81
    ## [1108] {other vegetables,                                                                                         
    ##         yogurt}                   => {fruit/vegetable juice}    0.008235892  0.1896956 0.043416370 2.6239884    81
    ## [1109] {fruit/vegetable juice,                                                                                    
    ##         yogurt}                   => {whole milk}               0.009456024  0.5054348 0.018708693 1.9780943    93
    ## [1110] {fruit/vegetable juice,                                                                                    
    ##         whole milk}               => {yogurt}                   0.009456024  0.3549618 0.026639553 2.5444968    93
    ## [1111] {whole milk,                                                                                               
    ##         yogurt}                   => {fruit/vegetable juice}    0.009456024  0.1687840 0.056024403 2.3347270    93
    ## [1112] {fruit/vegetable juice,                                                                                    
    ##         rolls/buns}               => {whole milk}               0.005592272  0.3846154 0.014539908 1.5052496    55
    ## [1113] {fruit/vegetable juice,                                                                                    
    ##         whole milk}               => {rolls/buns}               0.005592272  0.2099237 0.026639553 1.1412931    55
    ## [1114] {fruit/vegetable juice,                                                                                    
    ##         other vegetables}         => {whole milk}               0.010472801  0.4975845 0.021047280 1.9473713   103
    ## [1115] {fruit/vegetable juice,                                                                                    
    ##         whole milk}               => {other vegetables}         0.010472801  0.3931298 0.026639553 2.0317558   103
    ## [1116] {other vegetables,                                                                                         
    ##         whole milk}               => {fruit/vegetable juice}    0.010472801  0.1399457 0.074834774 1.9358164   103
    ## [1117] {pip fruit,                                                                                                
    ##         whipped/sour cream}       => {other vegetables}         0.005592272  0.6043956 0.009252669 3.1236105    55
    ## [1118] {other vegetables,                                                                                         
    ##         whipped/sour cream}       => {pip fruit}                0.005592272  0.1936620 0.028876462 2.5600343    55
    ## [1119] {other vegetables,                                                                                         
    ##         pip fruit}                => {whipped/sour cream}       0.005592272  0.2140078 0.026131164 2.9854844    55
    ## [1120] {pip fruit,                                                                                                
    ##         whipped/sour cream}       => {whole milk}               0.005998983  0.6483516 0.009252669 2.5374208    59
    ## [1121] {whipped/sour cream,                                                                                       
    ##         whole milk}               => {pip fruit}                0.005998983  0.1861199 0.032231825 2.4603346    59
    ## [1122] {pip fruit,                                                                                                
    ##         whole milk}               => {whipped/sour cream}       0.005998983  0.1993243 0.030096594 2.7806450    59
    ## [1123] {citrus fruit,                                                                                             
    ##         whipped/sour cream}       => {other vegetables}         0.005693950  0.5233645 0.010879512 2.7048291    56
    ## [1124] {other vegetables,                                                                                         
    ##         whipped/sour cream}       => {citrus fruit}             0.005693950  0.1971831 0.028876462 2.3824272    56
    ## [1125] {citrus fruit,                                                                                             
    ##         other vegetables}         => {whipped/sour cream}       0.005693950  0.1971831 0.028876462 2.7507741    56
    ## [1126] {citrus fruit,                                                                                             
    ##         whipped/sour cream}       => {whole milk}               0.006304016  0.5794393 0.010879512 2.2677219    62
    ## [1127] {whipped/sour cream,                                                                                       
    ##         whole milk}               => {citrus fruit}             0.006304016  0.1955836 0.032231825 2.3631016    62
    ## [1128] {citrus fruit,                                                                                             
    ##         whole milk}               => {whipped/sour cream}       0.006304016  0.2066667 0.030503305 2.8830733    62
    ## [1129] {sausage,                                                                                                  
    ##         whipped/sour cream}       => {whole milk}               0.005083884  0.5617978 0.009049314 2.1986792    50
    ## [1130] {whipped/sour cream,                                                                                       
    ##         whole milk}               => {sausage}                  0.005083884  0.1577287 0.032231825 1.6788548    50
    ## [1131] {sausage,                                                                                                  
    ##         whole milk}               => {whipped/sour cream}       0.005083884  0.1700680 0.029893238 2.3725093    50
    ## [1132] {tropical fruit,                                                                                           
    ##         whipped/sour cream}       => {yogurt}                   0.006202339  0.4485294 0.013828165 3.2152236    61
    ## [1133] {whipped/sour cream,                                                                                       
    ##         yogurt}                   => {tropical fruit}           0.006202339  0.2990196 0.020742247 2.8496685    61
    ## [1134] {tropical fruit,                                                                                           
    ##         yogurt}                   => {whipped/sour cream}       0.006202339  0.2118056 0.029283172 2.9547626    61
    ## [1135] {tropical fruit,                                                                                           
    ##         whipped/sour cream}       => {other vegetables}         0.007829181  0.5661765 0.013828165 2.9260881    77
    ## [1136] {other vegetables,                                                                                         
    ##         whipped/sour cream}       => {tropical fruit}           0.007829181  0.2711268 0.028876462 2.5838485    77
    ## [1137] {other vegetables,                                                                                         
    ##         tropical fruit}           => {whipped/sour cream}       0.007829181  0.2181303 0.035892222 3.0429952    77
    ## [1138] {tropical fruit,                                                                                           
    ##         whipped/sour cream}       => {whole milk}               0.007930859  0.5735294 0.013828165 2.2445928    78
    ## [1139] {whipped/sour cream,                                                                                       
    ##         whole milk}               => {tropical fruit}           0.007930859  0.2460568 0.032231825 2.3449307    78
    ## [1140] {tropical fruit,                                                                                           
    ##         whole milk}               => {whipped/sour cream}       0.007930859  0.1875000 0.042297916 2.6156915    78
    ## [1141] {root vegetables,                                                                                          
    ##         whipped/sour cream}       => {yogurt}                   0.006405694  0.3750000 0.017081851 2.6881378    63
    ## [1142] {whipped/sour cream,                                                                                       
    ##         yogurt}                   => {root vegetables}          0.006405694  0.3088235 0.020742247 2.8332830    63
    ## [1143] {root vegetables,                                                                                          
    ##         yogurt}                   => {whipped/sour cream}       0.006405694  0.2480315 0.025826131 3.4601273    63
    ## [1144] {root vegetables,                                                                                          
    ##         whipped/sour cream}       => {other vegetables}         0.008540925  0.5000000 0.017081851 2.5840778    84
    ## [1145] {other vegetables,                                                                                         
    ##         whipped/sour cream}       => {root vegetables}          0.008540925  0.2957746 0.028876462 2.7135668    84
    ## [1146] {other vegetables,                                                                                         
    ##         root vegetables}          => {whipped/sour cream}       0.008540925  0.1802575 0.047381800 2.5146562    84
    ## [1147] {root vegetables,                                                                                          
    ##         whipped/sour cream}       => {whole milk}               0.009456024  0.5535714 0.017081851 2.1664843    93
    ## [1148] {whipped/sour cream,                                                                                       
    ##         whole milk}               => {root vegetables}          0.009456024  0.2933754 0.032231825 2.6915550    93
    ## [1149] {root vegetables,                                                                                          
    ##         whole milk}               => {whipped/sour cream}       0.009456024  0.1933472 0.048906965 2.6972619    93
    ## [1150] {soda,                                                                                                     
    ##         whipped/sour cream}       => {whole milk}               0.005490595  0.4736842 0.011591256 1.8538337    54
    ## [1151] {whipped/sour cream,                                                                                       
    ##         whole milk}               => {soda}                     0.005490595  0.1703470 0.032231825 0.9768879    54
    ## [1152] {soda,                                                                                                     
    ##         whole milk}               => {whipped/sour cream}       0.005490595  0.1370558 0.040061007 1.9119775    54
    ## [1153] {whipped/sour cream,                                                                                       
    ##         yogurt}                   => {other vegetables}         0.010167768  0.4901961 0.020742247 2.5334096   100
    ## [1154] {other vegetables,                                                                                         
    ##         whipped/sour cream}       => {yogurt}                   0.010167768  0.3521127 0.028876462 2.5240730   100
    ## [1155] {other vegetables,                                                                                         
    ##         yogurt}                   => {whipped/sour cream}       0.010167768  0.2341920 0.043416370 3.2670620   100
    ## [1156] {whipped/sour cream,                                                                                       
    ##         yogurt}                   => {whole milk}               0.010879512  0.5245098 0.020742247 2.0527473   107
    ## [1157] {whipped/sour cream,                                                                                       
    ##         whole milk}               => {yogurt}                   0.010879512  0.3375394 0.032231825 2.4196066   107
    ## [1158] {whole milk,                                                                                               
    ##         yogurt}                   => {whipped/sour cream}       0.010879512  0.1941924 0.056024403 2.7090525   107
    ## [1159] {rolls/buns,                                                                                               
    ##         whipped/sour cream}       => {other vegetables}         0.006710727  0.4583333 0.014641586 2.3687380    66
    ## [1160] {other vegetables,                                                                                         
    ##         whipped/sour cream}       => {rolls/buns}               0.006710727  0.2323944 0.028876462 1.2634597    66
    ## [1161] {other vegetables,                                                                                         
    ##         rolls/buns}               => {whipped/sour cream}       0.006710727  0.1575179 0.042602949 2.1974306    66
    ## [1162] {rolls/buns,                                                                                               
    ##         whipped/sour cream}       => {whole milk}               0.007829181  0.5347222 0.014641586 2.0927151    77
    ## [1163] {whipped/sour cream,                                                                                       
    ##         whole milk}               => {rolls/buns}               0.007829181  0.2429022 0.032231825 1.3205877    77
    ## [1164] {rolls/buns,                                                                                               
    ##         whole milk}               => {whipped/sour cream}       0.007829181  0.1382406 0.056634469 1.9285050    77
    ## [1165] {other vegetables,                                                                                         
    ##         whipped/sour cream}       => {whole milk}               0.014641586  0.5070423 0.028876462 1.9843854   144
    ## [1166] {whipped/sour cream,                                                                                       
    ##         whole milk}               => {other vegetables}         0.014641586  0.4542587 0.032231825 2.3476795   144
    ## [1167] {other vegetables,                                                                                         
    ##         whole milk}               => {whipped/sour cream}       0.014641586  0.1956522 0.074834774 2.7294172   144
    ## [1168] {pastry,                                                                                                   
    ##         pip fruit}                => {whole milk}               0.005083884  0.4761905 0.010676157 1.8636424    50
    ## [1169] {pip fruit,                                                                                                
    ##         whole milk}               => {pastry}                   0.005083884  0.1689189 0.030096594 1.8986486    50
    ## [1170] {pastry,                                                                                                   
    ##         whole milk}               => {pip fruit}                0.005083884  0.1529052 0.033248602 2.0212670    50
    ## [1171] {citrus fruit,                                                                                             
    ##         pip fruit}                => {tropical fruit}           0.005592272  0.4044118 0.013828165 3.8540598    55
    ## [1172] {pip fruit,                                                                                                
    ##         tropical fruit}           => {citrus fruit}             0.005592272  0.2736318 0.020437214 3.3061046    55
    ## [1173] {citrus fruit,                                                                                             
    ##         tropical fruit}           => {pip fruit}                0.005592272  0.2806122 0.019928826 3.7094374    55
    ## [1174] {citrus fruit,                                                                                             
    ##         pip fruit}                => {other vegetables}         0.005897306  0.4264706 0.013828165 2.2040663    58
    ## [1175] {other vegetables,                                                                                         
    ##         pip fruit}                => {citrus fruit}             0.005897306  0.2256809 0.026131164 2.7267469    58
    ## [1176] {citrus fruit,                                                                                             
    ##         other vegetables}         => {pip fruit}                0.005897306  0.2042254 0.028876462 2.6996725    58
    ## [1177] {citrus fruit,                                                                                             
    ##         pip fruit}                => {whole milk}               0.005185562  0.3750000 0.013828165 1.4676184    51
    ## [1178] {pip fruit,                                                                                                
    ##         whole milk}               => {citrus fruit}             0.005185562  0.1722973 0.030096594 2.0817493    51
    ## [1179] {citrus fruit,                                                                                             
    ##         whole milk}               => {pip fruit}                0.005185562  0.1700000 0.030503305 2.2472446    51
    ## [1180] {pip fruit,                                                                                                
    ##         sausage}                  => {whole milk}               0.005592272  0.5188679 0.010777834 2.0306669    55
    ## [1181] {pip fruit,                                                                                                
    ##         whole milk}               => {sausage}                  0.005592272  0.1858108 0.030096594 1.9777590    55
    ## [1182] {sausage,                                                                                                  
    ##         whole milk}               => {pip fruit}                0.005592272  0.1870748 0.029893238 2.4729583    55
    ## [1183] {pip fruit,                                                                                                
    ##         tropical fruit}           => {root vegetables}          0.005287239  0.2587065 0.020437214 2.3734870    52
    ## [1184] {pip fruit,                                                                                                
    ##         root vegetables}          => {tropical fruit}           0.005287239  0.3398693 0.015556685 3.2389674    52
    ## [1185] {root vegetables,                                                                                          
    ##         tropical fruit}           => {pip fruit}                0.005287239  0.2512077 0.021047280 3.3207366    52
    ## [1186] {pip fruit,                                                                                                
    ##         tropical fruit}           => {yogurt}                   0.006405694  0.3134328 0.020437214 2.2468017    63
    ## [1187] {pip fruit,                                                                                                
    ##         yogurt}                   => {tropical fruit}           0.006405694  0.3559322 0.017996950 3.3920477    63
    ## [1188] {tropical fruit,                                                                                           
    ##         yogurt}                   => {pip fruit}                0.006405694  0.2187500 0.029283172 2.8916751    63
    ## [1189] {pip fruit,                                                                                                
    ##         tropical fruit}           => {other vegetables}         0.009456024  0.4626866 0.020437214 2.3912361    93
    ## [1190] {other vegetables,                                                                                         
    ##         pip fruit}                => {tropical fruit}           0.009456024  0.3618677 0.026131164 3.4486132    93
    ## [1191] {other vegetables,                                                                                         
    ##         tropical fruit}           => {pip fruit}                0.009456024  0.2634561 0.035892222 3.4826487    93
    ## [1192] {pip fruit,                                                                                                
    ##         tropical fruit}           => {whole milk}               0.008439248  0.4129353 0.020437214 1.6160839    83
    ## [1193] {pip fruit,                                                                                                
    ##         whole milk}               => {tropical fruit}           0.008439248  0.2804054 0.030096594 2.6722744    83
    ## [1194] {tropical fruit,                                                                                           
    ##         whole milk}               => {pip fruit}                0.008439248  0.1995192 0.042297916 2.6374619    83
    ## [1195] {pip fruit,                                                                                                
    ##         root vegetables}          => {yogurt}                   0.005287239  0.3398693 0.015556685 2.4363079    52
    ## [1196] {pip fruit,                                                                                                
    ##         yogurt}                   => {root vegetables}          0.005287239  0.2937853 0.017996950 2.6953158    52
    ## [1197] {root vegetables,                                                                                          
    ##         yogurt}                   => {pip fruit}                0.005287239  0.2047244 0.025826131 2.7062696    52
    ## [1198] {pip fruit,                                                                                                
    ##         root vegetables}          => {other vegetables}         0.008134215  0.5228758 0.015556685 2.7023036    80
    ## [1199] {other vegetables,                                                                                         
    ##         pip fruit}                => {root vegetables}          0.008134215  0.3112840 0.026131164 2.8558569    80
    ## [1200] {other vegetables,                                                                                         
    ##         root vegetables}          => {pip fruit}                0.008134215  0.1716738 0.047381800 2.2693710    80
    ## [1201] {pip fruit,                                                                                                
    ##         root vegetables}          => {whole milk}               0.008947636  0.5751634 0.015556685 2.2509877    88
    ## [1202] {pip fruit,                                                                                                
    ##         whole milk}               => {root vegetables}          0.008947636  0.2972973 0.030096594 2.7275363    88
    ## [1203] {root vegetables,                                                                                          
    ##         whole milk}               => {pip fruit}                0.008947636  0.1829522 0.048906965 2.4184606    88
    ## [1204] {pip fruit,                                                                                                
    ##         yogurt}                   => {other vegetables}         0.008134215  0.4519774 0.017996950 2.3358895    80
    ## [1205] {other vegetables,                                                                                         
    ##         pip fruit}                => {yogurt}                   0.008134215  0.3112840 0.026131164 2.2313984    80
    ## [1206] {other vegetables,                                                                                         
    ##         yogurt}                   => {pip fruit}                0.008134215  0.1873536 0.043416370 2.4766438    80
    ## [1207] {pip fruit,                                                                                                
    ##         yogurt}                   => {whole milk}               0.009557702  0.5310734 0.017996950 2.0784351    94
    ## [1208] {pip fruit,                                                                                                
    ##         whole milk}               => {yogurt}                   0.009557702  0.3175676 0.030096594 2.2764410    94
    ## [1209] {whole milk,                                                                                               
    ##         yogurt}                   => {pip fruit}                0.009557702  0.1705989 0.056024403 2.2551617    94
    ## [1210] {pip fruit,                                                                                                
    ##         rolls/buns}               => {other vegetables}         0.005083884  0.3649635 0.013929842 1.8861882    50
    ## [1211] {other vegetables,                                                                                         
    ##         pip fruit}                => {rolls/buns}               0.005083884  0.1945525 0.026131164 1.0577248    50
    ## [1212] {other vegetables,                                                                                         
    ##         rolls/buns}               => {pip fruit}                0.005083884  0.1193317 0.042602949 1.5774566    50
    ## [1213] {pip fruit,                                                                                                
    ##         rolls/buns}               => {whole milk}               0.006202339  0.4452555 0.013929842 1.7425737    61
    ## [1214] {pip fruit,                                                                                                
    ##         whole milk}               => {rolls/buns}               0.006202339  0.2060811 0.030096594 1.1204021    61
    ## [1215] {rolls/buns,                                                                                               
    ##         whole milk}               => {pip fruit}                0.006202339  0.1095153 0.056634469 1.4476916    61
    ## [1216] {other vegetables,                                                                                         
    ##         pip fruit}                => {whole milk}               0.013523132  0.5175097 0.026131164 2.0253514   133
    ## [1217] {pip fruit,                                                                                                
    ##         whole milk}               => {other vegetables}         0.013523132  0.4493243 0.030096594 2.3221780   133
    ## [1218] {other vegetables,                                                                                         
    ##         whole milk}               => {pip fruit}                0.013523132  0.1807065 0.074834774 2.3887751   133
    ## [1219] {pastry,                                                                                                   
    ##         sausage}                  => {whole milk}               0.005693950  0.4552846 0.012506355 1.7818239    56
    ## [1220] {pastry,                                                                                                   
    ##         whole milk}               => {sausage}                  0.005693950  0.1712538 0.033248602 1.8228153    56
    ## [1221] {sausage,                                                                                                  
    ##         whole milk}               => {pastry}                   0.005693950  0.1904762 0.029893238 2.1409524    56
    ## [1222] {pastry,                                                                                                   
    ##         tropical fruit}           => {other vegetables}         0.005083884  0.3846154 0.013218099 1.9877521    50
    ## [1223] {other vegetables,                                                                                         
    ##         pastry}                   => {tropical fruit}           0.005083884  0.2252252 0.022572445 2.1464051    50
    ## [1224] {other vegetables,                                                                                         
    ##         tropical fruit}           => {pastry}                   0.005083884  0.1416431 0.035892222 1.5920680    50
    ## [1225] {pastry,                                                                                                   
    ##         tropical fruit}           => {whole milk}               0.006710727  0.5076923 0.013218099 1.9869295    66
    ## [1226] {pastry,                                                                                                   
    ##         whole milk}               => {tropical fruit}           0.006710727  0.2018349 0.033248602 1.9234941    66
    ## [1227] {tropical fruit,                                                                                           
    ##         whole milk}               => {pastry}                   0.006710727  0.1586538 0.042297916 1.7832692    66
    ## [1228] {pastry,                                                                                                   
    ##         root vegetables}          => {other vegetables}         0.005897306  0.5370370 0.010981190 2.7754909    58
    ## [1229] {other vegetables,                                                                                         
    ##         pastry}                   => {root vegetables}          0.005897306  0.2612613 0.022572445 2.3969258    58
    ## [1230] {other vegetables,                                                                                         
    ##         root vegetables}          => {pastry}                   0.005897306  0.1244635 0.047381800 1.3989700    58
    ## [1231] {pastry,                                                                                                   
    ##         root vegetables}          => {whole milk}               0.005693950  0.5185185 0.010981190 2.0292995    56
    ## [1232] {pastry,                                                                                                   
    ##         whole milk}               => {root vegetables}          0.005693950  0.1712538 0.033248602 1.5711580    56
    ## [1233] {root vegetables,                                                                                          
    ##         whole milk}               => {pastry}                   0.005693950  0.1164241 0.048906965 1.3086071    56
    ## [1234] {pastry,                                                                                                   
    ##         soda}                     => {rolls/buns}               0.005388917  0.2560386 0.021047280 1.3920067    53
    ## [1235] {pastry,                                                                                                   
    ##         rolls/buns}               => {soda}                     0.005388917  0.2572816 0.020945602 1.4754309    53
    ## [1236] {rolls/buns,                                                                                               
    ##         soda}                     => {pastry}                   0.005388917  0.1405836 0.038332486 1.5801592    53
    ## [1237] {pastry,                                                                                                   
    ##         soda}                     => {other vegetables}         0.005490595  0.2608696 0.021047280 1.3482145    54
    ## [1238] {other vegetables,                                                                                         
    ##         pastry}                   => {soda}                     0.005490595  0.2432432 0.022572445 1.3949255    54
    ## [1239] {other vegetables,                                                                                         
    ##         soda}                     => {pastry}                   0.005490595  0.1677019 0.032740214 1.8849689    54
    ## [1240] {pastry,                                                                                                   
    ##         soda}                     => {whole milk}               0.008235892  0.3913043 0.021047280 1.5314279    81
    ## [1241] {pastry,                                                                                                   
    ##         whole milk}               => {soda}                     0.008235892  0.2477064 0.033248602 1.4205205    81
    ## [1242] {soda,                                                                                                     
    ##         whole milk}               => {pastry}                   0.008235892  0.2055838 0.040061007 2.3107614    81
    ## [1243] {pastry,                                                                                                   
    ##         yogurt}                   => {rolls/buns}               0.005795628  0.3275862 0.017691917 1.7809897    57
    ## [1244] {pastry,                                                                                                   
    ##         rolls/buns}               => {yogurt}                   0.005795628  0.2766990 0.020945602 1.9834803    57
    ## [1245] {rolls/buns,                                                                                               
    ##         yogurt}                   => {pastry}                   0.005795628  0.1686391 0.034367056 1.8955030    57
    ## [1246] {pastry,                                                                                                   
    ##         yogurt}                   => {other vegetables}         0.006609049  0.3735632 0.017691917 1.9306328    65
    ## [1247] {other vegetables,                                                                                         
    ##         pastry}                   => {yogurt}                   0.006609049  0.2927928 0.022572445 2.0988463    65
    ## [1248] {other vegetables,                                                                                         
    ##         yogurt}                   => {pastry}                   0.006609049  0.1522248 0.043416370 1.7110070    65
    ## [1249] {pastry,                                                                                                   
    ##         yogurt}                   => {whole milk}               0.009150991  0.5172414 0.017691917 2.0243012    90
    ## [1250] {pastry,                                                                                                   
    ##         whole milk}               => {yogurt}                   0.009150991  0.2752294 0.033248602 1.9729451    90
    ## [1251] {whole milk,                                                                                               
    ##         yogurt}                   => {pastry}                   0.009150991  0.1633394 0.056024403 1.8359347    90
    ## [1252] {pastry,                                                                                                   
    ##         rolls/buns}               => {other vegetables}         0.006100661  0.2912621 0.020945602 1.5052880    60
    ## [1253] {other vegetables,                                                                                         
    ##         pastry}                   => {rolls/buns}               0.006100661  0.2702703 0.022572445 1.4693798    60
    ## [1254] {other vegetables,                                                                                         
    ##         rolls/buns}               => {pastry}                   0.006100661  0.1431981 0.042602949 1.6095465    60
    ## [1255] {pastry,                                                                                                   
    ##         rolls/buns}               => {whole milk}               0.008540925  0.4077670 0.020945602 1.5958569    84
    ## [1256] {pastry,                                                                                                   
    ##         whole milk}               => {rolls/buns}               0.008540925  0.2568807 0.033248602 1.3965849    84
    ## [1257] {rolls/buns,                                                                                               
    ##         whole milk}               => {pastry}                   0.008540925  0.1508079 0.056634469 1.6950808    84
    ## [1258] {other vegetables,                                                                                         
    ##         pastry}                   => {whole milk}               0.010574479  0.4684685 0.022572445 1.8334212   104
    ## [1259] {pastry,                                                                                                   
    ##         whole milk}               => {other vegetables}         0.010574479  0.3180428 0.033248602 1.6436947   104
    ## [1260] {other vegetables,                                                                                         
    ##         whole milk}               => {pastry}                   0.010574479  0.1413043 0.074834774 1.5882609   104
    ## [1261] {bottled water,                                                                                            
    ##         citrus fruit}             => {other vegetables}         0.005083884  0.3759398 0.013523132 1.9429156    50
    ## [1262] {citrus fruit,                                                                                             
    ##         other vegetables}         => {bottled water}            0.005083884  0.1760563 0.028876462 1.5929292    50
    ## [1263] {bottled water,                                                                                            
    ##         other vegetables}         => {citrus fruit}             0.005083884  0.2049180 0.024809354 2.4758831    50
    ## [1264] {bottled water,                                                                                            
    ##         citrus fruit}             => {whole milk}               0.005897306  0.4360902 0.013523132 1.7067041    58
    ## [1265] {citrus fruit,                                                                                             
    ##         whole milk}               => {bottled water}            0.005897306  0.1933333 0.030503305 1.7492487    58
    ## [1266] {bottled water,                                                                                            
    ##         whole milk}               => {citrus fruit}             0.005897306  0.1715976 0.034367056 2.0732957    58
    ## [1267] {citrus fruit,                                                                                             
    ##         tropical fruit}           => {root vegetables}          0.005693950  0.2857143 0.019928826 2.6212687    56
    ## [1268] {citrus fruit,                                                                                             
    ##         root vegetables}          => {tropical fruit}           0.005693950  0.3218391 0.017691917 3.0671389    56
    ## [1269] {root vegetables,                                                                                          
    ##         tropical fruit}           => {citrus fruit}             0.005693950  0.2705314 0.021047280 3.2686441    56
    ## [1270] {citrus fruit,                                                                                             
    ##         tropical fruit}           => {yogurt}                   0.006304016  0.3163265 0.019928826 2.2675448    62
    ## [1271] {citrus fruit,                                                                                             
    ##         yogurt}                   => {tropical fruit}           0.006304016  0.2910798 0.021657346 2.7740019    62
    ## [1272] {tropical fruit,                                                                                           
    ##         yogurt}                   => {citrus fruit}             0.006304016  0.2152778 0.029283172 2.6010528    62
    ## [1273] {citrus fruit,                                                                                             
    ##         tropical fruit}           => {other vegetables}         0.009049314  0.4540816 0.019928826 2.3467645    89
    ## [1274] {citrus fruit,                                                                                             
    ##         other vegetables}         => {tropical fruit}           0.009049314  0.3133803 0.028876462 2.9865262    89
    ## [1275] {other vegetables,                                                                                         
    ##         tropical fruit}           => {citrus fruit}             0.009049314  0.2521246 0.035892222 3.0462480    89
    ## [1276] {citrus fruit,                                                                                             
    ##         tropical fruit}           => {whole milk}               0.009049314  0.4540816 0.019928826 1.7771161    89
    ## [1277] {citrus fruit,                                                                                             
    ##         whole milk}               => {tropical fruit}           0.009049314  0.2966667 0.030503305 2.8272448    89
    ## [1278] {tropical fruit,                                                                                           
    ##         whole milk}               => {citrus fruit}             0.009049314  0.2139423 0.042297916 2.5849172    89
    ## [1279] {citrus fruit,                                                                                             
    ##         root vegetables}          => {other vegetables}         0.010371124  0.5862069 0.017691917 3.0296084   102
    ## [1280] {citrus fruit,                                                                                             
    ##         other vegetables}         => {root vegetables}          0.010371124  0.3591549 0.028876462 3.2950455   102
    ## [1281] {other vegetables,                                                                                         
    ##         root vegetables}          => {citrus fruit}             0.010371124  0.2188841 0.047381800 2.6446257   102
    ## [1282] {citrus fruit,                                                                                             
    ##         root vegetables}          => {whole milk}               0.009150991  0.5172414 0.017691917 2.0243012    90
    ## [1283] {citrus fruit,                                                                                             
    ##         whole milk}               => {root vegetables}          0.009150991  0.3000000 0.030503305 2.7523321    90
    ## [1284] {root vegetables,                                                                                          
    ##         whole milk}               => {citrus fruit}             0.009150991  0.1871102 0.048906965 2.2607232    90
    ## [1285] {citrus fruit,                                                                                             
    ##         yogurt}                   => {rolls/buns}               0.005795628  0.2676056 0.021657346 1.4548930    57
    ## [1286] {citrus fruit,                                                                                             
    ##         rolls/buns}               => {yogurt}                   0.005795628  0.3454545 0.016776817 2.4763451    57
    ## [1287] {rolls/buns,                                                                                               
    ##         yogurt}                   => {citrus fruit}             0.005795628  0.1686391 0.034367056 2.0375492    57
    ## [1288] {citrus fruit,                                                                                             
    ##         yogurt}                   => {other vegetables}         0.007625826  0.3521127 0.021657346 1.8197731    75
    ## [1289] {citrus fruit,                                                                                             
    ##         other vegetables}         => {yogurt}                   0.007625826  0.2640845 0.028876462 1.8930548    75
    ## [1290] {other vegetables,                                                                                         
    ##         yogurt}                   => {citrus fruit}             0.007625826  0.1756440 0.043416370 2.1221855    75
    ## [1291] {citrus fruit,                                                                                             
    ##         yogurt}                   => {whole milk}               0.010269446  0.4741784 0.021657346 1.8557678   101
    ## [1292] {citrus fruit,                                                                                             
    ##         whole milk}               => {yogurt}                   0.010269446  0.3366667 0.030503305 2.4133503   101
    ## [1293] {whole milk,                                                                                               
    ##         yogurt}                   => {citrus fruit}             0.010269446  0.1833031 0.056024403 2.2147246   101
    ## [1294] {citrus fruit,                                                                                             
    ##         rolls/buns}               => {other vegetables}         0.005998983  0.3575758 0.016776817 1.8480071    59
    ## [1295] {citrus fruit,                                                                                             
    ##         other vegetables}         => {rolls/buns}               0.005998983  0.2077465 0.028876462 1.1294564    59
    ## [1296] {other vegetables,                                                                                         
    ##         rolls/buns}               => {citrus fruit}             0.005998983  0.1408115 0.042602949 1.7013276    59
    ## [1297] {citrus fruit,                                                                                             
    ##         rolls/buns}               => {whole milk}               0.007219115  0.4303030 0.016776817 1.6840550    71
    ## [1298] {citrus fruit,                                                                                             
    ##         whole milk}               => {rolls/buns}               0.007219115  0.2366667 0.030503305 1.2866869    71
    ## [1299] {rolls/buns,                                                                                               
    ##         whole milk}               => {citrus fruit}             0.007219115  0.1274686 0.056634469 1.5401149    71
    ## [1300] {citrus fruit,                                                                                             
    ##         other vegetables}         => {whole milk}               0.013014743  0.4507042 0.028876462 1.7638982   128
    ## [1301] {citrus fruit,                                                                                             
    ##         whole milk}               => {other vegetables}         0.013014743  0.4266667 0.030503305 2.2050797   128
    ## [1302] {other vegetables,                                                                                         
    ##         whole milk}               => {citrus fruit}             0.013014743  0.1739130 0.074834774 2.1012712   128
    ## [1303] {sausage,                                                                                                  
    ##         shopping bags}            => {soda}                     0.005693950  0.3636364 0.015658363 2.0853432    56
    ## [1304] {shopping bags,                                                                                            
    ##         soda}                     => {sausage}                  0.005693950  0.2314050 0.024605999 2.4630604    56
    ## [1305] {sausage,                                                                                                  
    ##         soda}                     => {shopping bags}            0.005693950  0.2343096 0.024300966 2.3781580    56
    ## [1306] {sausage,                                                                                                  
    ##         shopping bags}            => {rolls/buns}               0.005998983  0.3831169 0.015658363 2.0828936    59
    ## [1307] {rolls/buns,                                                                                               
    ##         shopping bags}            => {sausage}                  0.005998983  0.3072917 0.019522115 3.2707939    59
    ## [1308] {rolls/buns,                                                                                               
    ##         sausage}                  => {shopping bags}            0.005998983  0.1960133 0.030604982 1.9894641    59
    ## [1309] {sausage,                                                                                                  
    ##         shopping bags}            => {other vegetables}         0.005388917  0.3441558 0.015658363 1.7786509    53
    ## [1310] {other vegetables,                                                                                         
    ##         shopping bags}            => {sausage}                  0.005388917  0.2324561 0.023182511 2.4742491    53
    ## [1311] {other vegetables,                                                                                         
    ##         sausage}                  => {shopping bags}            0.005388917  0.2000000 0.026944586 2.0299278    53
    ## [1312] {root vegetables,                                                                                          
    ##         shopping bags}            => {other vegetables}         0.006609049  0.5158730 0.012811388 2.6661120    65
    ## [1313] {other vegetables,                                                                                         
    ##         shopping bags}            => {root vegetables}          0.006609049  0.2850877 0.023182511 2.6155203    65
    ## [1314] {other vegetables,                                                                                         
    ##         root vegetables}          => {shopping bags}            0.006609049  0.1394850 0.047381800 1.4157222    65
    ## [1315] {root vegetables,                                                                                          
    ##         shopping bags}            => {whole milk}               0.005287239  0.4126984 0.012811388 1.6151567    52
    ## [1316] {shopping bags,                                                                                            
    ##         whole milk}               => {root vegetables}          0.005287239  0.2157676 0.024504321 1.9795473    52
    ## [1317] {root vegetables,                                                                                          
    ##         whole milk}               => {shopping bags}            0.005287239  0.1081081 0.048906965 1.0972582    52
    ## [1318] {shopping bags,                                                                                            
    ##         soda}                     => {rolls/buns}               0.006304016  0.2561983 0.024605999 1.3928749    62
    ## [1319] {rolls/buns,                                                                                               
    ##         shopping bags}            => {soda}                     0.006304016  0.3229167 0.019522115 1.8518282    62
    ## [1320] {rolls/buns,                                                                                               
    ##         soda}                     => {shopping bags}            0.006304016  0.1644562 0.038332486 1.6691714    62
    ## [1321] {shopping bags,                                                                                            
    ##         soda}                     => {other vegetables}         0.005388917  0.2190083 0.024605999 1.1318688    53
    ## [1322] {other vegetables,                                                                                         
    ##         shopping bags}            => {soda}                     0.005388917  0.2324561 0.023182511 1.3330648    53
    ## [1323] {other vegetables,                                                                                         
    ##         soda}                     => {shopping bags}            0.005388917  0.1645963 0.032740214 1.6705927    53
    ## [1324] {shopping bags,                                                                                            
    ##         soda}                     => {whole milk}               0.006812405  0.2768595 0.024605999 1.0835309    67
    ## [1325] {shopping bags,                                                                                            
    ##         whole milk}               => {soda}                     0.006812405  0.2780083 0.024504321 1.5942925    67
    ## [1326] {soda,                                                                                                     
    ##         whole milk}               => {shopping bags}            0.006812405  0.1700508 0.040061007 1.7259538    67
    ## [1327] {shopping bags,                                                                                            
    ##         yogurt}                   => {other vegetables}         0.005388917  0.3533333 0.015251652 1.8260816    53
    ## [1328] {other vegetables,                                                                                         
    ##         shopping bags}            => {yogurt}                   0.005388917  0.2324561 0.023182511 1.6663310    53
    ## [1329] {other vegetables,                                                                                         
    ##         yogurt}                   => {shopping bags}            0.005388917  0.1241218 0.043416370 1.2597912    53
    ## [1330] {shopping bags,                                                                                            
    ##         yogurt}                   => {whole milk}               0.005287239  0.3466667 0.015251652 1.3567317    52
    ## [1331] {shopping bags,                                                                                            
    ##         whole milk}               => {yogurt}                   0.005287239  0.2157676 0.024504321 1.5467017    52
    ## [1332] {rolls/buns,                                                                                               
    ##         shopping bags}            => {other vegetables}         0.005287239  0.2708333 0.019522115 1.3997088    52
    ## [1333] {other vegetables,                                                                                         
    ##         shopping bags}            => {rolls/buns}               0.005287239  0.2280702 0.023182511 1.2399503    52
    ## [1334] {other vegetables,                                                                                         
    ##         rolls/buns}               => {shopping bags}            0.005287239  0.1241050 0.042602949 1.2596210    52
    ## [1335] {rolls/buns,                                                                                               
    ##         shopping bags}            => {whole milk}               0.005287239  0.2708333 0.019522115 1.0599466    52
    ## [1336] {shopping bags,                                                                                            
    ##         whole milk}               => {rolls/buns}               0.005287239  0.2157676 0.024504321 1.1730651    52
    ## [1337] {other vegetables,                                                                                         
    ##         shopping bags}            => {whole milk}               0.007625826  0.3289474 0.023182511 1.2873845    75
    ## [1338] {shopping bags,                                                                                            
    ##         whole milk}               => {other vegetables}         0.007625826  0.3112033 0.024504321 1.6083472    75
    ## [1339] {other vegetables,                                                                                         
    ##         whole milk}               => {shopping bags}            0.007625826  0.1019022 0.074834774 1.0342703    75
    ## [1340] {bottled water,                                                                                            
    ##         sausage}                  => {other vegetables}         0.005083884  0.4237288 0.011997966 2.1898964    50
    ## [1341] {other vegetables,                                                                                         
    ##         sausage}                  => {bottled water}            0.005083884  0.1886792 0.026944586 1.7071393    50
    ## [1342] {bottled water,                                                                                            
    ##         other vegetables}         => {sausage}                  0.005083884  0.2049180 0.024809354 2.1811351    50
    ## [1343] {sausage,                                                                                                  
    ##         tropical fruit}           => {other vegetables}         0.005998983  0.4306569 0.013929842 2.2257020    59
    ## [1344] {other vegetables,                                                                                         
    ##         sausage}                  => {tropical fruit}           0.005998983  0.2226415 0.026944586 2.1217822    59
    ## [1345] {other vegetables,                                                                                         
    ##         tropical fruit}           => {sausage}                  0.005998983  0.1671388 0.035892222 1.7790154    59
    ## [1346] {sausage,                                                                                                  
    ##         tropical fruit}           => {whole milk}               0.007219115  0.5182482 0.013929842 2.0282415    71
    ## [1347] {sausage,                                                                                                  
    ##         whole milk}               => {tropical fruit}           0.007219115  0.2414966 0.029893238 2.3014719    71
    ## [1348] {tropical fruit,                                                                                           
    ##         whole milk}               => {sausage}                  0.007219115  0.1706731 0.042297916 1.8166339    71
    ## [1349] {root vegetables,                                                                                          
    ##         sausage}                  => {yogurt}                   0.005185562  0.3469388 0.014946619 2.4869846    51
    ## [1350] {sausage,                                                                                                  
    ##         yogurt}                   => {root vegetables}          0.005185562  0.2642487 0.019623793 2.4243340    51
    ## [1351] {root vegetables,                                                                                          
    ##         yogurt}                   => {sausage}                  0.005185562  0.2007874 0.025826131 2.1371689    51
    ## [1352] {root vegetables,                                                                                          
    ##         sausage}                  => {other vegetables}         0.006812405  0.4557823 0.014946619 2.3555539    67
    ## [1353] {other vegetables,                                                                                         
    ##         sausage}                  => {root vegetables}          0.006812405  0.2528302 0.026944586 2.3195755    67
    ## [1354] {other vegetables,                                                                                         
    ##         root vegetables}          => {sausage}                  0.006812405  0.1437768 0.047381800 1.5303518    67
    ## [1355] {root vegetables,                                                                                          
    ##         sausage}                  => {whole milk}               0.007727504  0.5170068 0.014946619 2.0233832    76
    ## [1356] {sausage,                                                                                                  
    ##         whole milk}               => {root vegetables}          0.007727504  0.2585034 0.029893238 2.3716240    76
    ## [1357] {root vegetables,                                                                                          
    ##         whole milk}               => {sausage}                  0.007727504  0.1580042 0.048906965 1.6817867    76
    ## [1358] {sausage,                                                                                                  
    ##         soda}                     => {yogurt}                   0.005592272  0.2301255 0.024300966 1.6496243    55
    ## [1359] {sausage,                                                                                                  
    ##         yogurt}                   => {soda}                     0.005592272  0.2849741 0.019623793 1.6342392    55
    ## [1360] {soda,                                                                                                     
    ##         yogurt}                   => {sausage}                  0.005592272  0.2044610 0.027351296 2.1762701    55
    ## [1361] {sausage,                                                                                                  
    ##         soda}                     => {rolls/buns}               0.009659380  0.3974895 0.024300966 2.1610335    95
    ## [1362] {rolls/buns,                                                                                               
    ##         sausage}                  => {soda}                     0.009659380  0.3156146 0.030604982 1.8099532    95
    ## [1363] {rolls/buns,                                                                                               
    ##         soda}                     => {sausage}                  0.009659380  0.2519894 0.038332486 2.6821598    95
    ## [1364] {sausage,                                                                                                  
    ##         soda}                     => {other vegetables}         0.007219115  0.2970711 0.024300966 1.5353098    71
    ## [1365] {other vegetables,                                                                                         
    ##         sausage}                  => {soda}                     0.007219115  0.2679245 0.026944586 1.5364652    71
    ## [1366] {other vegetables,                                                                                         
    ##         soda}                     => {sausage}                  0.007219115  0.2204969 0.032740214 2.3469556    71
    ## [1367] {sausage,                                                                                                  
    ##         soda}                     => {whole milk}               0.006710727  0.2761506 0.024300966 1.0807566    66
    ## [1368] {sausage,                                                                                                  
    ##         whole milk}               => {soda}                     0.006710727  0.2244898 0.029893238 1.2873803    66
    ## [1369] {soda,                                                                                                     
    ##         whole milk}               => {sausage}                  0.006710727  0.1675127 0.040061007 1.7829949    66
    ## [1370] {sausage,                                                                                                  
    ##         yogurt}                   => {rolls/buns}               0.005998983  0.3056995 0.019623793 1.6619980    59
    ## [1371] {rolls/buns,                                                                                               
    ##         sausage}                  => {yogurt}                   0.005998983  0.1960133 0.030604982 1.4050953    59
    ## [1372] {rolls/buns,                                                                                               
    ##         yogurt}                   => {sausage}                  0.005998983  0.1745562 0.034367056 1.8579658    59
    ## [1373] {sausage,                                                                                                  
    ##         yogurt}                   => {other vegetables}         0.008134215  0.4145078 0.019623793 2.1422406    80
    ## [1374] {other vegetables,                                                                                         
    ##         sausage}                  => {yogurt}                   0.008134215  0.3018868 0.026944586 2.1640354    80
    ## [1375] {other vegetables,                                                                                         
    ##         yogurt}                   => {sausage}                  0.008134215  0.1873536 0.043416370 1.9941807    80
    ## [1376] {sausage,                                                                                                  
    ##         yogurt}                   => {whole milk}               0.008744281  0.4455959 0.019623793 1.7439058    86
    ## [1377] {sausage,                                                                                                  
    ##         whole milk}               => {yogurt}                   0.008744281  0.2925170 0.029893238 2.0968694    86
    ## [1378] {whole milk,                                                                                               
    ##         yogurt}                   => {sausage}                  0.008744281  0.1560799 0.056024403 1.6613045    86
    ## [1379] {rolls/buns,                                                                                               
    ##         sausage}                  => {other vegetables}         0.008845958  0.2890365 0.030604982 1.4937858    87
    ## [1380] {other vegetables,                                                                                         
    ##         sausage}                  => {rolls/buns}               0.008845958  0.3283019 0.026944586 1.7848806    87
    ## [1381] {other vegetables,                                                                                         
    ##         rolls/buns}               => {sausage}                  0.008845958  0.2076372 0.042602949 2.2100781    87
    ## [1382] {rolls/buns,                                                                                               
    ##         sausage}                  => {whole milk}               0.009354347  0.3056478 0.030604982 1.1961984    92
    ## [1383] {sausage,                                                                                                  
    ##         whole milk}               => {rolls/buns}               0.009354347  0.3129252 0.029893238 1.7012820    92
    ## [1384] {rolls/buns,                                                                                               
    ##         whole milk}               => {sausage}                  0.009354347  0.1651706 0.056634469 1.7580654    92
    ## [1385] {other vegetables,                                                                                         
    ##         sausage}                  => {whole milk}               0.010167768  0.3773585 0.026944586 1.4768487   100
    ## [1386] {sausage,                                                                                                  
    ##         whole milk}               => {other vegetables}         0.010167768  0.3401361 0.029893238 1.7578760   100
    ## [1387] {other vegetables,                                                                                         
    ##         whole milk}               => {sausage}                  0.010167768  0.1358696 0.074834774 1.4461874   100
    ## [1388] {bottled water,                                                                                            
    ##         tropical fruit}           => {soda}                     0.005185562  0.2802198 0.018505338 1.6069747    51
    ## [1389] {bottled water,                                                                                            
    ##         soda}                     => {tropical fruit}           0.005185562  0.1789474 0.028978139 1.7053754    51
    ## [1390] {soda,                                                                                                     
    ##         tropical fruit}           => {bottled water}            0.005185562  0.2487805 0.020843925 2.2509256    51
    ## [1391] {bottled water,                                                                                            
    ##         tropical fruit}           => {yogurt}                   0.007117438  0.3846154 0.018505338 2.7570644    70
    ## [1392] {bottled water,                                                                                            
    ##         yogurt}                   => {tropical fruit}           0.007117438  0.3097345 0.022979156 2.9517819    70
    ## [1393] {tropical fruit,                                                                                           
    ##         yogurt}                   => {bottled water}            0.007117438  0.2430556 0.029283172 2.1991273    70
    ## [1394] {bottled water,                                                                                            
    ##         tropical fruit}           => {rolls/buns}               0.005388917  0.2912088 0.018505338 1.5832164    53
    ## [1395] {bottled water,                                                                                            
    ##         rolls/buns}               => {tropical fruit}           0.005388917  0.2226891 0.024199288 2.1222355    53
    ## [1396] {rolls/buns,                                                                                               
    ##         tropical fruit}           => {bottled water}            0.005388917  0.2190083 0.024605999 1.9815513    53
    ## [1397] {bottled water,                                                                                            
    ##         tropical fruit}           => {other vegetables}         0.006202339  0.3351648 0.018505338 1.7321840    61
    ## [1398] {bottled water,                                                                                            
    ##         other vegetables}         => {tropical fruit}           0.006202339  0.2500000 0.024809354 2.3825097    61
    ## [1399] {other vegetables,                                                                                         
    ##         tropical fruit}           => {bottled water}            0.006202339  0.1728045 0.035892222 1.5635074    61
    ## [1400] {bottled water,                                                                                            
    ##         tropical fruit}           => {whole milk}               0.008032537  0.4340659 0.018505338 1.6987817    79
    ## [1401] {bottled water,                                                                                            
    ##         whole milk}               => {tropical fruit}           0.008032537  0.2337278 0.034367056 2.2274351    79
    ## [1402] {tropical fruit,                                                                                           
    ##         whole milk}               => {bottled water}            0.008032537  0.1899038 0.042297916 1.7182193    79
    ## [1403] {bottled water,                                                                                            
    ##         root vegetables}          => {other vegetables}         0.007015760  0.4480519 0.015658363 2.3156022    69
    ## [1404] {bottled water,                                                                                            
    ##         other vegetables}         => {root vegetables}          0.007015760  0.2827869 0.024809354 2.5944114    69
    ## [1405] {other vegetables,                                                                                         
    ##         root vegetables}          => {bottled water}            0.007015760  0.1480687 0.047381800 1.3397013    69
    ## [1406] {bottled water,                                                                                            
    ##         root vegetables}          => {whole milk}               0.007320793  0.4675325 0.015658363 1.8297580    72
    ## [1407] {bottled water,                                                                                            
    ##         whole milk}               => {root vegetables}          0.007320793  0.2130178 0.034367056 1.9543186    72
    ## [1408] {root vegetables,                                                                                          
    ##         whole milk}               => {bottled water}            0.007320793  0.1496881 0.048906965 1.3543541    72
    ## [1409] {bottled water,                                                                                            
    ##         soda}                     => {yogurt}                   0.007422471  0.2561404 0.028978139 1.8361081    73
    ## [1410] {bottled water,                                                                                            
    ##         yogurt}                   => {soda}                     0.007422471  0.3230088 0.022979156 1.8523569    73
    ## [1411] {soda,                                                                                                     
    ##         yogurt}                   => {bottled water}            0.007422471  0.2713755 0.027351296 2.4553613    73
    ## [1412] {bottled water,                                                                                            
    ##         soda}                     => {rolls/buns}               0.006812405  0.2350877 0.028978139 1.2781027    67
    ## [1413] {bottled water,                                                                                            
    ##         rolls/buns}               => {soda}                     0.006812405  0.2815126 0.024199288 1.6143886    67
    ## [1414] {rolls/buns,                                                                                               
    ##         soda}                     => {bottled water}            0.006812405  0.1777188 0.038332486 1.6079712    67
    ## [1415] {bottled water,                                                                                            
    ##         soda}                     => {other vegetables}         0.005693950  0.1964912 0.028978139 1.0154972    56
    ## [1416] {bottled water,                                                                                            
    ##         other vegetables}         => {soda}                     0.005693950  0.2295082 0.024809354 1.3161593    56
    ## [1417] {other vegetables,                                                                                         
    ##         soda}                     => {bottled water}            0.005693950  0.1739130 0.032740214 1.5735371    56
    ## [1418] {bottled water,                                                                                            
    ##         soda}                     => {whole milk}               0.007524148  0.2596491 0.028978139 1.0161755    74
    ## [1419] {bottled water,                                                                                            
    ##         whole milk}               => {soda}                     0.007524148  0.2189349 0.034367056 1.2555247    74
    ## [1420] {soda,                                                                                                     
    ##         whole milk}               => {bottled water}            0.007524148  0.1878173 0.040061007 1.6993401    74
    ## [1421] {bottled water,                                                                                            
    ##         yogurt}                   => {rolls/buns}               0.007117438  0.3097345 0.022979156 1.6839353    70
    ## [1422] {bottled water,                                                                                            
    ##         rolls/buns}               => {yogurt}                   0.007117438  0.2941176 0.024199288 2.1083433    70
    ## [1423] {rolls/buns,                                                                                               
    ##         yogurt}                   => {bottled water}            0.007117438  0.2071006 0.034367056 1.8738126    70
    ## [1424] {bottled water,                                                                                            
    ##         yogurt}                   => {other vegetables}         0.008134215  0.3539823 0.022979156 1.8294356    80
    ## [1425] {bottled water,                                                                                            
    ##         other vegetables}         => {yogurt}                   0.008134215  0.3278689 0.024809354 2.3502844    80
    ## [1426] {other vegetables,                                                                                         
    ##         yogurt}                   => {bottled water}            0.008134215  0.1873536 0.043416370 1.6951453    80
    ## [1427] {bottled water,                                                                                            
    ##         yogurt}                   => {whole milk}               0.009659380  0.4203540 0.022979156 1.6451180    95
    ## [1428] {bottled water,                                                                                            
    ##         whole milk}               => {yogurt}                   0.009659380  0.2810651 0.034367056 2.0147778    95
    ## [1429] {whole milk,                                                                                               
    ##         yogurt}                   => {bottled water}            0.009659380  0.1724138 0.056024403 1.5599721    95
    ## [1430] {bottled water,                                                                                            
    ##         rolls/buns}               => {other vegetables}         0.007320793  0.3025210 0.024199288 1.5634756    72
    ## [1431] {bottled water,                                                                                            
    ##         other vegetables}         => {rolls/buns}               0.007320793  0.2950820 0.024809354 1.6042737    72
    ## [1432] {other vegetables,                                                                                         
    ##         rolls/buns}               => {bottled water}            0.007320793  0.1718377 0.042602949 1.5547598    72
    ## [1433] {bottled water,                                                                                            
    ##         rolls/buns}               => {whole milk}               0.008744281  0.3613445 0.024199288 1.4141757    86
    ## [1434] {bottled water,                                                                                            
    ##         whole milk}               => {rolls/buns}               0.008744281  0.2544379 0.034367056 1.3833037    86
    ## [1435] {rolls/buns,                                                                                               
    ##         whole milk}               => {bottled water}            0.008744281  0.1543986 0.056634469 1.3969732    86
    ## [1436] {bottled water,                                                                                            
    ##         other vegetables}         => {whole milk}               0.010777834  0.4344262 0.024809354 1.7001918   106
    ## [1437] {bottled water,                                                                                            
    ##         whole milk}               => {other vegetables}         0.010777834  0.3136095 0.034367056 1.6207825   106
    ## [1438] {other vegetables,                                                                                         
    ##         whole milk}               => {bottled water}            0.010777834  0.1440217 0.074834774 1.3030854   106
    ## [1439] {root vegetables,                                                                                          
    ##         tropical fruit}           => {yogurt}                   0.008134215  0.3864734 0.021047280 2.7703835    80
    ## [1440] {tropical fruit,                                                                                           
    ##         yogurt}                   => {root vegetables}          0.008134215  0.2777778 0.029283172 2.5484556    80
    ## [1441] {root vegetables,                                                                                          
    ##         yogurt}                   => {tropical fruit}           0.008134215  0.3149606 0.025826131 3.0015870    80
    ## [1442] {root vegetables,                                                                                          
    ##         tropical fruit}           => {rolls/buns}               0.005897306  0.2801932 0.021047280 1.5233281    58
    ## [1443] {rolls/buns,                                                                                               
    ##         tropical fruit}           => {root vegetables}          0.005897306  0.2396694 0.024605999 2.1988328    58
    ## [1444] {rolls/buns,                                                                                               
    ##         root vegetables}          => {tropical fruit}           0.005897306  0.2426778 0.024300966 2.3127291    58
    ## [1445] {root vegetables,                                                                                          
    ##         tropical fruit}           => {other vegetables}         0.012302999  0.5845411 0.021047280 3.0209991   121
    ## [1446] {other vegetables,                                                                                         
    ##         tropical fruit}           => {root vegetables}          0.012302999  0.3427762 0.035892222 3.1447798   121
    ## [1447] {other vegetables,                                                                                         
    ##         root vegetables}          => {tropical fruit}           0.012302999  0.2596567 0.047381800 2.4745380   121
    ## [1448] {root vegetables,                                                                                          
    ##         tropical fruit}           => {whole milk}               0.011997966  0.5700483 0.021047280 2.2309690   118
    ## [1449] {tropical fruit,                                                                                           
    ##         whole milk}               => {root vegetables}          0.011997966  0.2836538 0.042297916 2.6023653   118
    ## [1450] {root vegetables,                                                                                          
    ##         whole milk}               => {tropical fruit}           0.011997966  0.2453222 0.048906965 2.3379305   118
    ## [1451] {soda,                                                                                                     
    ##         tropical fruit}           => {yogurt}                   0.006609049  0.3170732 0.020843925 2.2728970    65
    ## [1452] {tropical fruit,                                                                                           
    ##         yogurt}                   => {soda}                     0.006609049  0.2256944 0.029283172 1.2942885    65
    ## [1453] {soda,                                                                                                     
    ##         yogurt}                   => {tropical fruit}           0.006609049  0.2416357 0.027351296 2.3027975    65
    ## [1454] {soda,                                                                                                     
    ##         tropical fruit}           => {rolls/buns}               0.005388917  0.2585366 0.020843925 1.4055872    53
    ## [1455] {rolls/buns,                                                                                               
    ##         tropical fruit}           => {soda}                     0.005388917  0.2190083 0.024605999 1.2559454    53
    ## [1456] {rolls/buns,                                                                                               
    ##         soda}                     => {tropical fruit}           0.005388917  0.1405836 0.038332486 1.3397667    53
    ## [1457] {soda,                                                                                                     
    ##         tropical fruit}           => {other vegetables}         0.007219115  0.3463415 0.020843925 1.7899466    71
    ## [1458] {other vegetables,                                                                                         
    ##         tropical fruit}           => {soda}                     0.007219115  0.2011331 0.035892222 1.1534370    71
    ## [1459] {other vegetables,                                                                                         
    ##         soda}                     => {tropical fruit}           0.007219115  0.2204969 0.032740214 2.1013440    71
    ## [1460] {soda,                                                                                                     
    ##         tropical fruit}           => {whole milk}               0.007829181  0.3756098 0.020843925 1.4700048    77
    ## [1461] {tropical fruit,                                                                                           
    ##         whole milk}               => {soda}                     0.007829181  0.1850962 0.042297916 1.0614698    77
    ## [1462] {soda,                                                                                                     
    ##         whole milk}               => {tropical fruit}           0.007829181  0.1954315 0.040061007 1.8624695    77
    ## [1463] {tropical fruit,                                                                                           
    ##         yogurt}                   => {rolls/buns}               0.008744281  0.2986111 0.029283172 1.6234606    86
    ## [1464] {rolls/buns,                                                                                               
    ##         tropical fruit}           => {yogurt}                   0.008744281  0.3553719 0.024605999 2.5474363    86
    ## [1465] {rolls/buns,                                                                                               
    ##         yogurt}                   => {tropical fruit}           0.008744281  0.2544379 0.034367056 2.4248028    86
    ## [1466] {tropical fruit,                                                                                           
    ##         yogurt}                   => {other vegetables}         0.012302999  0.4201389 0.029283172 2.1713431   121
    ## [1467] {other vegetables,                                                                                         
    ##         tropical fruit}           => {yogurt}                   0.012302999  0.3427762 0.035892222 2.4571457   121
    ## [1468] {other vegetables,                                                                                         
    ##         yogurt}                   => {tropical fruit}           0.012302999  0.2833724 0.043416370 2.7005496   121
    ## [1469] {tropical fruit,                                                                                           
    ##         yogurt}                   => {whole milk}               0.015149975  0.5173611 0.029283172 2.0247698   149
    ## [1470] {tropical fruit,                                                                                           
    ##         whole milk}               => {yogurt}                   0.015149975  0.3581731 0.042297916 2.5675162   149
    ## [1471] {whole milk,                                                                                               
    ##         yogurt}                   => {tropical fruit}           0.015149975  0.2704174 0.056024403 2.5770885   149
    ## [1472] {rolls/buns,                                                                                               
    ##         tropical fruit}           => {other vegetables}         0.007829181  0.3181818 0.024605999 1.6444131    77
    ## [1473] {other vegetables,                                                                                         
    ##         tropical fruit}           => {rolls/buns}               0.007829181  0.2181303 0.035892222 1.1859102    77
    ## [1474] {other vegetables,                                                                                         
    ##         rolls/buns}               => {tropical fruit}           0.007829181  0.1837709 0.042602949 1.7513436    77
    ## [1475] {rolls/buns,                                                                                               
    ##         tropical fruit}           => {whole milk}               0.010981190  0.4462810 0.024605999 1.7465872   108
    ## [1476] {tropical fruit,                                                                                           
    ##         whole milk}               => {rolls/buns}               0.010981190  0.2596154 0.042297916 1.4114524   108
    ## [1477] {rolls/buns,                                                                                               
    ##         whole milk}               => {tropical fruit}           0.010981190  0.1938959 0.056634469 1.8478352   108
    ## [1478] {other vegetables,                                                                                         
    ##         tropical fruit}           => {whole milk}               0.017081851  0.4759207 0.035892222 1.8625865   168
    ## [1479] {tropical fruit,                                                                                           
    ##         whole milk}               => {other vegetables}         0.017081851  0.4038462 0.042297916 2.0871397   168
    ## [1480] {other vegetables,                                                                                         
    ##         whole milk}               => {tropical fruit}           0.017081851  0.2282609 0.074834774 2.1753349   168
    ## [1481] {root vegetables,                                                                                          
    ##         soda}                     => {other vegetables}         0.008235892  0.4426230 0.018607016 2.2875443    81
    ## [1482] {other vegetables,                                                                                         
    ##         root vegetables}          => {soda}                     0.008235892  0.1738197 0.047381800 0.9968030    81
    ## [1483] {other vegetables,                                                                                         
    ##         soda}                     => {root vegetables}          0.008235892  0.2515528 0.032740214 2.3078561    81
    ## [1484] {root vegetables,                                                                                          
    ##         soda}                     => {whole milk}               0.008134215  0.4371585 0.018607016 1.7108848    80
    ## [1485] {root vegetables,                                                                                          
    ##         whole milk}               => {soda}                     0.008134215  0.1663202 0.048906965 0.9537952    80
    ## [1486] {soda,                                                                                                     
    ##         whole milk}               => {root vegetables}          0.008134215  0.2030457 0.040061007 1.8628305    80
    ## [1487] {root vegetables,                                                                                          
    ##         yogurt}                   => {rolls/buns}               0.007219115  0.2795276 0.025826131 1.5197090    71
    ## [1488] {rolls/buns,                                                                                               
    ##         root vegetables}          => {yogurt}                   0.007219115  0.2970711 0.024300966 2.1295150    71
    ## [1489] {rolls/buns,                                                                                               
    ##         yogurt}                   => {root vegetables}          0.007219115  0.2100592 0.034367056 1.9271753    71
    ## [1490] {root vegetables,                                                                                          
    ##         yogurt}                   => {other vegetables}         0.012913066  0.5000000 0.025826131 2.5840778   127
    ## [1491] {other vegetables,                                                                                         
    ##         root vegetables}          => {yogurt}                   0.012913066  0.2725322 0.047381800 1.9536108   127
    ## [1492] {other vegetables,                                                                                         
    ##         yogurt}                   => {root vegetables}          0.012913066  0.2974239 0.043416370 2.7286977   127
    ## [1493] {root vegetables,                                                                                          
    ##         yogurt}                   => {whole milk}               0.014539908  0.5629921 0.025826131 2.2033536   143
    ## [1494] {root vegetables,                                                                                          
    ##         whole milk}               => {yogurt}                   0.014539908  0.2972973 0.048906965 2.1311362   143
    ## [1495] {whole milk,                                                                                               
    ##         yogurt}                   => {root vegetables}          0.014539908  0.2595281 0.056024403 2.3810253   143
    ## [1496] {rolls/buns,                                                                                               
    ##         root vegetables}          => {other vegetables}         0.012201322  0.5020921 0.024300966 2.5948898   120
    ## [1497] {other vegetables,                                                                                         
    ##         root vegetables}          => {rolls/buns}               0.012201322  0.2575107 0.047381800 1.4000100   120
    ## [1498] {other vegetables,                                                                                         
    ##         rolls/buns}               => {root vegetables}          0.012201322  0.2863962 0.042602949 2.6275247   120
    ## [1499] {rolls/buns,                                                                                               
    ##         root vegetables}          => {whole milk}               0.012709710  0.5230126 0.024300966 2.0468876   125
    ## [1500] {root vegetables,                                                                                          
    ##         whole milk}               => {rolls/buns}               0.012709710  0.2598753 0.048906965 1.4128652   125
    ## [1501] {rolls/buns,                                                                                               
    ##         whole milk}               => {root vegetables}          0.012709710  0.2244165 0.056634469 2.0588959   125
    ## [1502] {other vegetables,                                                                                         
    ##         root vegetables}          => {whole milk}               0.023182511  0.4892704 0.047381800 1.9148326   228
    ## [1503] {root vegetables,                                                                                          
    ##         whole milk}               => {other vegetables}         0.023182511  0.4740125 0.048906965 2.4497702   228
    ## [1504] {other vegetables,                                                                                         
    ##         whole milk}               => {root vegetables}          0.023182511  0.3097826 0.074834774 2.8420820   228
    ## [1505] {soda,                                                                                                     
    ##         yogurt}                   => {rolls/buns}               0.008642603  0.3159851 0.027351296 1.7179181    85
    ## [1506] {rolls/buns,                                                                                               
    ##         soda}                     => {yogurt}                   0.008642603  0.2254642 0.038332486 1.6162101    85
    ## [1507] {rolls/buns,                                                                                               
    ##         yogurt}                   => {soda}                     0.008642603  0.2514793 0.034367056 1.4421567    85
    ## [1508] {soda,                                                                                                     
    ##         yogurt}                   => {other vegetables}         0.008337570  0.3048327 0.027351296 1.5754229    82
    ## [1509] {other vegetables,                                                                                         
    ##         soda}                     => {yogurt}                   0.008337570  0.2546584 0.032740214 1.8254849    82
    ## [1510] {other vegetables,                                                                                         
    ##         yogurt}                   => {soda}                     0.008337570  0.1920375 0.043416370 1.1012761    82
    ## [1511] {soda,                                                                                                     
    ##         yogurt}                   => {whole milk}               0.010472801  0.3828996 0.027351296 1.4985348   103
    ## [1512] {soda,                                                                                                     
    ##         whole milk}               => {yogurt}                   0.010472801  0.2614213 0.040061007 1.8739641   103
    ## [1513] {whole milk,                                                                                               
    ##         yogurt}                   => {soda}                     0.010472801  0.1869328 0.056024403 1.0720027   103
    ## [1514] {rolls/buns,                                                                                               
    ##         soda}                     => {other vegetables}         0.009862735  0.2572944 0.038332486 1.3297376    97
    ## [1515] {other vegetables,                                                                                         
    ##         soda}                     => {rolls/buns}               0.009862735  0.3012422 0.032740214 1.6377653    97
    ## [1516] {other vegetables,                                                                                         
    ##         rolls/buns}               => {soda}                     0.009862735  0.2315036 0.042602949 1.3276022    97
    ## [1517] {rolls/buns,                                                                                               
    ##         soda}                     => {whole milk}               0.008845958  0.2307692 0.038332486 0.9031498    87
    ## [1518] {soda,                                                                                                     
    ##         whole milk}               => {rolls/buns}               0.008845958  0.2208122 0.040061007 1.2004908    87
    ## [1519] {rolls/buns,                                                                                               
    ##         whole milk}               => {soda}                     0.008845958  0.1561939 0.056634469 0.8957242    87
    ## [1520] {other vegetables,                                                                                         
    ##         soda}                     => {whole milk}               0.013929842  0.4254658 0.032740214 1.6651240   137
    ## [1521] {soda,                                                                                                     
    ##         whole milk}               => {other vegetables}         0.013929842  0.3477157 0.040061007 1.7970490   137
    ## [1522] {other vegetables,                                                                                         
    ##         whole milk}               => {soda}                     0.013929842  0.1861413 0.074834774 1.0674634   137
    ## [1523] {rolls/buns,                                                                                               
    ##         yogurt}                   => {other vegetables}         0.011489578  0.3343195 0.034367056 1.7278153   113
    ## [1524] {other vegetables,                                                                                         
    ##         yogurt}                   => {rolls/buns}               0.011489578  0.2646370 0.043416370 1.4387534   113
    ## [1525] {other vegetables,                                                                                         
    ##         rolls/buns}               => {yogurt}                   0.011489578  0.2696897 0.042602949 1.9332351   113
    ## [1526] {rolls/buns,                                                                                               
    ##         yogurt}                   => {whole milk}               0.015556685  0.4526627 0.034367056 1.7715630   153
    ## [1527] {whole milk,                                                                                               
    ##         yogurt}                   => {rolls/buns}               0.015556685  0.2776770 0.056024403 1.5096478   153
    ## [1528] {rolls/buns,                                                                                               
    ##         whole milk}               => {yogurt}                   0.015556685  0.2746858 0.056634469 1.9690488   153
    ## [1529] {other vegetables,                                                                                         
    ##         yogurt}                   => {whole milk}               0.022267412  0.5128806 0.043416370 2.0072345   219
    ## [1530] {whole milk,                                                                                               
    ##         yogurt}                   => {other vegetables}         0.022267412  0.3974592 0.056024403 2.0541308   219
    ## [1531] {other vegetables,                                                                                         
    ##         whole milk}               => {yogurt}                   0.022267412  0.2975543 0.074834774 2.1329789   219
    ## [1532] {other vegetables,                                                                                         
    ##         rolls/buns}               => {whole milk}               0.017895272  0.4200477 0.042602949 1.6439194   176
    ## [1533] {rolls/buns,                                                                                               
    ##         whole milk}               => {other vegetables}         0.017895272  0.3159785 0.056634469 1.6330258   176
    ## [1534] {other vegetables,                                                                                         
    ##         whole milk}               => {rolls/buns}               0.017895272  0.2391304 0.074834774 1.3000817   176
    ## [1535] {fruit/vegetable juice,                                                                                    
    ##         other vegetables,                                                                                         
    ##         yogurt}                   => {whole milk}               0.005083884  0.6172840 0.008235892 2.4158327    50
    ## [1536] {fruit/vegetable juice,                                                                                    
    ##         whole milk,                                                                                               
    ##         yogurt}                   => {other vegetables}         0.005083884  0.5376344 0.009456024 2.7785782    50
    ## [1537] {fruit/vegetable juice,                                                                                    
    ##         other vegetables,                                                                                         
    ##         whole milk}               => {yogurt}                   0.005083884  0.4854369 0.010472801 3.4797900    50
    ## [1538] {other vegetables,                                                                                         
    ##         whole milk,                                                                                               
    ##         yogurt}                   => {fruit/vegetable juice}    0.005083884  0.2283105 0.022267412 3.1581347    50
    ## [1539] {other vegetables,                                                                                         
    ##         root vegetables,                                                                                          
    ##         whipped/sour cream}       => {whole milk}               0.005185562  0.6071429 0.008540925 2.3761441    51
    ## [1540] {root vegetables,                                                                                          
    ##         whipped/sour cream,                                                                                       
    ##         whole milk}               => {other vegetables}         0.005185562  0.5483871 0.009456024 2.8341498    51
    ## [1541] {other vegetables,                                                                                         
    ##         whipped/sour cream,                                                                                       
    ##         whole milk}               => {root vegetables}          0.005185562  0.3541667 0.014641586 3.2492809    51
    ## [1542] {other vegetables,                                                                                         
    ##         root vegetables,                                                                                          
    ##         whole milk}               => {whipped/sour cream}       0.005185562  0.2236842 0.023182511 3.1204741    51
    ## [1543] {other vegetables,                                                                                         
    ##         whipped/sour cream,                                                                                       
    ##         yogurt}                   => {whole milk}               0.005592272  0.5500000 0.010167768 2.1525070    55
    ## [1544] {whipped/sour cream,                                                                                       
    ##         whole milk,                                                                                               
    ##         yogurt}                   => {other vegetables}         0.005592272  0.5140187 0.010879512 2.6565286    55
    ## [1545] {other vegetables,                                                                                         
    ##         whipped/sour cream,                                                                                       
    ##         whole milk}               => {yogurt}                   0.005592272  0.3819444 0.014641586 2.7379181    55
    ## [1546] {other vegetables,                                                                                         
    ##         whole milk,                                                                                               
    ##         yogurt}                   => {whipped/sour cream}       0.005592272  0.2511416 0.022267412 3.5035137    55
    ## [1547] {other vegetables,                                                                                         
    ##         pip fruit,                                                                                                
    ##         root vegetables}          => {whole milk}               0.005490595  0.6750000 0.008134215 2.6417131    54
    ## [1548] {pip fruit,                                                                                                
    ##         root vegetables,                                                                                          
    ##         whole milk}               => {other vegetables}         0.005490595  0.6136364 0.008947636 3.1713682    54
    ## [1549] {other vegetables,                                                                                         
    ##         pip fruit,                                                                                                
    ##         whole milk}               => {root vegetables}          0.005490595  0.4060150 0.013523132 3.7249607    54
    ## [1550] {other vegetables,                                                                                         
    ##         root vegetables,                                                                                          
    ##         whole milk}               => {pip fruit}                0.005490595  0.2368421 0.023182511 3.1308362    54
    ## [1551] {other vegetables,                                                                                         
    ##         pip fruit,                                                                                                
    ##         yogurt}                   => {whole milk}               0.005083884  0.6250000 0.008134215 2.4460306    50
    ## [1552] {pip fruit,                                                                                                
    ##         whole milk,                                                                                               
    ##         yogurt}                   => {other vegetables}         0.005083884  0.5319149 0.009557702 2.7490189    50
    ## [1553] {other vegetables,                                                                                         
    ##         pip fruit,                                                                                                
    ##         whole milk}               => {yogurt}                   0.005083884  0.3759398 0.013523132 2.6948749    50
    ## [1554] {other vegetables,                                                                                         
    ##         whole milk,                                                                                               
    ##         yogurt}                   => {pip fruit}                0.005083884  0.2283105 0.022267412 3.0180562    50
    ## [1555] {citrus fruit,                                                                                             
    ##         other vegetables,                                                                                         
    ##         root vegetables}          => {whole milk}               0.005795628  0.5588235 0.010371124 2.1870392    57
    ## [1556] {citrus fruit,                                                                                             
    ##         root vegetables,                                                                                          
    ##         whole milk}               => {other vegetables}         0.005795628  0.6333333 0.009150991 3.2731652    57
    ## [1557] {citrus fruit,                                                                                             
    ##         other vegetables,                                                                                         
    ##         whole milk}               => {root vegetables}          0.005795628  0.4453125 0.013014743 4.0854929    57
    ## [1558] {other vegetables,                                                                                         
    ##         root vegetables,                                                                                          
    ##         whole milk}               => {citrus fruit}             0.005795628  0.2500000 0.023182511 3.0205774    57
    ## [1559] {root vegetables,                                                                                          
    ##         tropical fruit,                                                                                           
    ##         yogurt}                   => {whole milk}               0.005693950  0.7000000 0.008134215 2.7395543    56
    ## [1560] {root vegetables,                                                                                          
    ##         tropical fruit,                                                                                           
    ##         whole milk}               => {yogurt}                   0.005693950  0.4745763 0.011997966 3.4019370    56
    ## [1561] {tropical fruit,                                                                                           
    ##         whole milk,                                                                                               
    ##         yogurt}                   => {root vegetables}          0.005693950  0.3758389 0.015149975 3.4481118    56
    ## [1562] {root vegetables,                                                                                          
    ##         whole milk,                                                                                               
    ##         yogurt}                   => {tropical fruit}           0.005693950  0.3916084 0.014539908 3.7320432    56
    ## [1563] {other vegetables,                                                                                         
    ##         root vegetables,                                                                                          
    ##         tropical fruit}           => {whole milk}               0.007015760  0.5702479 0.012302999 2.2317503    69
    ## [1564] {root vegetables,                                                                                          
    ##         tropical fruit,                                                                                           
    ##         whole milk}               => {other vegetables}         0.007015760  0.5847458 0.011997966 3.0220571    69
    ## [1565] {other vegetables,                                                                                         
    ##         tropical fruit,                                                                                           
    ##         whole milk}               => {root vegetables}          0.007015760  0.4107143 0.017081851 3.7680737    69
    ## [1566] {other vegetables,                                                                                         
    ##         root vegetables,                                                                                          
    ##         whole milk}               => {tropical fruit}           0.007015760  0.3026316 0.023182511 2.8840907    69
    ## [1567] {other vegetables,                                                                                         
    ##         tropical fruit,                                                                                           
    ##         yogurt}                   => {whole milk}               0.007625826  0.6198347 0.012302999 2.4258155    75
    ## [1568] {tropical fruit,                                                                                           
    ##         whole milk,                                                                                               
    ##         yogurt}                   => {other vegetables}         0.007625826  0.5033557 0.015149975 2.6014206    75
    ## [1569] {other vegetables,                                                                                         
    ##         tropical fruit,                                                                                           
    ##         whole milk}               => {yogurt}                   0.007625826  0.4464286 0.017081851 3.2001640    75
    ## [1570] {other vegetables,                                                                                         
    ##         whole milk,                                                                                               
    ##         yogurt}                   => {tropical fruit}           0.007625826  0.3424658 0.022267412 3.2637119    75
    ## [1571] {other vegetables,                                                                                         
    ##         root vegetables,                                                                                          
    ##         yogurt}                   => {whole milk}               0.007829181  0.6062992 0.012913066 2.3728423    77
    ## [1572] {root vegetables,                                                                                          
    ##         whole milk,                                                                                               
    ##         yogurt}                   => {other vegetables}         0.007829181  0.5384615 0.014539908 2.7828530    77
    ## [1573] {other vegetables,                                                                                         
    ##         root vegetables,                                                                                          
    ##         whole milk}               => {yogurt}                   0.007829181  0.3377193 0.023182511 2.4208960    77
    ## [1574] {other vegetables,                                                                                         
    ##         whole milk,                                                                                               
    ##         yogurt}                   => {root vegetables}          0.007829181  0.3515982 0.022267412 3.2257165    77
    ## [1575] {other vegetables,                                                                                         
    ##         rolls/buns,                                                                                               
    ##         root vegetables}          => {whole milk}               0.006202339  0.5083333 0.012201322 1.9894383    61
    ## [1576] {rolls/buns,                                                                                               
    ##         root vegetables,                                                                                          
    ##         whole milk}               => {other vegetables}         0.006202339  0.4880000 0.012709710 2.5220599    61
    ## [1577] {other vegetables,                                                                                         
    ##         root vegetables,                                                                                          
    ##         whole milk}               => {rolls/buns}               0.006202339  0.2675439 0.023182511 1.4545571    61
    ## [1578] {other vegetables,                                                                                         
    ##         rolls/buns,                                                                                               
    ##         whole milk}               => {root vegetables}          0.006202339  0.3465909 0.017895272 3.1797776    61
    ## [1579] {other vegetables,                                                                                         
    ##         rolls/buns,                                                                                               
    ##         yogurt}                   => {whole milk}               0.005998983  0.5221239 0.011489578 2.0434097    59
    ## [1580] {rolls/buns,                                                                                               
    ##         whole milk,                                                                                               
    ##         yogurt}                   => {other vegetables}         0.005998983  0.3856209 0.015556685 1.9929489    59
    ## [1581] {other vegetables,                                                                                         
    ##         whole milk,                                                                                               
    ##         yogurt}                   => {rolls/buns}               0.005998983  0.2694064 0.022267412 1.4646832    59
    ## [1582] {other vegetables,                                                                                         
    ##         rolls/buns,                                                                                               
    ##         whole milk}               => {yogurt}                   0.005998983  0.3352273 0.017895272 2.4030322    59

Since there are too many rules, we chose lift threshold as 1 and
confidence threshold as 0.5. The below table shows the Left Hand Side
(antecedent) and Right Hand Side (consequent), support, confidence, lift
and etc…

    inspect(subset(itemrules, subset=lift > 1 & confidence > 0.5))

    ##       lhs                           rhs                    support confidence    coverage     lift count
    ## [1]   {baking powder}            => {whole milk}       0.009252669  0.5229885 0.017691917 2.046793    91
    ## [2]   {oil,                                                                                             
    ##        other vegetables}         => {whole milk}       0.005083884  0.5102041 0.009964413 1.996760    50
    ## [3]   {onions,                                                                                          
    ##        root vegetables}          => {other vegetables} 0.005693950  0.6021505 0.009456024 3.112008    56
    ## [4]   {onions,                                                                                          
    ##        whole milk}               => {other vegetables} 0.006609049  0.5462185 0.012099644 2.822942    65
    ## [5]   {hygiene articles,                                                                                
    ##        other vegetables}         => {whole milk}       0.005185562  0.5425532 0.009557702 2.123363    51
    ## [6]   {other vegetables,                                                                                
    ##        sugar}                    => {whole milk}       0.006304016  0.5849057 0.010777834 2.289115    62
    ## [7]   {long life bakery product,                                                                        
    ##        other vegetables}         => {whole milk}       0.005693950  0.5333333 0.010676157 2.087279    56
    ## [8]   {cream cheese,                                                                                    
    ##        yogurt}                   => {whole milk}       0.006609049  0.5327869 0.012404677 2.085141    65
    ## [9]   {chicken,                                                                                         
    ##        root vegetables}          => {other vegetables} 0.005693950  0.5233645 0.010879512 2.704829    56
    ## [10]  {chicken,                                                                                         
    ##        root vegetables}          => {whole milk}       0.005998983  0.5514019 0.010879512 2.157993    59
    ## [11]  {chicken,                                                                                         
    ##        rolls/buns}               => {whole milk}       0.005287239  0.5473684 0.009659380 2.142208    52
    ## [12]  {coffee,                                                                                          
    ##        yogurt}                   => {whole milk}       0.005083884  0.5208333 0.009761057 2.038359    50
    ## [13]  {frozen vegetables,                                                                               
    ##        root vegetables}          => {other vegetables} 0.006100661  0.5263158 0.011591256 2.720082    60
    ## [14]  {frozen vegetables,                                                                               
    ##        root vegetables}          => {whole milk}       0.006202339  0.5350877 0.011591256 2.094146    61
    ## [15]  {frozen vegetables,                                                                               
    ##        other vegetables}         => {whole milk}       0.009659380  0.5428571 0.017793594 2.124552    95
    ## [16]  {beef,                                                                                            
    ##        yogurt}                   => {whole milk}       0.006100661  0.5217391 0.011692933 2.041904    60
    ## [17]  {curd,                                                                                            
    ##        whipped/sour cream}       => {whole milk}       0.005897306  0.5631068 0.010472801 2.203802    58
    ## [18]  {curd,                                                                                            
    ##        tropical fruit}           => {yogurt}           0.005287239  0.5148515 0.010269446 3.690645    52
    ## [19]  {curd,                                                                                            
    ##        tropical fruit}           => {other vegetables} 0.005287239  0.5148515 0.010269446 2.660833    52
    ## [20]  {curd,                                                                                            
    ##        tropical fruit}           => {whole milk}       0.006507372  0.6336634 0.010269446 2.479936    64
    ## [21]  {curd,                                                                                            
    ##        root vegetables}          => {other vegetables} 0.005490595  0.5046729 0.010879512 2.608228    54
    ## [22]  {curd,                                                                                            
    ##        root vegetables}          => {whole milk}       0.006202339  0.5700935 0.010879512 2.231146    61
    ## [23]  {curd,                                                                                            
    ##        yogurt}                   => {whole milk}       0.010066090  0.5823529 0.017285206 2.279125    99
    ## [24]  {curd,                                                                                            
    ##        rolls/buns}               => {whole milk}       0.005897306  0.5858586 0.010066090 2.292845    58
    ## [25]  {curd,                                                                                            
    ##        other vegetables}         => {whole milk}       0.009862735  0.5739645 0.017183528 2.246296    97
    ## [26]  {pork,                                                                                            
    ##        root vegetables}          => {other vegetables} 0.007015760  0.5149254 0.013624809 2.661214    69
    ## [27]  {pork,                                                                                            
    ##        rolls/buns}               => {whole milk}       0.006202339  0.5495495 0.011286223 2.150744    61
    ## [28]  {frankfurter,                                                                                     
    ##        tropical fruit}           => {whole milk}       0.005185562  0.5483871 0.009456024 2.146195    51
    ## [29]  {frankfurter,                                                                                     
    ##        yogurt}                   => {whole milk}       0.006202339  0.5545455 0.011184545 2.170296    61
    ## [30]  {bottled beer,                                                                                    
    ##        yogurt}                   => {whole milk}       0.005185562  0.5604396 0.009252669 2.193364    51
    ## [31]  {brown bread,                                                                                     
    ##        tropical fruit}           => {whole milk}       0.005693950  0.5333333 0.010676157 2.087279    56
    ## [32]  {brown bread,                                                                                     
    ##        root vegetables}          => {whole milk}       0.005693950  0.5600000 0.010167768 2.191643    56
    ## [33]  {domestic eggs,                                                                                   
    ##        margarine}                => {whole milk}       0.005185562  0.6219512 0.008337570 2.434099    51
    ## [34]  {margarine,                                                                                       
    ##        root vegetables}          => {other vegetables} 0.005897306  0.5321101 0.011082867 2.750028    58
    ## [35]  {margarine,                                                                                       
    ##        rolls/buns}               => {whole milk}       0.007930859  0.5379310 0.014743264 2.105273    78
    ## [36]  {butter,                                                                                          
    ##        domestic eggs}            => {whole milk}       0.005998983  0.6210526 0.009659380 2.430582    59
    ## [37]  {butter,                                                                                          
    ##        whipped/sour cream}       => {other vegetables} 0.005795628  0.5700000 0.010167768 2.945849    57
    ## [38]  {butter,                                                                                          
    ##        whipped/sour cream}       => {whole milk}       0.006710727  0.6600000 0.010167768 2.583008    66
    ## [39]  {butter,                                                                                          
    ##        citrus fruit}             => {whole milk}       0.005083884  0.5555556 0.009150991 2.174249    50
    ## [40]  {bottled water,                                                                                   
    ##        butter}                   => {whole milk}       0.005388917  0.6022727 0.008947636 2.357084    53
    ## [41]  {butter,                                                                                          
    ##        tropical fruit}           => {other vegetables} 0.005490595  0.5510204 0.009964413 2.847759    54
    ## [42]  {butter,                                                                                          
    ##        tropical fruit}           => {whole milk}       0.006202339  0.6224490 0.009964413 2.436047    61
    ## [43]  {butter,                                                                                          
    ##        root vegetables}          => {other vegetables} 0.006609049  0.5118110 0.012913066 2.645119    65
    ## [44]  {butter,                                                                                          
    ##        root vegetables}          => {whole milk}       0.008235892  0.6377953 0.012913066 2.496107    81
    ## [45]  {butter,                                                                                          
    ##        yogurt}                   => {whole milk}       0.009354347  0.6388889 0.014641586 2.500387    92
    ## [46]  {butter,                                                                                          
    ##        other vegetables}         => {whole milk}       0.011489578  0.5736041 0.020030503 2.244885   113
    ## [47]  {newspapers,                                                                                      
    ##        root vegetables}          => {other vegetables} 0.005998983  0.5221239 0.011489578 2.698417    59
    ## [48]  {newspapers,                                                                                      
    ##        root vegetables}          => {whole milk}       0.005795628  0.5044248 0.011489578 1.974142    57
    ## [49]  {domestic eggs,                                                                                   
    ##        whipped/sour cream}       => {other vegetables} 0.005083884  0.5102041 0.009964413 2.636814    50
    ## [50]  {domestic eggs,                                                                                   
    ##        whipped/sour cream}       => {whole milk}       0.005693950  0.5714286 0.009964413 2.236371    56
    ## [51]  {domestic eggs,                                                                                   
    ##        pip fruit}                => {whole milk}       0.005388917  0.6235294 0.008642603 2.440275    53
    ## [52]  {citrus fruit,                                                                                    
    ##        domestic eggs}            => {whole milk}       0.005693950  0.5490196 0.010371124 2.148670    56
    ## [53]  {domestic eggs,                                                                                   
    ##        tropical fruit}           => {whole milk}       0.006914082  0.6071429 0.011387900 2.376144    68
    ## [54]  {domestic eggs,                                                                                   
    ##        root vegetables}          => {other vegetables} 0.007320793  0.5106383 0.014336553 2.639058    72
    ## [55]  {domestic eggs,                                                                                   
    ##        root vegetables}          => {whole milk}       0.008540925  0.5957447 0.014336553 2.331536    84
    ## [56]  {domestic eggs,                                                                                   
    ##        yogurt}                   => {whole milk}       0.007727504  0.5390071 0.014336553 2.109485    76
    ## [57]  {domestic eggs,                                                                                   
    ##        other vegetables}         => {whole milk}       0.012302999  0.5525114 0.022267412 2.162336   121
    ## [58]  {fruit/vegetable juice,                                                                           
    ##        root vegetables}          => {other vegetables} 0.006609049  0.5508475 0.011997966 2.846865    65
    ## [59]  {fruit/vegetable juice,                                                                           
    ##        root vegetables}          => {whole milk}       0.006507372  0.5423729 0.011997966 2.122657    64
    ## [60]  {fruit/vegetable juice,                                                                           
    ##        yogurt}                   => {whole milk}       0.009456024  0.5054348 0.018708693 1.978094    93
    ## [61]  {pip fruit,                                                                                       
    ##        whipped/sour cream}       => {other vegetables} 0.005592272  0.6043956 0.009252669 3.123610    55
    ## [62]  {pip fruit,                                                                                       
    ##        whipped/sour cream}       => {whole milk}       0.005998983  0.6483516 0.009252669 2.537421    59
    ## [63]  {citrus fruit,                                                                                    
    ##        whipped/sour cream}       => {other vegetables} 0.005693950  0.5233645 0.010879512 2.704829    56
    ## [64]  {citrus fruit,                                                                                    
    ##        whipped/sour cream}       => {whole milk}       0.006304016  0.5794393 0.010879512 2.267722    62
    ## [65]  {sausage,                                                                                         
    ##        whipped/sour cream}       => {whole milk}       0.005083884  0.5617978 0.009049314 2.198679    50
    ## [66]  {tropical fruit,                                                                                  
    ##        whipped/sour cream}       => {other vegetables} 0.007829181  0.5661765 0.013828165 2.926088    77
    ## [67]  {tropical fruit,                                                                                  
    ##        whipped/sour cream}       => {whole milk}       0.007930859  0.5735294 0.013828165 2.244593    78
    ## [68]  {root vegetables,                                                                                 
    ##        whipped/sour cream}       => {whole milk}       0.009456024  0.5535714 0.017081851 2.166484    93
    ## [69]  {whipped/sour cream,                                                                              
    ##        yogurt}                   => {whole milk}       0.010879512  0.5245098 0.020742247 2.052747   107
    ## [70]  {rolls/buns,                                                                                      
    ##        whipped/sour cream}       => {whole milk}       0.007829181  0.5347222 0.014641586 2.092715    77
    ## [71]  {other vegetables,                                                                                
    ##        whipped/sour cream}       => {whole milk}       0.014641586  0.5070423 0.028876462 1.984385   144
    ## [72]  {pip fruit,                                                                                       
    ##        sausage}                  => {whole milk}       0.005592272  0.5188679 0.010777834 2.030667    55
    ## [73]  {pip fruit,                                                                                       
    ##        root vegetables}          => {other vegetables} 0.008134215  0.5228758 0.015556685 2.702304    80
    ## [74]  {pip fruit,                                                                                       
    ##        root vegetables}          => {whole milk}       0.008947636  0.5751634 0.015556685 2.250988    88
    ## [75]  {pip fruit,                                                                                       
    ##        yogurt}                   => {whole milk}       0.009557702  0.5310734 0.017996950 2.078435    94
    ## [76]  {other vegetables,                                                                                
    ##        pip fruit}                => {whole milk}       0.013523132  0.5175097 0.026131164 2.025351   133
    ## [77]  {pastry,                                                                                          
    ##        tropical fruit}           => {whole milk}       0.006710727  0.5076923 0.013218099 1.986930    66
    ## [78]  {pastry,                                                                                          
    ##        root vegetables}          => {other vegetables} 0.005897306  0.5370370 0.010981190 2.775491    58
    ## [79]  {pastry,                                                                                          
    ##        root vegetables}          => {whole milk}       0.005693950  0.5185185 0.010981190 2.029299    56
    ## [80]  {pastry,                                                                                          
    ##        yogurt}                   => {whole milk}       0.009150991  0.5172414 0.017691917 2.024301    90
    ## [81]  {citrus fruit,                                                                                    
    ##        root vegetables}          => {other vegetables} 0.010371124  0.5862069 0.017691917 3.029608   102
    ## [82]  {citrus fruit,                                                                                    
    ##        root vegetables}          => {whole milk}       0.009150991  0.5172414 0.017691917 2.024301    90
    ## [83]  {root vegetables,                                                                                 
    ##        shopping bags}            => {other vegetables} 0.006609049  0.5158730 0.012811388 2.666112    65
    ## [84]  {sausage,                                                                                         
    ##        tropical fruit}           => {whole milk}       0.007219115  0.5182482 0.013929842 2.028241    71
    ## [85]  {root vegetables,                                                                                 
    ##        sausage}                  => {whole milk}       0.007727504  0.5170068 0.014946619 2.023383    76
    ## [86]  {root vegetables,                                                                                 
    ##        tropical fruit}           => {other vegetables} 0.012302999  0.5845411 0.021047280 3.020999   121
    ## [87]  {root vegetables,                                                                                 
    ##        tropical fruit}           => {whole milk}       0.011997966  0.5700483 0.021047280 2.230969   118
    ## [88]  {tropical fruit,                                                                                  
    ##        yogurt}                   => {whole milk}       0.015149975  0.5173611 0.029283172 2.024770   149
    ## [89]  {root vegetables,                                                                                 
    ##        yogurt}                   => {whole milk}       0.014539908  0.5629921 0.025826131 2.203354   143
    ## [90]  {rolls/buns,                                                                                      
    ##        root vegetables}          => {other vegetables} 0.012201322  0.5020921 0.024300966 2.594890   120
    ## [91]  {rolls/buns,                                                                                      
    ##        root vegetables}          => {whole milk}       0.012709710  0.5230126 0.024300966 2.046888   125
    ## [92]  {other vegetables,                                                                                
    ##        yogurt}                   => {whole milk}       0.022267412  0.5128806 0.043416370 2.007235   219
    ## [93]  {fruit/vegetable juice,                                                                           
    ##        other vegetables,                                                                                
    ##        yogurt}                   => {whole milk}       0.005083884  0.6172840 0.008235892 2.415833    50
    ## [94]  {fruit/vegetable juice,                                                                           
    ##        whole milk,                                                                                      
    ##        yogurt}                   => {other vegetables} 0.005083884  0.5376344 0.009456024 2.778578    50
    ## [95]  {other vegetables,                                                                                
    ##        root vegetables,                                                                                 
    ##        whipped/sour cream}       => {whole milk}       0.005185562  0.6071429 0.008540925 2.376144    51
    ## [96]  {root vegetables,                                                                                 
    ##        whipped/sour cream,                                                                              
    ##        whole milk}               => {other vegetables} 0.005185562  0.5483871 0.009456024 2.834150    51
    ## [97]  {other vegetables,                                                                                
    ##        whipped/sour cream,                                                                              
    ##        yogurt}                   => {whole milk}       0.005592272  0.5500000 0.010167768 2.152507    55
    ## [98]  {whipped/sour cream,                                                                              
    ##        whole milk,                                                                                      
    ##        yogurt}                   => {other vegetables} 0.005592272  0.5140187 0.010879512 2.656529    55
    ## [99]  {other vegetables,                                                                                
    ##        pip fruit,                                                                                       
    ##        root vegetables}          => {whole milk}       0.005490595  0.6750000 0.008134215 2.641713    54
    ## [100] {pip fruit,                                                                                       
    ##        root vegetables,                                                                                 
    ##        whole milk}               => {other vegetables} 0.005490595  0.6136364 0.008947636 3.171368    54
    ## [101] {other vegetables,                                                                                
    ##        pip fruit,                                                                                       
    ##        yogurt}                   => {whole milk}       0.005083884  0.6250000 0.008134215 2.446031    50
    ## [102] {pip fruit,                                                                                       
    ##        whole milk,                                                                                      
    ##        yogurt}                   => {other vegetables} 0.005083884  0.5319149 0.009557702 2.749019    50
    ## [103] {citrus fruit,                                                                                    
    ##        other vegetables,                                                                                
    ##        root vegetables}          => {whole milk}       0.005795628  0.5588235 0.010371124 2.187039    57
    ## [104] {citrus fruit,                                                                                    
    ##        root vegetables,                                                                                 
    ##        whole milk}               => {other vegetables} 0.005795628  0.6333333 0.009150991 3.273165    57
    ## [105] {root vegetables,                                                                                 
    ##        tropical fruit,                                                                                  
    ##        yogurt}                   => {whole milk}       0.005693950  0.7000000 0.008134215 2.739554    56
    ## [106] {other vegetables,                                                                                
    ##        root vegetables,                                                                                 
    ##        tropical fruit}           => {whole milk}       0.007015760  0.5702479 0.012302999 2.231750    69
    ## [107] {root vegetables,                                                                                 
    ##        tropical fruit,                                                                                  
    ##        whole milk}               => {other vegetables} 0.007015760  0.5847458 0.011997966 3.022057    69
    ## [108] {other vegetables,                                                                                
    ##        tropical fruit,                                                                                  
    ##        yogurt}                   => {whole milk}       0.007625826  0.6198347 0.012302999 2.425816    75
    ## [109] {tropical fruit,                                                                                  
    ##        whole milk,                                                                                      
    ##        yogurt}                   => {other vegetables} 0.007625826  0.5033557 0.015149975 2.601421    75
    ## [110] {other vegetables,                                                                                
    ##        root vegetables,                                                                                 
    ##        yogurt}                   => {whole milk}       0.007829181  0.6062992 0.012913066 2.372842    77
    ## [111] {root vegetables,                                                                                 
    ##        whole milk,                                                                                      
    ##        yogurt}                   => {other vegetables} 0.007829181  0.5384615 0.014539908 2.782853    77
    ## [112] {other vegetables,                                                                                
    ##        rolls/buns,                                                                                      
    ##        root vegetables}          => {whole milk}       0.006202339  0.5083333 0.012201322 1.989438    61
    ## [113] {other vegetables,                                                                                
    ##        rolls/buns,                                                                                      
    ##        yogurt}                   => {whole milk}       0.005998983  0.5221239 0.011489578 2.043410    59

The graph below plots the rules of our items data with 3 varaibles:
x-axis as support, y-axis as confidence, and depth of each scatter
pointes as lift.

    plot(itemrules)

    ## To reduce overplotting, jitter is added! Use jitter = 0 to prevent jitter.

![](Figs/unnamed-chunk-43-1.png) Here, we utilzed two-key plot which
colors the scatter plot by its order(size).

    plot(itemrules, method='two-key plot')

    ## To reduce overplotting, jitter is added! Use jitter = 0 to prevent jitter.

![](Figs/unnamed-chunk-44-1.png) Here, we swapped lift and confidence so
that the confidence is now the depth and lift is y-axis.

    # can swap the axes and color scales
    plot(itemrules, measure = c("support", "lift"), shading = "confidence")

    ## To reduce overplotting, jitter is added! Use jitter = 0 to prevent jitter.

![](Figs/unnamed-chunk-45-1.png)

By observing the plots above, we could test out different subsets of the
rule. Here, we tried to find the case where LHS and RHS have strong
relationship between them. Through the graph right above, we could
estimate our threshold of lift (2) and confidence (0.45). Below table
shows the items that have strong relationship between them. Most of them
are quite obvious which indicates that our model is working fine.

    inspect(subset(itemrules, lift > 2 & confidence > 0.45))

    ##       lhs                           rhs                    support confidence    coverage     lift count
    ## [1]   {herbs}                    => {other vegetables} 0.007727504  0.4750000 0.016268429 2.454874    76
    ## [2]   {baking powder}            => {whole milk}       0.009252669  0.5229885 0.017691917 2.046793    91
    ## [3]   {onions}                   => {other vegetables} 0.014234875  0.4590164 0.031011693 2.372268   140
    ## [4]   {oil,                                                                                             
    ##        whole milk}               => {other vegetables} 0.005083884  0.4504505 0.011286223 2.327998    50
    ## [5]   {onions,                                                                                          
    ##        root vegetables}          => {other vegetables} 0.005693950  0.6021505 0.009456024 3.112008    56
    ## [6]   {onions,                                                                                          
    ##        whole milk}               => {other vegetables} 0.006609049  0.5462185 0.012099644 2.822942    65
    ## [7]   {hygiene articles,                                                                                
    ##        other vegetables}         => {whole milk}       0.005185562  0.5425532 0.009557702 2.123363    51
    ## [8]   {other vegetables,                                                                                
    ##        sugar}                    => {whole milk}       0.006304016  0.5849057 0.010777834 2.289115    62
    ## [9]   {long life bakery product,                                                                        
    ##        other vegetables}         => {whole milk}       0.005693950  0.5333333 0.010676157 2.087279    56
    ## [10]  {cream cheese,                                                                                    
    ##        yogurt}                   => {whole milk}       0.006609049  0.5327869 0.012404677 2.085141    65
    ## [11]  {chicken,                                                                                         
    ##        root vegetables}          => {other vegetables} 0.005693950  0.5233645 0.010879512 2.704829    56
    ## [12]  {chicken,                                                                                         
    ##        root vegetables}          => {whole milk}       0.005998983  0.5514019 0.010879512 2.157993    59
    ## [13]  {chicken,                                                                                         
    ##        rolls/buns}               => {whole milk}       0.005287239  0.5473684 0.009659380 2.142208    52
    ## [14]  {chicken,                                                                                         
    ##        whole milk}               => {other vegetables} 0.008439248  0.4797688 0.017590239 2.479520    83
    ## [15]  {coffee,                                                                                          
    ##        yogurt}                   => {whole milk}       0.005083884  0.5208333 0.009761057 2.038359    50
    ## [16]  {frozen vegetables,                                                                               
    ##        root vegetables}          => {other vegetables} 0.006100661  0.5263158 0.011591256 2.720082    60
    ## [17]  {frozen vegetables,                                                                               
    ##        root vegetables}          => {whole milk}       0.006202339  0.5350877 0.011591256 2.094146    61
    ## [18]  {frozen vegetables,                                                                               
    ##        other vegetables}         => {whole milk}       0.009659380  0.5428571 0.017793594 2.124552    95
    ## [19]  {frozen vegetables,                                                                               
    ##        whole milk}               => {other vegetables} 0.009659380  0.4726368 0.020437214 2.442661    95
    ## [20]  {beef,                                                                                            
    ##        root vegetables}          => {other vegetables} 0.007930859  0.4561404 0.017386884 2.357404    78
    ## [21]  {beef,                                                                                            
    ##        yogurt}                   => {whole milk}       0.006100661  0.5217391 0.011692933 2.041904    60
    ## [22]  {curd,                                                                                            
    ##        whipped/sour cream}       => {whole milk}       0.005897306  0.5631068 0.010472801 2.203802    58
    ## [23]  {curd,                                                                                            
    ##        tropical fruit}           => {yogurt}           0.005287239  0.5148515 0.010269446 3.690645    52
    ## [24]  {curd,                                                                                            
    ##        tropical fruit}           => {other vegetables} 0.005287239  0.5148515 0.010269446 2.660833    52
    ## [25]  {curd,                                                                                            
    ##        tropical fruit}           => {whole milk}       0.006507372  0.6336634 0.010269446 2.479936    64
    ## [26]  {curd,                                                                                            
    ##        root vegetables}          => {other vegetables} 0.005490595  0.5046729 0.010879512 2.608228    54
    ## [27]  {curd,                                                                                            
    ##        root vegetables}          => {whole milk}       0.006202339  0.5700935 0.010879512 2.231146    61
    ## [28]  {curd,                                                                                            
    ##        yogurt}                   => {whole milk}       0.010066090  0.5823529 0.017285206 2.279125    99
    ## [29]  {curd,                                                                                            
    ##        rolls/buns}               => {whole milk}       0.005897306  0.5858586 0.010066090 2.292845    58
    ## [30]  {curd,                                                                                            
    ##        other vegetables}         => {whole milk}       0.009862735  0.5739645 0.017183528 2.246296    97
    ## [31]  {pork,                                                                                            
    ##        root vegetables}          => {other vegetables} 0.007015760  0.5149254 0.013624809 2.661214    69
    ## [32]  {pork,                                                                                            
    ##        rolls/buns}               => {other vegetables} 0.005592272  0.4954955 0.011286223 2.560798    55
    ## [33]  {pork,                                                                                            
    ##        rolls/buns}               => {whole milk}       0.006202339  0.5495495 0.011286223 2.150744    61
    ## [34]  {pork,                                                                                            
    ##        whole milk}               => {other vegetables} 0.010167768  0.4587156 0.022165735 2.370714   100
    ## [35]  {frankfurter,                                                                                     
    ##        tropical fruit}           => {whole milk}       0.005185562  0.5483871 0.009456024 2.146195    51
    ## [36]  {frankfurter,                                                                                     
    ##        yogurt}                   => {whole milk}       0.006202339  0.5545455 0.011184545 2.170296    61
    ## [37]  {bottled beer,                                                                                    
    ##        yogurt}                   => {whole milk}       0.005185562  0.5604396 0.009252669 2.193364    51
    ## [38]  {brown bread,                                                                                     
    ##        tropical fruit}           => {whole milk}       0.005693950  0.5333333 0.010676157 2.087279    56
    ## [39]  {brown bread,                                                                                     
    ##        root vegetables}          => {whole milk}       0.005693950  0.5600000 0.010167768 2.191643    56
    ## [40]  {domestic eggs,                                                                                   
    ##        margarine}                => {whole milk}       0.005185562  0.6219512 0.008337570 2.434099    51
    ## [41]  {margarine,                                                                                       
    ##        root vegetables}          => {other vegetables} 0.005897306  0.5321101 0.011082867 2.750028    58
    ## [42]  {margarine,                                                                                       
    ##        rolls/buns}               => {whole milk}       0.007930859  0.5379310 0.014743264 2.105273    78
    ## [43]  {butter,                                                                                          
    ##        domestic eggs}            => {whole milk}       0.005998983  0.6210526 0.009659380 2.430582    59
    ## [44]  {butter,                                                                                          
    ##        whipped/sour cream}       => {other vegetables} 0.005795628  0.5700000 0.010167768 2.945849    57
    ## [45]  {butter,                                                                                          
    ##        whipped/sour cream}       => {whole milk}       0.006710727  0.6600000 0.010167768 2.583008    66
    ## [46]  {butter,                                                                                          
    ##        citrus fruit}             => {whole milk}       0.005083884  0.5555556 0.009150991 2.174249    50
    ## [47]  {bottled water,                                                                                   
    ##        butter}                   => {whole milk}       0.005388917  0.6022727 0.008947636 2.357084    53
    ## [48]  {butter,                                                                                          
    ##        tropical fruit}           => {other vegetables} 0.005490595  0.5510204 0.009964413 2.847759    54
    ## [49]  {butter,                                                                                          
    ##        tropical fruit}           => {whole milk}       0.006202339  0.6224490 0.009964413 2.436047    61
    ## [50]  {butter,                                                                                          
    ##        root vegetables}          => {other vegetables} 0.006609049  0.5118110 0.012913066 2.645119    65
    ## [51]  {butter,                                                                                          
    ##        root vegetables}          => {whole milk}       0.008235892  0.6377953 0.012913066 2.496107    81
    ## [52]  {butter,                                                                                          
    ##        yogurt}                   => {whole milk}       0.009354347  0.6388889 0.014641586 2.500387    92
    ## [53]  {butter,                                                                                          
    ##        other vegetables}         => {whole milk}       0.011489578  0.5736041 0.020030503 2.244885   113
    ## [54]  {newspapers,                                                                                      
    ##        root vegetables}          => {other vegetables} 0.005998983  0.5221239 0.011489578 2.698417    59
    ## [55]  {domestic eggs,                                                                                   
    ##        whipped/sour cream}       => {other vegetables} 0.005083884  0.5102041 0.009964413 2.636814    50
    ## [56]  {domestic eggs,                                                                                   
    ##        whipped/sour cream}       => {whole milk}       0.005693950  0.5714286 0.009964413 2.236371    56
    ## [57]  {domestic eggs,                                                                                   
    ##        pip fruit}                => {whole milk}       0.005388917  0.6235294 0.008642603 2.440275    53
    ## [58]  {citrus fruit,                                                                                    
    ##        domestic eggs}            => {whole milk}       0.005693950  0.5490196 0.010371124 2.148670    56
    ## [59]  {domestic eggs,                                                                                   
    ##        tropical fruit}           => {whole milk}       0.006914082  0.6071429 0.011387900 2.376144    68
    ## [60]  {domestic eggs,                                                                                   
    ##        root vegetables}          => {other vegetables} 0.007320793  0.5106383 0.014336553 2.639058    72
    ## [61]  {domestic eggs,                                                                                   
    ##        root vegetables}          => {whole milk}       0.008540925  0.5957447 0.014336553 2.331536    84
    ## [62]  {domestic eggs,                                                                                   
    ##        yogurt}                   => {whole milk}       0.007727504  0.5390071 0.014336553 2.109485    76
    ## [63]  {domestic eggs,                                                                                   
    ##        other vegetables}         => {whole milk}       0.012302999  0.5525114 0.022267412 2.162336   121
    ## [64]  {fruit/vegetable juice,                                                                           
    ##        tropical fruit}           => {other vegetables} 0.006609049  0.4814815 0.013726487 2.488371    65
    ## [65]  {fruit/vegetable juice,                                                                           
    ##        root vegetables}          => {other vegetables} 0.006609049  0.5508475 0.011997966 2.846865    65
    ## [66]  {fruit/vegetable juice,                                                                           
    ##        root vegetables}          => {whole milk}       0.006507372  0.5423729 0.011997966 2.122657    64
    ## [67]  {pip fruit,                                                                                       
    ##        whipped/sour cream}       => {other vegetables} 0.005592272  0.6043956 0.009252669 3.123610    55
    ## [68]  {pip fruit,                                                                                       
    ##        whipped/sour cream}       => {whole milk}       0.005998983  0.6483516 0.009252669 2.537421    59
    ## [69]  {citrus fruit,                                                                                    
    ##        whipped/sour cream}       => {other vegetables} 0.005693950  0.5233645 0.010879512 2.704829    56
    ## [70]  {citrus fruit,                                                                                    
    ##        whipped/sour cream}       => {whole milk}       0.006304016  0.5794393 0.010879512 2.267722    62
    ## [71]  {sausage,                                                                                         
    ##        whipped/sour cream}       => {whole milk}       0.005083884  0.5617978 0.009049314 2.198679    50
    ## [72]  {tropical fruit,                                                                                  
    ##        whipped/sour cream}       => {other vegetables} 0.007829181  0.5661765 0.013828165 2.926088    77
    ## [73]  {tropical fruit,                                                                                  
    ##        whipped/sour cream}       => {whole milk}       0.007930859  0.5735294 0.013828165 2.244593    78
    ## [74]  {root vegetables,                                                                                 
    ##        whipped/sour cream}       => {other vegetables} 0.008540925  0.5000000 0.017081851 2.584078    84
    ## [75]  {root vegetables,                                                                                 
    ##        whipped/sour cream}       => {whole milk}       0.009456024  0.5535714 0.017081851 2.166484    93
    ## [76]  {whipped/sour cream,                                                                              
    ##        yogurt}                   => {other vegetables} 0.010167768  0.4901961 0.020742247 2.533410   100
    ## [77]  {whipped/sour cream,                                                                              
    ##        yogurt}                   => {whole milk}       0.010879512  0.5245098 0.020742247 2.052747   107
    ## [78]  {rolls/buns,                                                                                      
    ##        whipped/sour cream}       => {other vegetables} 0.006710727  0.4583333 0.014641586 2.368738    66
    ## [79]  {rolls/buns,                                                                                      
    ##        whipped/sour cream}       => {whole milk}       0.007829181  0.5347222 0.014641586 2.092715    77
    ## [80]  {whipped/sour cream,                                                                              
    ##        whole milk}               => {other vegetables} 0.014641586  0.4542587 0.032231825 2.347679   144
    ## [81]  {pip fruit,                                                                                       
    ##        sausage}                  => {whole milk}       0.005592272  0.5188679 0.010777834 2.030667    55
    ## [82]  {pip fruit,                                                                                       
    ##        tropical fruit}           => {other vegetables} 0.009456024  0.4626866 0.020437214 2.391236    93
    ## [83]  {pip fruit,                                                                                       
    ##        root vegetables}          => {other vegetables} 0.008134215  0.5228758 0.015556685 2.702304    80
    ## [84]  {pip fruit,                                                                                       
    ##        root vegetables}          => {whole milk}       0.008947636  0.5751634 0.015556685 2.250988    88
    ## [85]  {pip fruit,                                                                                       
    ##        yogurt}                   => {other vegetables} 0.008134215  0.4519774 0.017996950 2.335890    80
    ## [86]  {pip fruit,                                                                                       
    ##        yogurt}                   => {whole milk}       0.009557702  0.5310734 0.017996950 2.078435    94
    ## [87]  {other vegetables,                                                                                
    ##        pip fruit}                => {whole milk}       0.013523132  0.5175097 0.026131164 2.025351   133
    ## [88]  {pastry,                                                                                          
    ##        root vegetables}          => {other vegetables} 0.005897306  0.5370370 0.010981190 2.775491    58
    ## [89]  {pastry,                                                                                          
    ##        root vegetables}          => {whole milk}       0.005693950  0.5185185 0.010981190 2.029299    56
    ## [90]  {pastry,                                                                                          
    ##        yogurt}                   => {whole milk}       0.009150991  0.5172414 0.017691917 2.024301    90
    ## [91]  {citrus fruit,                                                                                    
    ##        tropical fruit}           => {other vegetables} 0.009049314  0.4540816 0.019928826 2.346765    89
    ## [92]  {citrus fruit,                                                                                    
    ##        root vegetables}          => {other vegetables} 0.010371124  0.5862069 0.017691917 3.029608   102
    ## [93]  {citrus fruit,                                                                                    
    ##        root vegetables}          => {whole milk}       0.009150991  0.5172414 0.017691917 2.024301    90
    ## [94]  {root vegetables,                                                                                 
    ##        shopping bags}            => {other vegetables} 0.006609049  0.5158730 0.012811388 2.666112    65
    ## [95]  {sausage,                                                                                         
    ##        tropical fruit}           => {whole milk}       0.007219115  0.5182482 0.013929842 2.028241    71
    ## [96]  {root vegetables,                                                                                 
    ##        sausage}                  => {other vegetables} 0.006812405  0.4557823 0.014946619 2.355554    67
    ## [97]  {root vegetables,                                                                                 
    ##        sausage}                  => {whole milk}       0.007727504  0.5170068 0.014946619 2.023383    76
    ## [98]  {root vegetables,                                                                                 
    ##        tropical fruit}           => {other vegetables} 0.012302999  0.5845411 0.021047280 3.020999   121
    ## [99]  {root vegetables,                                                                                 
    ##        tropical fruit}           => {whole milk}       0.011997966  0.5700483 0.021047280 2.230969   118
    ## [100] {tropical fruit,                                                                                  
    ##        yogurt}                   => {whole milk}       0.015149975  0.5173611 0.029283172 2.024770   149
    ## [101] {root vegetables,                                                                                 
    ##        yogurt}                   => {other vegetables} 0.012913066  0.5000000 0.025826131 2.584078   127
    ## [102] {root vegetables,                                                                                 
    ##        yogurt}                   => {whole milk}       0.014539908  0.5629921 0.025826131 2.203354   143
    ## [103] {rolls/buns,                                                                                      
    ##        root vegetables}          => {other vegetables} 0.012201322  0.5020921 0.024300966 2.594890   120
    ## [104] {rolls/buns,                                                                                      
    ##        root vegetables}          => {whole milk}       0.012709710  0.5230126 0.024300966 2.046888   125
    ## [105] {root vegetables,                                                                                 
    ##        whole milk}               => {other vegetables} 0.023182511  0.4740125 0.048906965 2.449770   228
    ## [106] {other vegetables,                                                                                
    ##        yogurt}                   => {whole milk}       0.022267412  0.5128806 0.043416370 2.007235   219
    ## [107] {fruit/vegetable juice,                                                                           
    ##        other vegetables,                                                                                
    ##        yogurt}                   => {whole milk}       0.005083884  0.6172840 0.008235892 2.415833    50
    ## [108] {fruit/vegetable juice,                                                                           
    ##        whole milk,                                                                                      
    ##        yogurt}                   => {other vegetables} 0.005083884  0.5376344 0.009456024 2.778578    50
    ## [109] {fruit/vegetable juice,                                                                           
    ##        other vegetables,                                                                                
    ##        whole milk}               => {yogurt}           0.005083884  0.4854369 0.010472801 3.479790    50
    ## [110] {other vegetables,                                                                                
    ##        root vegetables,                                                                                 
    ##        whipped/sour cream}       => {whole milk}       0.005185562  0.6071429 0.008540925 2.376144    51
    ## [111] {root vegetables,                                                                                 
    ##        whipped/sour cream,                                                                              
    ##        whole milk}               => {other vegetables} 0.005185562  0.5483871 0.009456024 2.834150    51
    ## [112] {other vegetables,                                                                                
    ##        whipped/sour cream,                                                                              
    ##        yogurt}                   => {whole milk}       0.005592272  0.5500000 0.010167768 2.152507    55
    ## [113] {whipped/sour cream,                                                                              
    ##        whole milk,                                                                                      
    ##        yogurt}                   => {other vegetables} 0.005592272  0.5140187 0.010879512 2.656529    55
    ## [114] {other vegetables,                                                                                
    ##        pip fruit,                                                                                       
    ##        root vegetables}          => {whole milk}       0.005490595  0.6750000 0.008134215 2.641713    54
    ## [115] {pip fruit,                                                                                       
    ##        root vegetables,                                                                                 
    ##        whole milk}               => {other vegetables} 0.005490595  0.6136364 0.008947636 3.171368    54
    ## [116] {other vegetables,                                                                                
    ##        pip fruit,                                                                                       
    ##        yogurt}                   => {whole milk}       0.005083884  0.6250000 0.008134215 2.446031    50
    ## [117] {pip fruit,                                                                                       
    ##        whole milk,                                                                                      
    ##        yogurt}                   => {other vegetables} 0.005083884  0.5319149 0.009557702 2.749019    50
    ## [118] {citrus fruit,                                                                                    
    ##        other vegetables,                                                                                
    ##        root vegetables}          => {whole milk}       0.005795628  0.5588235 0.010371124 2.187039    57
    ## [119] {citrus fruit,                                                                                    
    ##        root vegetables,                                                                                 
    ##        whole milk}               => {other vegetables} 0.005795628  0.6333333 0.009150991 3.273165    57
    ## [120] {root vegetables,                                                                                 
    ##        tropical fruit,                                                                                  
    ##        yogurt}                   => {whole milk}       0.005693950  0.7000000 0.008134215 2.739554    56
    ## [121] {root vegetables,                                                                                 
    ##        tropical fruit,                                                                                  
    ##        whole milk}               => {yogurt}           0.005693950  0.4745763 0.011997966 3.401937    56
    ## [122] {other vegetables,                                                                                
    ##        root vegetables,                                                                                 
    ##        tropical fruit}           => {whole milk}       0.007015760  0.5702479 0.012302999 2.231750    69
    ## [123] {root vegetables,                                                                                 
    ##        tropical fruit,                                                                                  
    ##        whole milk}               => {other vegetables} 0.007015760  0.5847458 0.011997966 3.022057    69
    ## [124] {other vegetables,                                                                                
    ##        tropical fruit,                                                                                  
    ##        yogurt}                   => {whole milk}       0.007625826  0.6198347 0.012302999 2.425816    75
    ## [125] {tropical fruit,                                                                                  
    ##        whole milk,                                                                                      
    ##        yogurt}                   => {other vegetables} 0.007625826  0.5033557 0.015149975 2.601421    75
    ## [126] {other vegetables,                                                                                
    ##        root vegetables,                                                                                 
    ##        yogurt}                   => {whole milk}       0.007829181  0.6062992 0.012913066 2.372842    77
    ## [127] {root vegetables,                                                                                 
    ##        whole milk,                                                                                      
    ##        yogurt}                   => {other vegetables} 0.007829181  0.5384615 0.014539908 2.782853    77
    ## [128] {rolls/buns,                                                                                      
    ##        root vegetables,                                                                                 
    ##        whole milk}               => {other vegetables} 0.006202339  0.4880000 0.012709710 2.522060    61
    ## [129] {other vegetables,                                                                                
    ##        rolls/buns,                                                                                      
    ##        yogurt}                   => {whole milk}       0.005998983  0.5221239 0.011489578 2.043410    59

The graph below shows graph for 100 rules. The transparent circles
represent support, and the circle’s color represents lift (more red =
high lift).

    sub1 = subset(itemrules, subset=confidence > 0.5 & support > 0.005)
    summary(sub1)

    ## set of 113 rules
    ## 
    ## rule length distribution (lhs + rhs):sizes
    ##  2  3  4 
    ##  1 91 21 
    ## 
    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   2.000   3.000   3.000   3.177   3.000   4.000 
    ## 
    ## summary of quality measures:
    ##     support           confidence        coverage             lift      
    ##  Min.   :0.005084   Min.   :0.5021   Min.   :0.008134   Min.   :1.974  
    ##  1st Qu.:0.005694   1st Qu.:0.5221   1st Qu.:0.009964   1st Qu.:2.109  
    ##  Median :0.006202   Median :0.5484   Median :0.011388   Median :2.268  
    ##  Mean   :0.007315   Mean   :0.5570   Mean   :0.013268   Mean   :2.394  
    ##  3rd Qu.:0.007931   3rd Qu.:0.5824   3rd Qu.:0.014642   3rd Qu.:2.657  
    ##  Max.   :0.022267   Max.   :0.7000   Max.   :0.043416   Max.   :3.691  
    ##      count       
    ##  Min.   : 50.00  
    ##  1st Qu.: 56.00  
    ##  Median : 61.00  
    ##  Mean   : 71.95  
    ##  3rd Qu.: 78.00  
    ##  Max.   :219.00  
    ## 
    ## mining info:
    ##          data ntransactions support confidence
    ##  transactions          9835   0.005        0.1

    plot(head(sub1, 100, by='lift'), method='graph')

![](Figs/unnamed-chunk-47-1.png)

    saveAsGraph(head(itemrules, n = 1000, by = "lift"), file = "itemrules.graphml")

Below graphs are exported from the visualization program “Gephi”. The
first graph is a result from the layout called “Fruchterman Reingold”
which represents the whoel association rules in a circular way (heavier
as close to the center) and the second one is the result from the layout
called “Label Layout” which spreads out the rules by the frequency of
items (heavier as far away from the center).

![Fruchterman
Reingold](/Users/macintosh/Documents/R%20studio/Gephi-Fruchterman%20Reingold.png)
![Label-Layout](/Users/macintosh/Documents/R%20studio/Gephi-Label%20Layout.png)
