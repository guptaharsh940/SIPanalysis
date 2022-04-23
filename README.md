# SIP Data Analysis

Description: In this Project, I tried to analyze the SIP Returns of Nifty 50 Index ETF taking the Nippon India Nifty Bees as the base data.

# Initiation

Chose the base data as Nippon India’s Nifty Bees, as it was one of the most actively traded ETFs and the data was available since 2002 so it was a complete 20 Years of ETF Price data for 20 Years.

Source of data = [www.Investing.com](https://www.investing.com/etfs/goldman-sachs-nifty-historical-data)

Then used an amount of INR 5000/Month SIP for the entire 20 year period. 

Then I used the data to form the various Categories discussed in the future sections and derived the XIRR for an entire time period in excel and through python. More on that in the sections below.

The final goal was to see what is the maximum and minimum returns you can achieve through SIP and how do the returns spread from the Short to the Long term. And in the project, I was successful to do the same.

## Some Assumptions

As you know everything on paper cannot be compared exactly with real life so here are some of the assumptions I made:

- Used an ETF and not included all the Transaction Charges, LTCG and Brokerage. This was because it would have made the already lengthy calculation more lengthy and prone to more mistakes. Also, various different brokers have different brokerage charges on Equity Deliver but the top broker in India ‘Zerodha’ has 0 Brokerage on Equity Delivery so it doesn't make a huge difference in the calculations.
- Obviously, everyone cannot be as disciplined and invest continuously the same amount every month without fail manually in some cases like (Spoiler Alert) Daily, Weekly and on every monthly Expiry. Even though you can start a SEP (Systematic Equity Plan) which is like a SIP for a Stock or an ETF which will give you the option for setting the frequency to even Daily but it isn’t possible for the last Thursday of every month.
- If you have a Demat Account with a broker which charges some Brokerage for Equity Delivery then Daily & Weekly investing would not be as beneficial for you as you might end up paying more in Brokerage and the returns would shrink.
- I Rounded down the Quantity of ETF you can get for the money in the whole numbers as you cannot buy it in fractional quantity. For eg:- With INR 5000 and the ETF trading at INR 183/share you can get 27.3224043715847 shares but I rounded it down to 27 Quantity which results in the investment of INR 4941 investment and the rest INR 59 left uninvested. This doesn’t become a big problem in Monthly SIP, while in Daily SIP you end up having a lot of uninvested amount. Though this doesn’t affect the Return Percentage.

# Types of SIPs

The Various Types of SIPs compared are the following

- **Normal SIP**
    
    Purchasing the ETF of almost INR 5000 on the first trading day of the Month
    
- **Expiry SIP**
    
    Purchasing the ETF of almost INR 5000 on the last Thursday of every month which is the Weekly as well as the Monthly Expiry and is presumably one of the most volatile days of the Month. Also if Thursday is a Holiday then buying on the Previous Trading Day. 
    
- **Min SIP**
    
    Hypothetically, Purchasing the ETF of almost INR 5000 at the lowest point of Nifty in that particular month. This is to find out the maximum return you could get doing the SIP. 
    
- **Max SIP**
    
    Hypothetically, Purchasing the ETF of almost INR 5000 at the highest point of Nifty in that particular month. This is to find out the minimum return you could get doing the SIP. 
    
- **Week SIP**
    
    Purchasing the ETF of INR (5000*12) / (Number of Weeks in that Year) on the first trading day of that week.
    
- **Day SIP**
    
    Purchasing the ETF of INR 5000 / (Number of Trading in that Month) Daily at the Closing Price of that Day. 
    

I then calculated the XIRR of all of the above using Python as well as Excel and during the process, I realized that Excel and my Python function gave the same results until the data was small but the Returns differed as data became bigger. So to cross-check I also tested another function to calculate the XIRR from [Stack Overflow](https://stackoverflow.com/a/11503492/16929310) and the results with my function and the function from Stack Overflow matched so I concluded that Excel estimates the returns as the data gets bigger to make the formula work faster.

So you can see that I used two Hypothetical cases and four Doable cases in which the one (Expiry SIP) requires manual intervention until you are a coder and automate the stuff. 

The two hypothetical cases here are used to quench the curiosity of how much better returns you can get in those cases and the results are somewhat interesting.

The Normal SIP, Week SIP & Day SIP are the most commonly used options in Index Funds.

Some people might ask why I didn’t calculate other cases like some lucky dates, mid-month etc. The simple answer to that is, they do not hold any fundamental sense or special events like Expiry Day. The thing is that even if I evaluate the returns for those dates they might not valid for the next 20 Years as that might only be a one-time lucky return.

## Timeframes

I also distributed the data in various timeframes to get an idea of how does different SIPs perform in the Short-Term, Medium-Term and the Long-Term because only looking at one timeframe will give this Analysis not so detailed results so the following Time Frames which are presented by this Analysis are as follows:

- **1 Year**

    From the first trading day to the last trading day of each year I calculated the Returns of all 6 types of SIPs for all 20 Individual Years which gave me 120 XIRR Values. Then took the recent 20, 15, 10 & 5 Years of Data Averages to get the picture of how is the trend changing along with time.
    
- **3 Years**
   
    I made sets of three years like ‘2002 - 2004’, ‘2003 - 2005’ and so on. This evaluated the returns within the first trading day of say 2002 to the last trading day of 2004 and cashing out on the last trading day of 2004. Which gave me 18 sets of years and for 6 types, resulting in 108 XIRR Values. Also calculated the recent 20, 15, 10 & 5 Years of Data Averages.
    
- **5 Years**

    In this, I made sets of five years this time like ‘2002 - 2006’, ‘2003 - 2007’ and so on. This evaluated the returns within the first trading day of say 2002 to the last trading day of 2004 and cashing out on the last trading day of 2006. Which gave me 16 sets of years and for 6 types, resulting in 96 XIRR Values. Also calculated the recent 20, 15 & 10 Years of Data Averages as the recent 5 Years is calculated in the last set of Years.
    
- **7 Years**

    Similarly made sets of seven years like ‘2002 - 2008’ and got 14 sets which gave 84 XIRR Values. Also calculated the recent 20, 15 & 10 Years of Data Averages.
    
- **15 Years**

    Similarly made sets of seven years like ‘2002 - 2016’ and got 6 sets which gave 36 XIRR Values. Also calculated the recent 20 Years of Data Average as 15 Year Average return can be taken from the last set of years.
    
- **20 Years**
 
    Here I calculated the entire 20 Years SIP returns and used the Cash Outflow date of the last trading day data which was recorded in the initial data i.e. 31st Jan 2022.
  
 
 # The Logic

The simple logic I used was to take the raw data and according to each type of SIPs, I separated the dates to do SIP on whether it would be the First Trading day or the variable Expiry Dates for every month. Then getting the closing price of that day and then dividing the Investment Amount by that price, the Investment Amounts for different cases are :

- **Monthly** - INR 5000
- **Weekly** - INR (5000*12) / Number of Weeks in that Year
- **Daily** - INR 5000 / No. of Trading Days in that month.

Then Rounding Down the Quantity to the just below whole number and then add that to their respective Pandas data frame and which is then added to their respective ‘.csv’ files in the ‘SIP Details’ Folder. 

To evaluate the XIRR I used my own code which was obviously slow as I am a newbie to coding right now but it worked accurately and when compared with the better code available on the [Stack Overflow](https://stackoverflow.com/a/11503492/16929310) it was faster for a small number of cashflows but relatively slow for more cashflows. 

[Internal Rate of Return Algo](https://www.notion.so/Internal-Rate-of-Return-Algo-af46f1a39d664f68a7cd6a5537702eff) 

- **How does XIRR Work**
    
    So for those who don’t know actually XIRR takes the dates and cashflows which are -ve for Cash Outflows and +ve for Cash Inflows and calculates the time adjusted returns by discounting the cashflows by (1+r)^t, where r is the rate of return and t is the Time in years since the first cashflow. So when you add all of the Cashflows you should get a 0, hence as we need to find r for such a long equation we need to use hit and trial method to reach the best return which results almost 0. For more info you can go to [Investopedia Link](https://www.investopedia.com/terms/i/irr.asp).   
    

To calculate the XIRR, you require the final cash outflow which I stupidly took the last cash inflow date i.e. the last date of the last SIP Amount, you have hypothetically taken out the money on that day’s price itself. The problem with that was that as the Cash Outflow date varied with different types of SIPs the ‘Min SIP’ and ‘Max SIP’ didn’t show the Best & Worst Returns respectively for all time frames which we are gonna talk about in detail below. 

So correcting my stupidity, I then chose to take the Last day of Every Trading Year as the cash outflow date and that day’s price and for the entire 20 years of data, I used the last trading day’s data in the Initial Data which was 31st January 2022.

Now making sets of all types of timeframes and taking making one function which is used for all 6 types of SIPs taking the Type name as Argument takes just less than 4 mins to compile and give all the 450 XIRR Values to compare resulting in a total of 704 Data Points after calculating various Averages and Range.

You can read through the code in the ‘.ipynb’ Jupyter Notebook attached in the Github Repo but a lot of code is quite roughly written for just one-time use so kindly ignore the efficiency and the way I wrote the code as this is my first Small Python Project.

# Analysis

## Colour Code

So the Conditional Formatting has been done within each row to compare the Highest to Lowest Returns within one timeframe. 

Min SIP & Max SIP Return Values have been ruled out as they are completely unachievable. 

**Dark Orange -** Signifies the Least Return in that particular Timeframe

**Orange -** Signifies the Second Least Return in that particular Timeframe

**Green -** Signifies the Second Best Return in that particular Timeframe

**Dark Green -** Signifies the Best Return in that particular Timeframe

## 1 Year Timeframe
![image](https://user-images.githubusercontent.com/30728750/164890232-4115552c-cd02-409f-a39b-94f3bc00a0ff.png)

- Here the **Normal SIP** has given the worst returns and the **Expiry SIP** has given the best returns.
- **Day SIP** is slightly better than **Week SIP**.
- The Range between the best of four and the worst is 2.56% for the last 20 Year's Average.
- **Big Difference in Maximum Returns and the Minimum Returns** in the short-term average.

## 3 Years Timeframe
![image](https://user-images.githubusercontent.com/30728750/164890246-fd9d2008-12be-4d8d-aff0-d191de144238.png)

- The Returns here become slightly more confusing but still, **Expiry SIP** has still performed the best and **Normal SIP** the worst.
- Here both **Week SIP** & **Day SIP** has performed almost similarly.
- The Range between the best of four and the worst is now reduced to just 0.45% for the last 20 Year's Average.
- The difference between the **Max SIP** and the **Min SIP** has also been reduced by almost more than 3 times.

## 5 Years Timeframe
![image](https://user-images.githubusercontent.com/30728750/164890264-7303e78c-70da-40af-a6ad-aa1b160bd6d7.png)

- Not Very Different from the previous two datasets, **Expiry SIP** is still the best and **Normal SIP** the worst.
- **Week SIP** & **Day SIP** performed almost similarly.
- The Range between the best of four and the worst is now reduced to 0.2% for the last 20 Year's Average.
- The difference between the **Max SIP** and the **Min SIP** has also been reduced by almost 2 times.

## 7 Years Timeframe
![image](https://user-images.githubusercontent.com/30728750/164890271-ab3bdedb-ad36-4123-b921-5563de201014.png)

- Again **Expiry SIP** is still the best and **Normal SIP** the worst.
- **Week SIP** & **Day SIP** performed almost similarly.
- The Range between the best of four and the worst is now reduced to 0.13% for the last 20 Year's Average.
- The difference in the **Max SIP** and the **Min SIP** has also been slightly reduced.

## 15 Years Timeframe
![image](https://user-images.githubusercontent.com/30728750/164890275-e657f7be-26aa-4244-8403-cf5890693349.png)

- Here though **Normal SIP** has still performed the worst that too by a very little difference but the **Expiry SIP**, **Week SIP** & **Day SIP** all have performed mostly similarly.
- The Range between the best of four and the worst is now reduced to 0.05% for the last 20 Year's Average.
- The difference in the **Max SIP** and the **Min SIP** has also been reduced to less than 1%.

## 20 Years Timeframe
![image](https://user-images.githubusercontent.com/30728750/164890311-8dbc35ba-d773-41f7-95fd-4cbb85b03091.png)

- Here the constant is that the **Normal SIP** has still given the worst return.
- But surprisingly the winner here is **Day SIP** & **Week SIP**.
- Also maybe due to some calculation error of such a long period **Min SIP** & **Max SIP** return numbers are not the Maximum & Minimum among all other types of SIP.

## Conclusion

Finally, until 15 Years of **Expiry SIP** i.e. Buying the Index ETF on the Monthly Expiry of that month has given the best IRR 

While we can see the clear trend that as the timeframe increases the difference between the returns of various types of SIPs taken in this Analysis decreases substantially. And as we reach the 20 Years mark the difference is quite less but even 0.5% compounded interest may give you a good difference in Absolute Return but not very exorbitant.

As the above analysis is done for the previous 20 years of data, it's not necessary that the same may repeat over the next 20 Years.

So finally the thing which we can derive through the analysis is that if you can manage to buy the ETF on the Monthly Expiry with proper discipline, then you can go ahead and go for that route for a better return in short term but as we know that discipline is a very big issue when we talk about a long period so an automatic SIP like Normal SIP, Week SIP & Day SIP are the options left. Out of these, I would say that Week SIP would be the best pick as over a longer term it can definitely average out better, while Daily SIP can be better but only if your SIP Amount is good enough to buy at least one unit of ETF every day which increases day by day.

Instead of buying ETF Daily or Weekly, I would recommend starting a SIP with any Index Direct Mutual Fund as there is no issue of buying units of the stock in whole numbers.

I hope with all this detailed analysis you would be able to make a decision on how you can plan your investment over a long or short period and see the volatility of the market with the data in each and every period. I think even if you would not agree with my conclusion over the data, you can surely derive your own.
