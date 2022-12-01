![](Trading%20Wizard.jpg)
# <div align = "center"> Challenge-Two
## <div align = "center"> Team Two
### <div align = "center"> Akhil Kavuri, Brendan Van Maaneen, Danny Milsom, Henry Date and Ling Dong
#### <div align = "center"> *AN INTERACTIVE TRADING & INVESTEMENT MACHINE BOT*

**1. Project Aim:**  
To build an interactive and intuitive trading BOT that optimises techical indicators through machine learning (Ensemble Technique) to provide highly accurate investment and trading recommendations. Importantly the BOT is to reliablely predict how price interacts with technical indicators (EMA) in order to maximise indicator trading performance.   
To allow for a high degree of "fine tuning" the BOT model relied up the Ensemble Technique 
  
  
***To utilise machine learning to outcompete the profitability and risk of the S&P 500 (Sharpe Ratio).  
Determine best trading strategy using Machine Learning and trading technical indicator for S&P 500.
We are trying to train a model to predict which indicators best predict index prices?**

  
**2. Key Technologies:** 
  
To use machine learning through the Ensemble Method to filter accurate buy/sell recommendations from three key technical indicationrs.


   [MACD](https://investopedia.com/terms/m/macd.asp)  
   Moving average convergence/divergence (MACD, or MAC-D) is a trend-following momentum indicator that shows the relationship between two exponential moving averages      (EMAs) of a security’s price. The MACD line is calculated by subtracting the 26-period EMA from the 12-period EMA.
   
   [Bollinger Bands](https://www.investopedia.com/terms/b/bollingerbands.asp)  
  A Bollinger Band® is a technical analysis tool defined by a set of trendlines plotted two standard deviations (positively and negatively) away from a simple moving average (SMA) of a security's price, but which can be adjusted to user preferences.
  
  [Exponential Moving Averages](https://investopedia.com/terms/e/ema.asp)  
   An exponential moving average (EMA) is a type of moving average (MA) that places a greater weight and significance on the most recent data points. The exponential moving average is also referred to as the exponentially weighted moving average. An exponentially weighted moving average reacts more significantly to recent price changes than a simple moving average simple moving average (SMA), which applies an equal weight to all observations in the period.
  
  [Relative Strength Index](https://investopedia.com/terms/r/rsi.asp)  
  The relative strength index (RSI) is a momentum indicator used in technical analysis. RSI measures the speed and magnitude of a security's recent price changes to evaluate overvalued or undervalued conditions in the price of that security.
  
  [Ensemble Methods](https://scikit-learn.org/stable/modules/ensemble.html)  
  The goal of ensemble methods is to combine the predictions of several base estimators built with a given learning algorithm in order to improve generalizability/  robustness over a single estimator.  
  Ensemble methods use:
  
 1. [Logistic Regression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html?highlight=logistic+regression)  
    In the multiclass case, the training algorithm uses the one-vs-rest (OvR) scheme if the ‘multi_class’ option is set to ‘ovr’, and uses the cross-entropy loss if       the ‘multi_class’ option is set to ‘multinomial’. (Currently the ‘multinomial’ option is supported only by the ‘lbfgs’, ‘sag’, ‘saga’ and ‘newton-cg’ solvers.)
 2. [GaussianNB](https://scikit-learn.org/stable/modules/generated/sklearn.naive_bayes.GaussianNB.html?highlight=gaussiannb#sklearn.naive_bayes.GaussianNB)  
    Can perform online updates to model parameters via partial_fit. For details on algorithm used to update feature means and variance online, see Stanford CS tech         report STAN-CS-79-773 by Chan, Golub, and LeVeque.
 3. [XGBClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.GradientBoostingClassifier.html)  
    This algorithm builds an additive model in a forward stage-wise fashion; it allows for the optimization of arbitrary differentiable loss functions. In each stage       n_classes_ regression trees are fit on the negative gradient of the loss function, e.g. binary or multiclass log loss. Binary classification is a special case         where only a single regression tree is induced.
 4. [Voting Classifier](https://scikit-learn.org/stable/modules/ensemble.html#voting-classifier)
    The idea behind the VotingClassifier is to combine conceptually different machine learning classifiers and use a majority vote or the average predicted                 probabilities (soft vote) to predict the class labels. Such a classifier can be useful for a set of equally well performing models in order to balance out             their individual weaknesses.
    
  [Amazon LEX](https://aws.amazon.com/lex/)  
  Easily add AI that understands intent, maintains context, and automates simple tasks across many languages.

 
    c. Optimise weightings between 3 indices (if time permits).  
    

  
  
  
a.	To utilise machine learning to outcompete the profitability and risk of the S&P 500 (Sharpe Ratio).  
b.	Determine best trading strategy using Machine Learning and trading technical indicator for S&P 500.
c.	We are trying to train a model to predict which indicators best predict index prices?


2.	What is the machine learning component predicting?
a.	Predicting how price interacts with technical indicator (EMA)
b.	Testing models to maximise indicator performance
c.	What is the feature set? Prediction set? 
i.	Feature set: date, high, low, open, close
ii.	Prediction set: indicator crossing EMA 30
Target: 

What are we trying to solve? 
To utilise machine learning to outcompete the profitability and risk of the S&P 500 (Sharpe Ratio).  
Determine best trading strategy using Machine Learning and trading technical indicator for S&P 500.
We are trying to train a model to predict which indicators best predict index prices?

What is the machine learning component predicting?
Predicting how price interacts with technical indicator (EMA)
Testing models to maximise indicator performance
What is the feature set? Prediction set? 
Feature set: date, high, low, open, close
Prediction set: indicator crossing EMA 30

What are our approaches?
Timeframe data is based on weekly high, low close and open from 2006. 
To outperform the index due to the ability to execute both long and short trades


Stretch:
What are we trying to solve? 
To outcompete the profitability and risk of the S&P 500 using the Sharpe Ratio, sortino ratio. 
Determine best trading strategy using Machine Learning and trading technical indicators for S&P 500, DOW30, NASDAQ 100.
We are trying to train a model to predict which indicators best predict index prices?
Goal is to outperform indice performance due to long and short trading ability. 

What is the machine learning component predicting?
Predicting how price interacts with technical indicators (EMA, MACD, Bollinger Bands & Stochastics)
What other ML libs would you use? Know how to apply it (FB prophet, Kera, tensorflow, sklearn)

What are our approaches?
MACD, Bollinger Bands & Stochastics 
Ensemble method classifier 
Optimise weightings between 3 indices (if time permits)
Lexbot, recommend trading strategy based on different measures (min loss, max prof)
  
  Actual Results
  
  ![](https://github.com/Danny-M108/Challenge-Two-/blob/main/Actual_vs_model_cumprod_of_returns.png)
  
  
  
  
  
  
  
  
  
  
  
  
  

MEMBERS:
Henry Date
Danny Milsom
Ling Dong
Brendan Van Maanen
Akhil Kavuri

PROPOSED DATA SETS:
Alpaca Finance , pandas, numpy, pathlib, hvplot, Ensemble, sklearn, SVC classifier


BREAKDOWN ALLOCATION:
Project Manager: 		Brendan
GitMaster:			Henry
Code development:		All
Interface: 		Henry, Akhil, Danny M, Danny L
Lexbot			Danny L
Back end code: 		Henry, Akhil, Danny M, Danny L
Quality Assurance:		Brendan

  
  Target: 

What are we trying to solve? 


What is the machine learning component predicting?
Predicting how price interacts with technical indicator (EMA)
Testing models to maximise indicator performance
What is the feature set? Prediction set? 
Feature set: date, high, low, open, close
Prediction set: indicator crossing EMA 30

What are our approaches?
Timeframe data is based on weekly high, low close and open from 2006. 
To outperform the index due to the ability to execute both long and short trades


Stretch:
What are we trying to solve? 
To outcompete the profitability and risk of the S&P 500 using the Sharpe Ratio, sortino ratio. 
Determine best trading strategy using Machine Learning and trading technical indicators for S&P 500, DOW30, NASDAQ 100.
We are trying to train a model to predict which indicators best predict index prices?
Goal is to outperform indice performance due to long and short trading ability. 

What is the machine learning component predicting?
Predicting how price interacts with technical indicators (EMA, MACD, Bollinger Bands & Stochastics)
What other ML libs would you use? Know how to apply it (FB prophet, Kera, tensorflow, sklearn)

What are our approaches?
MACD, Bollinger Bands & Stochastics 
Ensemble method classifier 
Optimise weightings between 3 indices (if time permits)
Lexbot, recommend trading strategy based on different measures (min loss, max prof)










