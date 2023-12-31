# User Similarity basen on Jaccard Similarity, Min Hshing and LSH 

*Data Mining*  
*MSc in Data Science, Department of Informatics*  
*Athens University of Economics and Business*

## *Introduction*

- **Jaccard Similarity**
  - Jaccard Similarity is a measure of similarity between two sets.
  - It is defined as the size of the intersection divided by the size of the union of the sets.

- **MinHashing**
  - MinHashing is a technique used to estimate Jaccard Similarity efficiently, especially for large datasets.
  - It involves creating a compact signature for each set using hash functions, selecting the minimum hash value for each hash function.
 
- **Locality-Sensitive Hashing (LSH)**
  - LSH is a technique used to identify pairs of similar items efficiently, often applied in conjunction with MinHashing.
  - It involves hashing items in a way that similar items have a higher probability of colliding in the hash space.

- **Usage Scenarios**
    - Recommendation Systems
    - Genomic Sequence Analysis
    - Image Similarity
    - Social Network Analysis

## *Data*

- We will use the movieLens dataset.
- The dataset pertains to movie ratings provided by users.
- It comprises 100,000 ratings (1-5) from 943 users on 1682 movies.
- Each user has rated a minimum of 20 movies.
- The dataset is distributed across three files: users.txt, movies.txt, and ratings.txt.
  - users.txt: Contains id, age, gender, occupation, and postcode separated by |.
  - movies.txt: Includes id, title (with release year), and additional unrelated information separated by |.
  - ratings.txt: Tab-separated file containing userid, movieid, rating (1-5), and timestamp.
- For this assignment, only the set of movies that a user has rated will be used, excluding the ratings themselves.

 
## *Project Overview*

1. **Compute Exact Jaccard Similarity:**
   - Compute the exact Jaccard Similarity for all user pairs.
   - Output pairs with a similarity score of at least 0.5.
   - Identify the most similar user pair and list the common movie titles they've seen.

2. **Compute Similarity using Min-Hash Signatures:**
   - Use Min-Hash signatures with hash functions ha,b(x) = (ax+b) mod R.
   - Evaluate with 50, 100, and 200 hash functions.
   - Output pairs of users with estimated similarity ≥ 0.5.
   - Report false positives and false negatives over 5 runs.
   - Analyze the impact of the number of hash functions on false positives and negatives.

3. **Locate Similar Users using LSH Index:**
   - Implement Locality Sensitive Hashing with 200 hash functions.
   - Break up signatures into bands with r hash functions per band.
   - Use two LSH instances: (a) b = 25, r = 8 and (b) b = 40, r = 5.
   - Find user pairs with similarity ≥ 0.5 and report true positives.
   - Report the number of similarity evaluations using initial representations.
   - Average results over 5 runs with different functions.
