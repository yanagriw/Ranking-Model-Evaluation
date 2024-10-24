# Ranking Model Evaluation

## Dataset Overview

The dataset contains simplified data simulating Search Everywhere usage, 
where each row represents a lookup or state of the SE window at a particular moment. 
Given this data, we aim to evaluate the performance of a ranking model that predicts 
relevant search results based on user interactions.

## Evaluation Metrics

To assess the quality of the ranking model, we will use standard ranking evaluation metrics 
that consider user interactions with the search results. The following metrics are proposed:

- **Kendall Tau Distance**
  - Calculates the number of inversions in the ranking (an inversion is a pair of documents `(i, j)` such as `i` having a greater relevance than document j, appears after on the search result than `j`).
  - https://www.jstor.org/stable/2332303

- **Mean Reciprocal Rank (MRR)**
    - Calculates the rank position of the first relevant item selected by the user. It is defined as the average of the reciprocal ranks for each session.
    - Formula: MRR = (1/N) * Σ (1/rank_i), where N is the number of sessions, and rank_i is the rank of the first relevant item in session i.

- **Expected Reciprocal Rank (ERR)**
  - Calculates the expected position at which a user will stop searching because they are satisfied with the result found at that rank. the likelihood of a user stopping their search at a particular rank because they are satisfied with the result found at that position. This metric considers the probability of relevance at each rank and the decreasing likelihood of continuing the search after encountering relevant items.
  - https://dl.acm.org/doi/10.1145/1645953.1646033

  
### Session-Based Metrics (based on the number of events within a session):

- **Mean Event Rank**
  - Calculates the average event index at which the final selection occurs across all sessions. It evaluates how many events are needed, on average, for the user to find the desired item.

- **Success Rate**
  - Calculates the percentage of sessions that end with meaningful interaction (the final selection is not null).
 
- **Success Rate at N**
  - Calculates the percentage of sessions where the user's final selected index is within the top N results returned by the model.

- **Average Session Duration** 
  - Represents the time from the start to the end of each search session.


### Metrics Not Suitable for This Dataset
Some commonly used ranking metrics are not appropriate for the Search Everywhere dataset due to the nature of the interactions:

- **Precision@k, recall@k, F2 anf other derived metrics** 
  - These metrics are typically used when there are multiple relevant items to retrieve. Since the dataset focuses on scenarios with a single relevant item, these metrics are not suitable for our evaluation.

## References

Key sources include:
- "A New Measure of Rank Correlation" (Kendall Tau Distance): https://www.jstor.org/stable/2332303
- "Expected Reciprocal Rank for Graded Relevance" (ERR): https://dl.acm.org/doi/10.1145/1645953.1646033
- Some concepts were also drawn from the "Information Retrieval" course at the Faculty of Mathematics and Physics, Charles University.