# **Deep Learning Model Analysis - Alphabet Soup Charity**

**UCI Data Analytics Bootcamp**

**Vincent Passanisi**

**March 20, 2023**

## ***OVERVIEW***

The nonprofit foundation Alphabet Soup funds a variety of ventures across numerous classifications ranging from private to public, company-funded to independent, and with a wide range of income needs. Some of these organizations have income in the billions or dollars, others are pure-nonprofits with no income at all. Some are looking for small grant amounts and others are funding product development in the billions of dollars.

The foundation has had mixed results over the years and is looking for a way to better select the organizations with the best chance of success in meeting their fundraising goals. The Alphabet Soup business team has a dataset that contains more than 34,000 organizations that have received funding in the past and identifies whether they have been successful or not. The team has decided to use machine learning and neural networks to analyze the features in the data and create a binary classifier that seeks to predict whether applicants will be succesful if funded by Alphabet Soup.

The metadata in our possession has the following features.

* EIN and NAME—Identification columns
* APPLICATION_TYPE—Alphabet Soup application type
* AFFILIATION—Affiliated sector of industry
* CLASSIFICATION—Government organization classification
* USE_CASE—Use case for funding
* ORGANIZATION—Organization type
* STATUS—Active status
* INCOME_AMT—Income classification
* SPECIAL_CONSIDERATIONS—Special considerations for application
* ASK_AMT—Funding amount requested
* IS_SUCCESSFUL—Was the money used effectively

#### **Objective**

The objective of this analysis is to build a model with an accuracy goal of more than 75% that will predict whether or not an organization will be successrul in its fundraising attempts.

#### **Assumptions**

In cleaning and preparing the data provided, many assumptions had to be made, as well as decisions regarding what was useful and what was not. The first order of business was deciding what features would be analyzed and against what metric. Of the features, decisions needed to be made whether to categorize certain classifications into categories. The target variable was decided to be the *IS_SUCCESSFUL* column. The team unanimously agreed that this was the reason for the entire project in the first place. In the initial model training and analysis of the model, it was decided to use all remaining features available, but with some modifications to "bin" (or group) outliers into larger groups to minimize their impact in the analysis. More information will be provided below in the *Results* section of this analysis.

## ***RESULTS***

***First Attempt***

As stated above, the first attempt chose the *IS_SUCCESFUL* parameter as the target variable. The remaining columns of the dataset were kept as features with some modification. Both *application type* and *classification* were regrouped as discussed below in order to categorize "rare" variables, also referred to as outliers. As seen below, there were a couple of categories that had a limited number of organizations. It was the goal of the team to reduce these inputs to 10 and so created a broader category called *Other* to identify these groups.

![Alt text](Deep_Learning_Challenge/images/nunique.png)

* First, any applicaation types that had less than 700 organizations were reclassified as **other**.
* Second, any classification types with less than 1000 organizations were reclassified as **other**.
* Finally, all non-numerical data was converted into binary in order to run the model.

Because of the large number of features involved, a rectified linear unit (ReLU) function was chosen with two(2) hidden layers and eight(8) neurons each. A sigmoid function was used for the output. The model is displayed below.
<br></br>

![Alt text](Deep_Learning_Challenge/images/model1.png)

The model produced an accuracy of 72.7%, below the required threshold for the analysis, but close enough to warrant an attempt at optimizing the model. 

* 536/536 - 0s - loss: 0.5592 - accuracy: 0.7273 - 463ms/epoch - 865us/step
Loss: 0.559209406375885, Accuracy: 0.7273469567298889

***Optimization***

We then attempted to optimize the model several times in order to acheive a target predictive accuracy greater than 75%. The initial attempt used the same target and feature variables that were used in the first attempt. However, this model was trained using Keras Tuner in order to evaluate which model could potentially yield better results. The Keras tuner resulted in a model with three hidden layers with 3, 7, and 1 neurons respectively.

![Alt text](Deep_Learning_Challenge/images/first_opt.png)

Although, the model yielded a slight improvement with 73.9% accuracy, this still fell below the threshold value of 75%.

![Alt text](Deep_Learning_Challenge/images/first_opt_model.png)

***Optimization - Subsequent Attempts***

