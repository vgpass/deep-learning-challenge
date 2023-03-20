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

*First Attempt*

As stated above, the first attempt chose the *IS_SUCCESFUL* parameter as the target variable. The remaining columns of the dataset were kept as features with some modification. Both *application type* and *classification* were regrouped as discussed below in order to categorize "rare" variables, also referred to as outliers. As seen below, there were a couple of categories that had a limited number of organizations. It was the goal of the team to reduce these inputs to 10 and so created a broader category called *Other* to identify these groups.

![Unique number of featurest](images/nunique.png)

* First, any applicaation types that had less than 700 organizations were reclassified as **other**.
* Second, any classification types with less than 1000 organizations were reclassified as **other**.
* Finally, all non-numerical data was converted into binary in order to run the model.

Because of the large number of features involved, a rectified linear unit (ReLU) function was chosen with two(2) hidden layers and eight(8) neurons each. A sigmoid function was used for the output. The model is displayed below.

![model one](images/model1.png)

The model produced an accuracy of 72.3%, below the required threshhold for the analysis, but close enough to warrant an attempt at optimizing the model. 

* 536/536 - 0s - loss: 0.5578 - accuracy: 0.7232 - 336ms/epoch - 628us/step
Loss: 0.5577878952026367, Accuracy: 0.7232069969177246

## ***SUMMARY***