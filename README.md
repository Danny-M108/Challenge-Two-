![](Trading%20Wizard.jpg)
# <div align = "center"> Challenge-Two
## <div align = "center"> Team Two
### <div align = "center"> Akhil Kavuri, Brendan Van Maaneen, Danny Milsom, Henry Date and Ling Dong
#### <div align = "center"> *AN INTERACTIVE TRADING & INVESTEMENT MACHINE BOT*

## 1. Project Aim:   
To build an interactive and intuitive trading BOT that optimises techical indicators through machine learning (Ensemble Technique) to provide highly accurate investment and trading recommendations. Importantly the BOT is to reliablely predict how price interacts with technical indicators (EMA) in order to maximise indicator trading performance.   
To allow for a high degree of "fine tuning" the BOT model relied up the Ensemble Technique 
  
  
***To utilise machine learning to outcompete the profitability and risk of the S&P 500 (Sharpe Ratio).  
Determine best trading strategy using Machine Learning and trading technical indicator for S&P 500.
We are trying to train a model to predict which indicators best predict index prices?**

  
## 2. Key Technologies:
  
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
 
    

  ## 3. Key Technology Installations: 
  
  ### 3.1 Importing required libraries
  
      Installing Yahoo Finance  
      !pip install yfinance  
      !pip install pandas_datareader  
      !pip install scikeras  
      !pip install imbalanced-learn  
      !pip install xgboost  
   
  ### 3.2 Creating the feature variables
  
     'def calculated_features(df):
        df['aboveEMA50'] = np.where(df['Close'] > df['EMA50'], 1, 0)
        df['aboveEMA100'] = np.where(df['Close'] > df['EMA100'], 1, 0)
        df['aboveupperBB'] = np.where(df['Close'] > df['upperBB'], 1, 0)
        df['belowlowerBB'] = np.where(df['Close'] < df['lowerBB'], 1, 0)
        df['oversoldRSI'] = np.where(df['nor_RSI'] < 0.30, 1, 0)
        df['overboughtRSI'] = np.where(df['nor_RSI'] > 0.70, 1, 0)
        return df'
      
  ### 3.3 Creating Ensemble   
  
     from sklearn.metrics import log_loss  
     clf1 = LogisticRegression(random_state=1)  
     #clf2 = RandomForestClassifier(n_estimators=50, random_state=1)  
     clf3 = GaussianNB()  
     clf2 = XGBClassifier()  
     eclf = VotingClassifier(estimators=[('lr', clf1), ('xgb', clf2), ('gnb', clf3)],voting='hard')  

     eclf.fit(X_train, y_train)
 
     # predicting the output on the test dataset
     pred_final = eclf.predict(X_test)
 
     # printing log loss between actual and predicted value
     print("The accuracy of the model in percentage is",(accuracy_score(y_test, pred_final)*100))  
    
     The accuracy of the model in percentage is 85.42445274959958  
  
  ### 3.4 Normalising the data using Standard Scaler
  
     # Create a StandardScaler instance
     scaler = StandardScaler()

     # Fit the scaler to the features training dataset
     X_scaler = scaler.fit(X_train)

     # Scale both the training and testing data from the features dataset
     X_train_scaled = X_scaler.transform(X_train)
     X_test_scaled = X_scaler.transform(X_test)

     # encoding class labels as integers
     encoder = LabelEncoder()
     encoder.fit(y_train)
     encoded_Y = encoder.transform(y_train)
  
  ### 3.5 Adding Layers to Neural Network
  
      def create_model():
	    # create model
	    model = Sequential()
	    model.add(Dropout(0.2, input_shape=(21,)))
	    model.add(Dense(10, activation='relu', kernel_constraint=MaxNorm(3)))
	    model.add(Dense(5, activation='relu', kernel_constraint=MaxNorm(3)))
	    model.add(Dense(1, activation='sigmoid'))
	    # Compile model
	    sgd = SGD(learning_rate=0.1, momentum=0.9)
	    model.compile(loss='binary_crossentropy', optimizer=sgd, metrics=['accuracy'])
	    return model
  
  ### 3.6 Creating Ensemble   
  
      from sklearn.metrics import log_loss  
      clf1 = LogisticRegression(random_state=1)  
      #clf2 = RandomForestClassifier(n_estimators=50, random_state=1)  
      clf3 = GaussianNB()  
      clf2 = XGBClassifier()  
      eclf = VotingClassifier(estimators=[('lr', clf1), ('xgb', clf2), ('gnb', clf3)],voting='hard')  

      eclf.fit(X_train, y_train)
 
     # predicting the output on the test dataset
     pred_final = eclf.predict(X_test)
 
     # printing log loss between actual and predicted value
     print("The accuracy of the model in percentage is",(accuracy_score(y_test, pred_final)*100))  
    
     The accuracy of the model in percentage is 85.42445274959958  
  
  ## 4. Key Output Examples:

   ### 4.1 Actual Results
  
  ![](https://github.com/Danny-M108/Challenge-Two-/blob/main/Actual_vs_model_cumprod_of_returns.png)
	
  
  Code is well commented with concise, relevant notes. (5 points)
GitHub README file includes a concise project overview. (2 points)
GitHub README file includes detailed usage and installation instructions. (3 points)
GitHub README includes either examples of the application, or the results and a summary of the analysis. (5 points)
  
  
  
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
  
  
  
  
  
  
    c. Optimise weightings between 3 indices (if time permits).
  
  

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










