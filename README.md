# YouTube Video Transcript Summarization with Hugging Face Transformers

## Overview
This project provides a solution for automatically summarizing YouTube video transcripts using Hugging Face's `transformers` library. It extracts subtitles from YouTube videos via the `youtube_transcript_api` and generates concise summaries using a pre-trained text summarization model.

## Features
- Fetches transcripts from YouTube videos using `youtube_transcript_api`
- Summarizes extracted transcripts using Hugging Face Transformers
- Provides a simple pipeline for efficient summarization
- Works within Jupyter Notebooks and Google Colab

## Installation
To use this project, install the required dependencies using the following commands:

```bash
pip install transformers
pip install youtube_transcript_api
```

## Usage
1. Clone this repository:
   ```bash
   git clone https://github.com/naveenkm21/YTSummerizer.git
   cd YTSummerizer
   ```

2. Open the Jupyter Notebook or run in Google Colab:
   - Open [`Youtube_Video_Transcript_Summarization_with_Hugging_Face_Transformers.ipynb`](Youtube_Video_Transcript_Summarization_with_Hugging_Face_Transformers.ipynb)
   - Run the notebook cells step by step

3. Extract and summarize a YouTube video transcript:
   ```python
   from transformers import pipeline
   from youtube_transcript_api import YouTubeTranscriptApi

   # Function to fetch transcript
   def get_transcript(video_id):
       transcript = YouTubeTranscriptApi.get_transcript(video_id)
       text = " ".join([t["text"] for t in transcript])
       return text

   # Summarization pipeline
   summarizer = pipeline("summarization")
   
   video_id = "<YOUTUBE_VIDEO_ID>"  # Replace with actual video ID
   transcript_text = get_transcript(video_id)
   summary = summarizer(transcript_text, max_length=150, min_length=50, do_sample=False)
   print(summary[0]['summary_text'])
   ```

## Running on Google Colab
Click the badge below to open the notebook in Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/naveenkm21/YTSummerizer/blob/main/Youtube_Video_Transcript_Summarization_with_Hugging_Face_Transformers.ipynb)

## Requirements
- Python 3.7+
- `transformers`
- `youtube_transcript_api`

## Contributing
Contributions are welcome! Feel free to open issues or submit pull requests.

## License
This project is licensed under the MIT License. See the `LICENSE` file for more details.