Because of the lack of success using the Keras tuner, it was decided to modify the features being used to train the model. Columns were dropped or binned to account for rare occurences. Different binning strategies were used to see if a better result could be acheived. All attempts are summarized below, but it will be noted that none of them met the 75% threshold.
<br></br>

* ***Attempt #2***

    In this attempt, the following columns were dropped: 'STATUS', 'USE_CASE', 'AFFILIATION', 'SPECIAL_CONSIDERATIONS'. In addition, any `ask amounts` above $190,000 were dropped from the data frame, and the remaining amounts were binned into 6 categories.

    This model failed with an accuracy of just over **64%**.
    
    * 77/77 - 0s - loss: 0.6514 - accuracy: 0.6401 - 151ms/epoch - 2ms/step
    * Loss: 0.6514246463775635, Accuracy: 0.6401312947273254
<br></br>

* ***Attempt #3***

    In this attempt, the following columns were dropped: 'STATUS', 'SPECIAL_CONSIDERATIONS', 'INCOME_AMT'. In addition, any `ask amounts` above one million dollars were dropped from the data frame, and the remaining amounts were binned into 6 categories.

    This model also failed with an accuracy of **73%**.
    
    * 512/512 - 0s - loss: 0.5791 - accuracy: 0.7303 - 340ms/epoch - 664us/step
    * Loss: 0.5790629386901855, Accuracy: 0.7303343415260315
<br></br>

* ***Attempt #4***

    In this iteration only the 'STATUS' column was dropped. We felt that column was statistically insignificant since only five organizations had a `0` status. In addition, any `ask amounts` above $150 billion were dropped from the data frame. Both CLASSIFICATIONS and APPLICATION TYPES were reduced to four bins.

    This model failed with an accuracy of **72.0%**.
    
    * 535/535 - 1s - loss: 0.5743 - accuracy: 0.7200 - 693ms/epoch - 1ms/step
    * Loss: 0.5743011832237244, Accuracy: 0.7200140357017517
<br></br>

* ***Attempt #5***

    In this attempt, the following columns were dropped: 'STATUS', 'SPECIAL_CONSIDERATIONS', 'ASK_AMT', 'CLASSIFICATION'. In addition, Organization Types were binned into only two categories: T3 and Other.

    This model failed with an accuracy of **70.2%**
    
    * 536/536 - 0s - loss: 0.5999 - accuracy: 0.7017 - 452ms/epoch - 843us/step
    * Loss: 0.5999064445495605, Accuracy: 0.7016909718513489  


## ***SUMMARY***

Unfortunately, the Alphabet Soup Business Team was unsuccessful in it's attempt to create a deep learning model that it could use to help predict which organizations will be successful in their fundraising attempts. The five optimization models discussed in this report were the best of many attempts, yet all fell short of the 75% threshold that was the objective of this analysis.

Several next steps should be considered.

1. Current data being collected as features should be reconsidered if these are not helpful in creating a model. Just because certain data is easy to measure, collect, and monitor, does not mean that this information is useful in predicting an organization's success. Other features should be considered and tested to see what their predictive power might be. A short list of possibilities could be as follow, though should not be considered the only options.

    * Number of employees in the organization.
    * Amount spent on advertising in the campaign.
    * Annual marketing budget of the organization.
    * Location of the organization.
    * Management style of the organization, i.e. top-down or bottom-up.
    * Types of media used to conduct the campaign.

2. The second step that should be considered is using a different model to train and test the data. There are ensemble models, transfer learning, and others. In addition, other optimization algorithms might be attampted such as Adam, RMSprop, or Adagrad. Ensemble models are a way of combining multiple models through various methods such as bagging, where random data points can be selected more than once. Transfer Learning is a technique where the outputs of a model are used to further train a model. Certain learned features can be applied to the next training set and the weights fine-tuned to improve accuracy. These techniques can improve accuracy and sometimes speed up the performance of the model.

In conclusion, although the attempts were unsuccessful, much important information was obtained in the process. These 'lessons' could be used to create more predictive models in the future and could acheive the goal of Alphabet Soup to create a worthwhile tool to increase the foundations effectiveness in supporting charities.