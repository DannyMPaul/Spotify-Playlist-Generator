# Spotify Playlist Generator from Human Emotions

This project is a sophisticated pipeline that translates human emotion, as expressed in text, into a curated Spotify playlist. It analyzes a sentence or phrase, identifies the dominant emotion, and then generates a playlist of songs that match that mood.

## Features

- **Emotion-Based Recommendations:** Instead of relying on traditional genre or artist-based recommendations, this tool curates music based on the emotional sentiment of your text.
- **12 Macro Emotions:** The model is trained to recognize 12 distinct emotional categories: joy, sadness, anger, fear, excitement, disgust, love, admiration, gratitude, curiosity, optimism, and neutral.
- **Extensible and Transparent:** The entire pipeline, from data processing to model training and playlist generation, is documented in a series of Jupyter notebooks, making it easy to understand, modify, and extend.

## How It Works

The project is divided into three main stages:

1.  **Exploratory Data Analysis (EDA):** The first notebook, `01_EDA.ipynb`, explores the GoEmotions dataset. It visualizes the distribution of emotions, analyzes text characteristics, and collapses the original 27 emotion labels into our 12 macro-categories. This step is crucial for understanding the data and preparing it for modeling.

2.  **Emotion Classification:** In `02_Emotion_Classifier.ipynb`, we train a machine learning model to classify text into one of the 12 emotions. The notebook preprocesses the text data, vectorizes it using TF-IDF, and then trains and evaluates two different classifiers (Logistic Regression and LinearSVC). The best-performing model is saved for the next stage.

3.  **Spotify Pipeline:** The final notebook, `03_Spotify_Pipeline.ipynb`, brings everything together. It loads the trained classifier, takes a text input, and predicts the emotion. Based on the predicted emotion, it selects a set of genre seeds and uses the Spotify API to fetch a list of recommended tracks, creating a custom playlist for your mood.

## Setup and Usage

To run this project, you'll need to set up your environment and Spotify API credentials.

### 1. Installation

First, clone the repository and install the required Python packages:

```bash
git clone https://github.com/your-username/Spotify-Playlist-Generator.git
cd Spotify-Playlist-Generator
pip install -r requirements.txt
```

### 2. Spotify API Credentials

You'll need to create a Spotify Developer application to get your API credentials.

1.  Go to the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard/) and log in.
2.  Click "Create an App" and give it a name and description.
3.  Once your app is created, you'll see your `Client ID` and `Client Secret`.
4.  In the project directory, copy the `.env.example` file to a new file named `.env`:

    ```bash
    cp .env.example .env
    ```

5.  Open the `.env` file and paste your `Client ID` and `Client Secret`:

    ```
    SPOTIPY_CLIENT_ID='Your-Client-ID'
    SPOTIPY_CLIENT_SECRET='Your-Client-Secret'
    ```

### 3. Running the Pipeline

You can run the entire pipeline by executing the Jupyter notebooks in order. To simply try out the playlist generation with your own text, you can run the `03_Spotify_Pipeline.ipynb` notebook and modify the `mood_text` variable in the interactive cell.

## Project Structure

- `01_EDA.ipynb`: Notebook for data exploration and preprocessing.
- `02_Emotion_Classifier.ipynb`: Notebook for training and evaluating the emotion classifier.
- `03_Spotify_Pipeline.ipynb`: Notebook for the final Spotify playlist generation pipeline.
- `requirements.txt`: A list of all the Python packages required for this project.
- `data/`: Contains the raw and processed data.
- `models/`: Stores the trained machine learning models.
- `outputs/`: Saves the outputs from the notebooks, such as plots and evaluation results.
- `.env.example`: An example file for storing your Spotify API credentials.

This project was built with a focus on clarity and reproducibility. Feel free to explore the notebooks, experiment with the models, and adapt the pipeline to your own creative ideas!
