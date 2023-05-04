# reversal_strategy

## Strategy Characteristics

**Name:** Momentum/Reversal Strategy Segmenting by Company Characteristics (Size and Volatility) 
**Asset class:** Equities
**Universe:** NYSE, AMEX, ARMA, and NASDAQ
**Style:** Long-Short

## Methodology

This strategy uses the momentum/reversal effect but considers company characteristics. I explored 4 different datasets in different timeframes: 2000-2006, 2006-2012, 2012-2018, and 2018-2022. The first period is used to set the parameters and answer the following:
1.	Is there reversal or momentum?
2.	Do company characteristics (volatility and size) matter? 
3.	What formation and trading period is best?
The other three periods are used to test my findings from the questions above. This will help to avoid overfitting the model and test for robustness.

The portfolio construction and ticker selection for every trading period are exemplified below:

![image](https://user-images.githubusercontent.com/114669230/236274654-d2215288-de51-4920-b637-a0ac992a3e3c.png)

1.	In the formation period cumulative returns, volatility, and average market capitalisation are calculated. 
2.	I filtered out illiquid stocks: 1) No NA values in formation period, 2) Price > 10 USD. 
3.	I segmented the stocks into two groups: large-cap and small-cap.
4.	I created quintile groups based on past volatility and again based on past returns. 
5.	The returns for each portfolio are calculated.

I did this analysis for different combinations of formation periods (20, 30, 60, 90, and 252 days) and trading periods (5 and 10 days). To see all the results, refer to the Jupyter Notebook.

To avoid biases in each period analysed, I retrieved the tickers available at the beginning of the period. As well, I added a penalty in every transaction to consider for bid-ask spread. The median bid-ask spread for the price of all datasets is a maximum .2%, which is indicative of good liquidity

## Results

The below patterns were found:

•	Strong evidence of reversal behaviour.
•	Small firms outperform large firms.
•	The middle volatility quintiles exhibit the best performance for long-only portfolios. Considering all portfolios, the long-short portfolio with the most volatile stocks outperforms across most periods.

Based on a thorough analysis from 2000 to 2006, was concluded that the best formation and trading periods are 60-10 and 30-10. The best portfolio to have is the following:

•	Long on losers and short on winners (reversal effect).
•	Small-cap stocks.
•	Most volatile group (5th quintile)

In the appendix in section 1 can be found the cumulative performance - our portfolio of interest is the purple one. In section 2, can be found the summary statistics - our portfolio of interest is the one highlighted in red. The results in the appendix are for a 60-10 formation and trading period, to see the 30-10 variation check the Jupyter Notebook.

## Conclusion

The strategy seems robust. The strategy consists on forming a long-short portfolio of small and volatile stocks and taking advantage of the reversal effect.  Across the 4 different periods using 30-10 and 60-10, this portfolio outperforms the other portfolios and experiences the highest Sharpe ratio. However, the Sharpe ratio has been decaying over time and the drawdowns became huge from 2018 to 2022. Could be implemented a CPPI algorithm to reduce the drawdowns. 

## Appendix

1. Cumulative Performance

Figure 1.0

![image](https://user-images.githubusercontent.com/114669230/236275261-1c76334b-b38f-443e-9d2c-947186671e39.png)

Figure 1.1

![image](https://user-images.githubusercontent.com/114669230/236275297-a393aeb9-dcf4-4450-afc4-243dc1f5aa10.png)

Figure 1.2

![image](https://user-images.githubusercontent.com/114669230/236275336-1a4b05f5-9011-49d1-871a-4f9533a601e4.png)


2. Summary Statistics

Table 2.0 – Summary Statistics 2006-2012

![image](https://user-images.githubusercontent.com/114669230/236275369-6c3ff4de-67ac-42bd-85fc-c6d562d8139e.png)

Table 2.1 – Summary Statistics 2012-2018

![image](https://user-images.githubusercontent.com/114669230/236275406-6da6627a-f663-4ce4-8e04-4f597b1437be.png)

Table 2.2 – Summary Statistics 2018-2022

![image](https://user-images.githubusercontent.com/114669230/236275428-0e3ee351-1367-45fd-a686-c6febb845df9.png)
