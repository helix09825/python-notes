

## 1. NumPy

numpy pandas matplotlib seaborn scikit-learn
https://s3.amazonaws.com/assets.datacamp.com/blog_assets/Numpy_Python_Cheat_Sheet.pdf

https://github.com/rougier/numpy-100/blob/master/100_Numpy_exercises.ipynb

https://github.com/matplotlib/cheatsheets

Narysuj wykres dla sin i cos w zakresie od -2* pi do 2*pi; używaj różnych markerów;

https://pandas.pydata.org/docs/user_guide/10min.html

https://colab.research.google.com/drive/1YdKPGHID4k2ghKZapwh29g5IF7-yFOjb?usp=sharing

https://media.datacamp.com/legacy/image/upload/v1676302204/Marketing/Blog/Pandas_Cheat_Sheet.pdf

https://s3.studylib.net/store/data/025268801_1-1bb4205c74b96358224e9e1be6dbfbda.png

import pandas as pd

data = {

   "OrderID": [1001, 1002, 1003, 1004, 1005, 1006],

   "Customer": ["Alice", "Bob", "Alice", "Derek", "Eve", "Bob"],

   "Product": ["Laptop", "Monitor", "Mouse", "Laptop", "Mouse", "Monitor"],

   "Quantity": [1, 2, 3, 1, 2, 1],

   "Price": [1200, 300, 25, 1200, 25, 300],

   "Date": pd.to_datetime([

       "2024-05-01", "2024-05-03", "2024-05-04", 

       "2024-05-05", "2024-05-06", "2024-05-06"

   ])

}

df = pd.DataFrame(data) I**nspect the dataset**

- Display the first few rows.
- Print summary statistics.

**Add a new column** called Total which is Quantity * Price.

**Group by Customer**

- Show total sales per customer.
- Show average order value per customer.

**Find the best-selling product** by total quantity sold.

**Filter the data**

- Show only orders placed after "2024-05-03".

**Sort the dataset**

- Sort by Total in descending order.

**Create a pivot table**

- Show total revenue per product per day.

https://www.kaggle.com/datasets

https://colab.research.google.com/drive/1SkOGcCWT0B656quQyViv0GA3F-rxwzVG?usp=sharing












