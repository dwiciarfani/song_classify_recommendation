# Song Classify Recommendation

## Objective
The goal of this project is to develop a recommendation model for song classification based on historical popular songs. By analyzing songs that have been popular across various channels, the model aims to assist music platforms in identifying new songs with the potential to become hits in the future.

## Dataset
The dataset used in this project contains the following variables:

| No | Variable         | Type    | Notes                               |
|----|------------------|---------|-------------------------------------|
| 1  | Video ID         | object  | Unique identifier for each song     |
| 2  | Peak Views       | int64   | Highest view count                  |
| 3  | Daily Avg Views  | float64 | Average daily views                 |
| 4  | Channel          | object  | The channel that covered the song   |
| 5  | Bahasa           | object  | Language of the song (Indonesia, English, Daerah) |
| 6  | Mood Song        | object  | Mood conveyed (Bahagia, netral, sedih) |
| 7  | Concept          | object  | Video concept (Indoor, Outdoor, Studio) |
| 8  | Genre            | object  | Music genre (null, Pop, Reggae, Dangdut) |
| 9  | Outfit           | object  | Outfits featured (null, Kerudung, Non Kerudung) |
| 10 | Song Type        | object  | Type of song (null, Viral, Recycle) |

## Methodology
### Steps
1. **Calculate Average Daily Views**: Compute the average from the `Daily Avg Views` variable for each video.
2. **Determine Top 10% Threshold**: Calculate the threshold for `Peak Views` using the 90th percentile. This threshold helps identify the top 10% of videos based on peak view count.
3. **Weighting Parameters**: Create the weighting of each parameter using the formula:

   \[
   ((v/(v+m))xR) + ((m/(m+C))xC)
   \]

   Where:
   - \( C \): Average of Daily Average Views
   - \( m \): Top 10% song threshold (90th percentile of peak views)
   - \( v \): Peak Views of each video
   - \( R \): Daily Average Views of each video

4. **Determine the Mode**: Calculate the mode of the weighted results to identify which category has the highest score.

### Model Development
- Machine learning algorithms were utilized to classify songs based on these weighted parameters and recommend new songs with the potential to become popular.
  
## Results
The final model successfully identifies songs with a high potential for popularity across different channels. Detailed insights and visualizations of the results can be found in the [project presentation](https://docs.google.com/presentation/d/1zpD411awAOcJfUgyDdZRUUp6pjxN2fuz5BMyoBpo2qA/edit?usp=sharing).

## Usage
1. **Prerequisites**: Ensure you have Python installed along with the required libraries (`pandas`, `numpy`, `scikit-learn`, `pymysql`, `matplotlib`).
2. **Database Connection**: The code establishes a connection to a MySQL database to pull data. Adjust the connection parameters (`host`, `user`, `passwd`, `database`) in the script to connect to your database.
3. **Data Retrieval**: Run the script to execute SQL queries and retrieve song data from the database. The retrieved data is processed and prepared for model training.
4. **Model Training**:
   - Explore the data using the Jupyter notebooks in the `notebooks/` folder.
   - Use the `src/` folder scripts to perform K-Means clustering and other classification tasks.
   - Evaluate the model's performance using the provided metrics.
5. **Customization**: Adjust model parameters in the configuration files to fine-tune the recommendations as needed.

## Contact
For questions or collaboration, please reach out via [email](dwiluciaarfani35@gmail.com).
