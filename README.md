# Mobile Phone Sentiment Analysis

A specialized sentiment analysis system focused on mobile phone reviews from YouTube comments. This project collects comments from mobile phone review videos, performs feature-based sentiment analysis, and provides insights about public sentiment on specific phone features.

## Features

- YouTube comment extraction via YouTube Data API
- Text preprocessing and cleaning pipeline
- Feature-based sentiment analysis (camera, battery, performance, etc.)
- Multiple sentiment analysis approaches (VADER, TextBlob, and fine-tuned models)
- Visualization of sentiment distribution by feature
- Export of results to various formats

## Setup

1. Clone this repository:
```
git clone https://github.com/iyassh/mobile-sentiment-analysis.git
cd mobile-sentiment-analysis
```

2. Install dependencies:
```
pip install -r requirements.txt
```

3. Download NLTK data:
```python
python -c "import nltk; nltk.download('punkt'); nltk.download('stopwords'); nltk.download('wordnet')"
```

4. Download spaCy model:
```
python -m spacy download en_core_web_sm
```

5. Set up YouTube API credentials:
   - Create a project in the [Google Cloud Console](https://console.cloud.google.com/)
   - Enable the YouTube Data API v3
   - Create API credentials
   - Create a `.env` file with your API key:
   ```
   YOUTUBE_API_KEY=your_api_key_here
   ```

## Usage

### Basic Usage

```python
from src.youtube_extractor import YouTubeCommentExtractor
from src.preprocessor import TextPreprocessor
from src.sentiment_analyzer import FeatureSentimentAnalyzer
from src.visualizer import SentimentVisualizer

# Extract comments from a YouTube video
extractor = YouTubeCommentExtractor()
comments = extractor.extract_comments("VIDEO_ID_HERE")

# Preprocess comments
preprocessor = TextPreprocessor()
processed_comments = preprocessor.preprocess(comments)

# Analyze sentiment by feature
analyzer = FeatureSentimentAnalyzer()
results = analyzer.analyze(processed_comments)

# Visualize results
visualizer = SentimentVisualizer()
visualizer.plot_feature_sentiment(results)
```

### Run full pipeline

```
python main.py --video_id VIDEO_ID --features camera,battery,performance,display
```

## Project Structure

- `src/`: Source code
  - `youtube_extractor.py`: YouTube comment extraction
  - `preprocessor.py`: Text preprocessing
  - `feature_extractor.py`: Feature identification
  - `sentiment_analyzer.py`: Sentiment analysis
  - `visualizer.py`: Results visualization
  - `utils.py`: Utility functions
- `models/`: Trained models and feature dictionaries
- `data/`: Dataset storage
- `notebooks/`: Jupyter notebooks for exploration and analysis
- `tests/`: Unit tests
- `main.py`: Main execution script

## License

MIT