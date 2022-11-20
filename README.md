# FX Average Noon Rate Agreement Valuation


Foreign Exchange Rate Average Noon Rate Agreement (ANR) is an agreement to buy or sell USD dollars on a future value date at a rate equal to the average rate for a specified period and adjusted by forward points agreed at the inception. 

Notations used as follows.

t	Valuation Date
T	Maturity Date
 
Settlement Date
 
Spot Exchange Rate at time  

 
Risk-free discount rate of currency Ccy
 
Averaging start date
K	Strike price = Fixed Forward Points
 
Historical exchange rate at time  

 
Forward exchange rate for time interval (t,  ), where  

N	Notional amount

The average exchange rate,  , with m historical rate averaging points and n spot rate averaging points, is computed as

     if   ,  and        if   .

where  ,   and   if  , and   if  .  

The average forward rate,  , is then computed as

   if   ,  and      if   

and the forward exchange rate is computed as  , where  . 

The actual pricing (Mark-to-Market) is done at the inventory level and is in the base currency, which is usually USD. Currently, this product can only be used by Indirect Currencies, and is normally used in CADUSD only. Therefore, this report examines indirect quote only.

The rates are quoted as  . The notional currency is in USD only and the payoff currency is CAD only. The payoff at the maturity is defined as   in CAD. The expected payoff is then calculated as

 .

where   (1 or –1) is the long / short indicator. The price of the contract in USD is obtained by dividing the expected payoff by the forward rate,  , and by discounting it with USD

 	  	  (1)

The price of the contract and the perturbation of the spot rate in delta calculation is in USD/CAD. Thus, the perturbation of the spot is done as   and   where  . Thus, the USD Delta is defined by

USD Delta =                                             (2)

ANR payoff can de decomposed into two NRCs as the following.

 

where the first term on the right hand side is the payoff of a NRC with strike price –K, and the second term is the payoff of a one day NRC ( ) with zero strike price . Thus, a long position of ANR is decomposed into a short of the first NRC and a long of the second NRC. The ANR pricing can be written as

  	   		     (3)

where 

 		      (4)

and 

 	                  (5)

The second NRC, equation (5), is actually a cash instrument and, therefore, it has zero delta value. 

We examine the pricing and delta calculation with 5 test cases (for each of these test cases, ANR decomposition into 2 NRCs are also tested). The valuation date (called Spot Date in Atlas) is August 31, 2004. Actual/365 for Day Count Base, Daily Averaging frequency, and N=1,000,000 USD is used in all test cases.  

It is possible that matured ANR could be in the system (not paid out to clients) and, thus, daily Mark-to-Market and Delta calculations are also done on those matured ANRs. For a matured ANR, the pricing in equations (1), (4) and (5) are modified as the following. 

 	      	   (6)
   	               (7)
   			               (8)

Here,   is calculated only from historical rates and the forward rate in equation (1) and (4) becomes the spot rate   in the above equations (6) and (7). Since the pricing in equations (6) and (7) involve the spot price, which varies day-to-day, there are non-zero delta values on these cases (see case 1 in table 2). Note that the 2nd NRC, equation (8), should have the maturity date same as valuation date (i.e.,  ). You can find other pricing models at https://finpricing.com/lib/FiBond.html


Appendix 1. Test Cases

	Base Currency: USD
	Underlying Currency: CAD
	Principal Amount: 1,000,000 USD
	Spot Rate: 1.31895 CAD/USD

Case No.	Position (Buy / Sell)	Start Date	Maturity Date	Settlement Date	Strike Price
1	Sell	01-Jun-2004	30-Jun-2004	01-Jul-2004	0.0013
2	Sell	03-Aug-2004	03-Sep-2004	07-Sep-2004	-0.0075
3	Sell	18-Sep-2007	17-Oct-2007	18-Oct-2007	0.0156
4	Buy	25-Feb-2005	30-Mar-2005	31-Mar-2005	0.0105
5	Buy	10-Aug-2004	09-Sep-2004	10-Spe-2004	-0.0025

Appendix 2. Forward Foreign Exchange Rate

Number of Days from Valuation Date	CAD/USD Forward Points 
(bps)	CAD/USD Forward Outright
7	1.1500	1.319065
14	2.4500	1.319195
30	5.4500	1.319495
59	11.2000	1.320070
91	17.5000	1.320700
122	23.0000	1.321250
153	29.0000	1.321850
181	34.5000	1.322400
273	52.0000	1.324150
365	67.5000	1.325700
546	94.7500	1.328425
730	122.0000	1.331150

Appendix 3. USD Discount Factor

Number of Days from Valuation Date	USD DF

7	0.99969190
14	0.99938399
30	0.99868091
61	0.99716984
91	0.99558334
181	0.99031568
273	0.98421443
365	0.97755095
730	0.94537551
1,098	0.90750025
1,462	0.86651370
1,826	0.82442859


Appendix 4. Historical Rate



