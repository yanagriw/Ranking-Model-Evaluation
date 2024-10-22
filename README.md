# Ranking Model Evaluation

## Dataset Overview

The dataset contains simplified data simulating Search Everywhere usage, 
where each row represents a lookup or state of the SE window at a particular moment. 
Given this data, we aim to evaluate the performance of a ranking model that predicts 
relevant search results based on user interactions.

### Evaluation Metrics

To assess the quality of the ranking model, we will use standard ranking evaluation metrics 
that consider user interactions with the search results. The following metrics are proposed:

- Precision@k, recall@k, F2 anf other derived metrics - good for multiple choices 


- Kendall Tau Distance 
  - Calculates the number of inversions in the ranking (an inversion is a pair of documents `(i, j)` such as `i` having a greater relevance than document j, appears after on the search result than `j`)

- Mean Reciprocal Rank (MRR)
    - Calculates the rank position of the first relevant item selected by the user. It is defined as the average of the reciprocal ranks for each session.
    - Formula: MRR = (1/N) * Σ (1/rank_i), where N is the number of sessions, and rank_i is the rank of the first relevant item in session i.

- Expected Reciprocal Rank (ERR)
  - Calculates the expected position at which a user will stop searching because they are satisfied with the result found at that rank.

  
Devided metrics (using info about number of events):

- Mean Event Rank
  - Calculates the average event index at which the final selection occurs across all sessions. It evaluates how many events are needed, on average, for the user to find the desired item.

- Success Rate
  - Calculates the percentage of sessions that end with meaningful interaction (the final selection is not null).
 
- Success Rate at N
  - Calculates the percentage of sessions where the user's final selected index is within the top N results returned by the model.