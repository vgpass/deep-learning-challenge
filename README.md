# deep-learning-challenge
# Module 21 Challenge - UCI Data Analytics Bootcamp

### **Vincent Passanisi**

### **Due March 20, 2023**

<br></br>

### *Complete Challenge Analysis Report ca be found here:*
[**COMPLETED ALPHABET SOUP CHARITY ANALYSIS**](https://github.com/vgpass/deep-learning-challenge/blob/main/AlphabetSoupCharityAnalysis.md)

# ***INTRODUCTION***

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

<br></br>

# ***REPOSITORY FILES***

**README.md** - ReadMe file for the deep-learning challenge repo

[**AlphabetSoupCharityAnalysis**](https://github.com/vgpass/deep-learning-challenge/blob/main/AlphabetSoupCharityAnalysis.md) - Analysis report for Alphabet Soup Charities' Deep Learning Model

**Deep_Learning_Challenge** folder - contains the deep learning Jupityr notebooks for the initial model and optimizations, as well as the resource and images folders

        * *AlphabetSoupCharity_Complete.ipynb* - first deep learning model attempt with the charity data
        * *AlphabetSoupCharity_Optimization.ipynb* - model optimization - first attempt
        * *AlphabetSoupCharity_Optimization_2.ipynb* - model optimization - second attempt
        * *AlphabetSoupCharity_Optimization_3.ipynb* - model optimization - third attempt
        * *AlphabetSoupCharity_Optimization_4.ipynb* - model optimization - fourth attempt
        * *AlphabetSoupCharity_Optimization_5.ipynb* - model optimization - fifth attempt

**Output Files of Best Model from Tuner**

        * AlphabetSoupCharity.h5
        * AlphabetSoupCharity_Optimization.h5
        * AlphabetSoupCharity_Optimization_2.h5
        * AlphabetSoupCharity_Optimization_3.h5
        * AlphabetSoupCharity_Optimization_4.h5
        * AlphabetSoupCharity_Optimization_5.h5

**Resources** folder - contains the *charity_data.csv* file.

**images** folder - contains the images used in the analysis report.
<br></br>

# **Comments and Thoughts**

Most remarkable to me in attempting this homework challenge is the amount of comfort I am starting to feel with pandas dataframes. I really started to enjoy manipulating the columns, and binning various groups of information. The experimentations was fun if not profitable. I wasn't able to acheive the 75% accuracy desired for the model, but I made several attempts. Only five of which appear in my repo. Many more were attempted but with poor results.

I'm still doing a great deal more learning to try to understand the different types of models and what all the analysis means. It is still something of a 'mystery box' to me, but I'm sure with more study and reading, it will start to make greater sense. One thing that is becoming apparent in these later challenges is the amount of effort needed to accurately explain the results of the analysis. It's no longer enough to be able to produce a successful result. One needs to be able to explain the results to the desired audience, whether these be corporate executives, fellow data analysist, or sometimes the general public. I actually spent much more time trying to understand my results and write about them coherently than I did to actually produce the analysis in the first place.

It will be curious to see how this changes now with the availability of LLMs that could potentially help data analysts create content suited to their audience that clearly explains complex ideas in ways they were not able to create themselves.
