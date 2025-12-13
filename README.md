# Twitter Airline Sentiment Analysis

The data is taken from [![Static Badge](https://img.shields.io/badge/Twitter_Airline_Sentiment-black?logo=kaggle&logoColor=white&logoSize=auto&color=blue)](https://www.kaggle.com/datasets/crowdflower/twitter-airline-sentiment)

## Key Findings of EDA
- Puctuation wont be removed other than the #loremipsum or @someone
- Maximum word length is around 35-40 words per tweet
- Dataset is very imbalanced favoring negative reviews

## Decisions for Baseline Model
- Baseline Model would have a max length of 40 or 50 tokens
- Random Udersampling would be applied to balanced the data
- Optimizer using Adamw with a learning rate of 5e-4 for fast training
- 3 epochs since this is a pretrained model

## Parameters That are Fine-Tuned
- Learning Rate to `5e-5`
    - Slower learning rate
- Optimizer to Adam
- max_length to `256`
    - So the model can have more tokens to understand context
- batch size to `16`
    - A balance between memory usage and effeciency

## Training Results
| Data | Model | Weighted Precision | Weighted Recall | Weighted F1 Score |
| ---- | ----- | ------------------ | --------------- | ----------------- |
| Balanced | DistillBERT | 0.40 | 0.20 | 0.07 |
| Balanced | DistillBERT (fine-tuned) | 0.82 | 0.79 | 0.80 |
| Balanced |  Albert-base-v2 | 0.41 | 0.64 | 0.50 |
| Balanced | Albert-base-v2 (fine-tuned) | 0.83 | 0.77 | 0.79 |
| Imbalanced | DistillBERT | 0.41 | 0.64 | 0.50 |
| Imbalanced | DistillBERT (fine-tuned) | 0.82 | 0.83 | 0.82 |
| Imbalanced |  Albert-base-v2 | 0.42 | 0.64 | 0.50 |
| <b style="color:green">Imbalanced</b> | <b style="color:green">Albert-base-v2 (fine-tuned)</b> | <b style="color:green">0.84</b> | <b style="color:green">0.84</b> | <b style="color:green">0.84</b> |

**Result Analysis**:
- Interestingly the `Albert-base-v2 (fine-tuned)` model is the best so far in classifiying sentiment from tweets
- Reasons Albert outperformed DistillBERT:
    - DistillBERT focuses on **effeciency** due to the BERT model is reduced **40%** which makes training and inferencing faster.
    - Albert focuses on **Parameter Effeciency** which results in a model with fewer parameters than a simmilar sized BERT model. 