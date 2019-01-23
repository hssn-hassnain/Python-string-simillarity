# Python-string-simillarity
String Similarity

*prerequisite
-Setup JupyterLab.
-Install Levenshtein libraray

*Steps to string similarity.

1- In JupyterLab Import Pandas data frame

   import pandas as pd

2- Import Levenshtein libraray.

   import Levenshtein

3- Load the CSV file.

   df=pd.read_csv('C:\\Users\\iTranscend\\Desktop\\text-similarity\\train.csv')

4- DataFrame holding the first n rows of df.

   df.head()

5- Show only the description x and description y.

   df=df[['description_x','description_y']]

6- DataFrame holding the first n rows of df only the string values

   df.head()

7- Check the similarity.

    df['similarity'] = df.apply(lambda x : Levenshtein.distance(df['description_x'], df['description_y']), axis=1)
   similarity = []
   for i in range(df.shape[0]):
   similarity.append(1/(1+Levenshtein.distance(df['description_x'][i], df['description_y'][i])))
   df['similarity']= similarity
   
8- Reverse lookup and DataFrame holding the first n rows of df similarity.

   df['similarity'] = (df['similarity'] - df['similarity'].min())/(df['similarity'].max() - df['similarity'].min())
   df.head() 

9- export the string similarity file in CSV format

   df.to_csv('String_similarity.csv')

GitHub directory
https://github.com/hssn-hassnain/Python-string-simillarity.git                