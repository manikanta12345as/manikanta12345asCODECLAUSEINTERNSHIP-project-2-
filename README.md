![image](https://github.com/manikanta12345as/manikanta12345asCODECLAUSEINTERNSHIP-project-2-/assets/114325875/14f28484-ce09-4bab-8394-92e6a1d7947a)

1. Install and Import Dependencies
!pip install torch==1.8.1+cu111 torchvision==e.9.1+cu111
! pip install transformers requests beautifulsoup4 pandas numpy
• =e.8.1
-f https://download.pytorch.org/whl/torch_stablc
from transformers import AutoTokenizer, AutoMode1ForSequenceC1assification
import torch
import requests
from bs4 import BeautifulSoup
import re
2. Instantiate Model
tokenizer = AutoTokenizer.from_pretrained( 'nlptown/bert-base-multilingual-uncased-sentiment ' )
model = 'nlptown/bert-base-multilingual-uncased-sentiment')
3. Encode and Calculate Sentiment
tokens
result
= tokenizer. encode( 'It was good but couldve been better. Great' ,
= model (tokens)
return tensors= )
result . logits
int(torch. argmax(result. logits)
4. Collect Reviews
= requests . get( ' https://www.yelp. com/biz/social-brew-cafe-pyrmont ' )
= BeautifulSoup(r.text,
'html.parser')
soup
= re. compile(
' . *comment. *'
regex
{'class' : regex})
results
reviews
= [result. text for result in results]
reviews
5. Load Reviews into DataFrame and Score
import numpy as np
import pandas as pd
pd reviews)
df[ ' review' ] .i10c[0]
def sentiment_score(review) :
' review' ] )
tokens = tokenizer. encode(review, return tensors='pt )
= model (tokens)
result
return int(torch.argmax(result.logits))+l
sentiment_score(df[ ' review' ] . iloc[l] )
'sentiment'] =
df[ ' review'
' review' ] . apply(lambda x:
sentiment_score(x[ : 512] ) )
