step1:First to download the Dataset from ##Dataset url: https://grouplens.org/datasets/movielens/latest/
Step2:We have two dataset Movies and Credit dataset and merge both dataset based on the movieId which are commonly present in the movies and credit dataset.
step3:Remove Missing Values
Group by Movie Title and Count Ratings.
why we are doing Group by Movie Title and Count Ratings?
Identify Popular Movies:
By counting the number of ratings each movie has received, you can identify which movies are more popular or widely rated. This information can be useful for various analytical purposes, such as recommending popular movies to new users.

step4:Make the pivot table
why we made?
Create User-Item Matrices: Organize data where rows are users, columns are items, and cells contain ratings or interactions.
Handle Sparse Data: Efficiently manage large datasets with many missing values.
Aggregate Data: Summarize data for easy computation of statistics like mean ratings.
prepare for Algorithms: Essential for collaborative filtering and matrix factorization techniques.

step5:Converting the DataFrame to a CSR (Compressed Sparse Row) matrix before fitting the NearestNeighbors model is important for several reasons:

Memory Efficiency Sparse Data Handling: Many recommendation systems deal with sparse data where most of the entries are zeros. Storing and processing such data in a dense format (standard DataFrame or NumPy array) would consume a lot of memory unnecessarily. CSR Matrix: This format only stores non-zero entries and their indices, reducing memory usage significantly.

step6:
initializes a nearest neighbors model with cosine similarity as the distance metric and brute-force algorithm for computation. It then fits the model to a sparse matrix containing movie features, enabling it to find similar movies based on their characteristics.

step7:
1:Select a Random Movie:
2:Find Nearest Neighbors:
  movie_features_df.iloc[query_index, :]:
This selects the row corresponding to the randomly chosen movie (using query_index).
.values.reshape(1, -1):
Converts the selected row (which is a 1D array) to a 2D array with shape (1, number_of_features). This is necessary because the kneighbors method expects a 2D array.
model_knn.kneighbors(..., n_neighbors=6):
Finds the 6 nearest neighbors (including the movie itself) for the selected movie.
distances: An array containing the distances to each of the 6 nearest neighbors.
indices: An array containing the indices of the 6 nearest neighbors.

steps 8:
        Give one move it recommend the 5 movies.