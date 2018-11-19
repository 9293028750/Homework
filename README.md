# Midterm question SAMPLE for the class DSE-I1020 (Intro to Data Science) 
## Multiple choice concept questions
1. What is Not the technique for Machine Learning?
    - a. Supervised learning
    - b. Intelligent learning
    - c. Deep Learing
    - d. Reinforcement learning
Answer: (b)

2. Here is a Set s ={23, 2, 8}. What may be the result after operating s.add(8)?
    * a. {23, 2, 8, 8}
    * b. {8, 23, 2, 8,}
    * c. {23, 8, 2}
    * d. {23, 2}
Answer: (c)

3. What is Not the appropriate situation for applying Tuples?
    * a. Useful when you wan to provide information that cannot be changed
    * b. Stores unique dates
    * c. Most extreme case since structure has no function
    * d. Supports iterration, indexing, contains
Answer: (d)

4. Bayes theorem is often used to?
    * a. compute P(A|B) when P(A) and P(B) are known
    * b. relate P(A|B) to P(B|A)
    * c. compute P(A,B) from P(C)
    * d. relate P(A,B) to P(C)
Answer: (b)

5. What is Not the functions of Explanatory Data Visualization?
    * a. Having an understanding of the data outcome
    * b. Communicate data outcome to clients
    * c. Particularly useful for data scientists
    * d. Make data looks tidy
Answer: (d)

6. Time series analysis basic statistic model are great at
    * a. recognizing a trend
    * b. evaluating the performance of model
    * c. predicting the next value in a series
    * d. captureing the periodic pattens
Answer: (a)

7. What is most important for data stroytelling?
    * a. Elaborate explanation
    * b. Emotional connection
    * c. Unbiased statement
    * d. Clear data visualization
Answer: (b)

8. Vector Data GIS data is best for storing?
    * a. Points, Circle and Rectangle
    * b. Points, Lines and Circle
    * c. Points, Lines and Rectangle
    * d. Points, Lines and regional polygons
Answer: (d)
## True-false choice 
1. Data visualization is the mouthpiece of the data. 
    * a. True 
    * b. False
Answer: a

2. Statistical Time series analysis can predict black swans. 
    * a. True 
    * b. False
Answer: b （It can't predict black swans）

3. Google's alpha go beat the Go champion using supervised learning. 
    * a. True 
    * b. False
Answer: b (using Reinforcement learning)

4. To master the art of data analysis, you need to a good story teller and EDV helps you achive taht. 
    * a. True 
    * b. False
Answer: a

5. Supervised learning finds patterns in data. Unsupervised learning finds patterns for a prediction task.
    * a. True 
    * b. False
Answer: b (It would be right if exchanging the subject of the two sentence)

6. Neural networks account for interactions really well. 
    * a. True 
    * b. False
Answer: a
    
7. Machine learning can give computers the ability to learn to make decisions from data. 
    * a. True 
    * b. False
Answer: a
## Short-answer DataCamp-styled Notebook questions 
```
# Import what we need
import requests
from bs4 import BeautifulSoup
import nltk


# the e-book url of Alice's Adventures in Wonderland
url = "http://www.gutenberg.org/files/11/11-h/11-h.htm"

# Part 1 Getting the HTML of Alice's Adventures in Wonderland  
respond = ----------------------

# Part 2 Setting the correct text encoding of the HTML page
----------------------

# Part 3 Extracting the HTML from the request object
html = ----------------------

# Part 4 Creating a BeautifulSoup object from the HTML
soup = ----------------------

# Part 5 Getting the text out of the soup
text = ----------------------

#Part 7 Creating a tokenizer
tokenizer = ----------------------

#Part 7 Tokenizing the text
tokens = ----------------------

#Part 8 Printing out the first 10 words / tokens 
----------------------
```

Answer:
```
# Import what we need
import requests
from bs4 import BeautifulSoup
import nltk

# Part 1 Getting the HTML of Alice's Adventures in Wonderland  
respond = requests.get("http://www.gutenberg.org/files/11/11-h/11-h.htm")

# Part 2 Setting the correct text encoding of the HTML page
respond.encoding = 'utf-8'

# Part 3 Extracting the HTML from the request object
html = respond.text

# Part 4 Creating a BeautifulSoup object from the HTML
soup = BeautifulSoup(html)

# Part 5 Getting the text out of the soup
text = soup.text

#Part 7 Creating a tokenizer
tokenizer = nltk.tokenize.RegexpTokenizer('\w+')

#Part 7 Tokenizing the text
tokens = tokenizer.tokenize(text)

#Part 8 Printing out the first 8 words / tokens 
print(tokens[:10])
## Mini task on dataset (total: 1)
Load the Boston Dataset in Sklearn. Creating LinearRegression to fit feature and price of house.

Using the LinearRegression with features of house in Boston Dataset to predict price of house.

Print the scatter of actual price and predict price. It should look like this:
```
## Mini task on dataset 
<p> Load the Boston Dataset in Sklearn. Creating LinearRegression to fit feature and price of house. Using the LinearRegression with features of house in Boston Dataset to predict price of house. Print the scatter of actual price and predict price. It should look like this: </p>

Answer:
```
import matplotlib.pyplot as plt
from sklearn.datasets import load_boston
from sklearn.linear_model import LinearRegression
import pandas as pd

# Load the boston data base 
boston = load_boston()

bos = pd.DataFrame(boston.data)
bos.columns = boston.feature_names
bos['Price'] = boston.target

lm = LinearRegression()
X = bos.iloc[:,0:-1]
y_actual = bos.iloc[:,-1]
lm.fit(X,  y_actual)
y_pred = lm.predict(X)


plt.scatter(y_actual, y_pred)
plt.xlabel("actual price")
plt.ylabel("predicted price")
plt.show()
```
