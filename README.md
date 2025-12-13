# twitter-airline-sentiment-analysis
Twitter airline sentiment analysis from kaggle dataset

## Key Findings of EDA
- Puctuation wont be removed other than the #loremipsum or @someone
- Maximum word length is around 35-40 words per tweet
- Dataset is very imbalanced favoring negative reviews

## Decisions for Baseline Model
- Baseline Model would have a max length of 40 or 50
- Random Udersampling would be applied to balanced the data