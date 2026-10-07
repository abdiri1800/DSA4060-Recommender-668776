# DSA 4060 Personalized Movie Recommender

## Student Details
- **Name:** Abdirisak Hussein
- **Student ID:** 668776
- **Assigned User ID:** 37

## Project Objective
 a simple content-based recommender that profiles one assigned user from their ratings and suggests five unseen movies based on genre similarity

## Datasets
- `movies.csv` – movie catalogue (`movie_id`, `title`, `genres`; genres separated by `|`), 36 movies.
- `ratings.csv` – historical ratings (`user_id`, `movie_id`, `rating`) from 40 users, 440 ratings.

## Method / Approach
1. Calculated the assigned user ID from the Student ID: (last two digits MOD 40) + 1.
2. Profiled the user: listed rated movies, top three, and genre-level average ratings.
3. Treated movies rated >= 4.0 as "liked".
4. Converted genres into vectors with `CountVectorizer`.
5. Used cosine similarity between every movie and the liked movies, weighted by rating, then excluded already-rated movies and kept the top five.

## How to Run the Notebook
- Requirements: Python 3, `pandas`, `numpy`, `scikit-learn`, `jupyter`.
- Keep `movies.csv`, `ratings.csv` and the notebook in the same folder.
- Set `STUDENT_ID` in the first code cell, then run all cells from top to bottom (Kernel > Restart & Run All).

## Recommendation Results (these ones are not distinct)
1. Most similar to 'The Pursuit of Happyness' (rated 5.0); shares genre(s): Biography, Drama. Matches liked genres: Biography, Drama (similarity score 0.70).
2. Most similar to 'Remember the Titans' (rated 5.0); shares genre(s): Drama. Matches liked genres: Drama (similarity score 0.50).
3. Most similar to 'Remember the Titans' (rated 5.0); shares genre(s): Drama. Matches liked genres: Drama (similarity score 0.50).
4. Most similar to 'Remember the Titans' (rated 5.0); shares genre(s): Drama. Matches liked genres: Drama (similarity score 0.50).
5. Most similar to 'Remember the Titans' (rated 5.0); shares genre(s): Drama. Matches liked genres: Drama (similarity score 0.50).

## Recommendation Results (these ones are  distinct)
1. Shares Biography, Drama with liked movies 'The Pursuit of Happyness' (5.0) and 'The Social Network' (4.0) (score 0.70). Ranked above others with the same score by community avg rating 3.47
2. Shares Drama with liked movies 'Remember the Titans' (5.0) and 'Ford v Ferrari' (5.0) (score 0.50). Also adds Comedy, which is new to this user's liked list. Ranked above others with the same score by community avg rating 3.31
3. Shares Drama with liked movies 'Remember the Titans' (5.0) and 'Ford v Ferrari' (5.0) (score 0.50). Also adds Sci-Fi, which is new to this user's liked list. Ranked above others with the same score by community avg rating 3.24.
4. Shares Drama with liked movies 'Remember the Titans' (5.0) and 'Ford v Ferrari' (5.0) (score 0.50). Also adds Sci-Fi, which is new to this user's liked list. Ranked above others with the same score by community avg rating 3.23
5. Shares Drama with liked movies 'Remember the Titans' (5.0) and 'Ford v Ferrari' (5.0) (score 0.50). Also adds Sci-Fi, which is new to this user's liked list. Ranked above others with the same score by community avg rating 3.15.

## Limitation and Suggested Improvement
- **Limitation:** The recommender depends only on genre labels, so movies that share one broad genre look equally similar. I mean In my results, four of the five recommendations tied at a similarity score of 0.50 because they only shared "Drama" with Remember the Titans, even though they differ a lot in style and theme. The user's small number of ratings also makes the profile weak
- **Improvement:** I would basically add filtering, finding users with similar rating patterns and using their high ratings to rank candidates. This would use real preference data to separate movies that genre alone treats as identical, making the recommendations more personalized
