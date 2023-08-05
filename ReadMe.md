# YouTube Video Transcript Retrieval and Query Notebook

This Jupyter notebook provides a step-by-step guide on how to retrieve and query YouTube video transcripts using ThirdAI and OpenAI's GeneralQnA models. The notebook demonstrates how to extract video transcripts, set up APIs, query the models, and obtain insightful answers.

## Prerequisites

Before running this notebook, make sure you have the necessary libraries and APIs installed. You can install the required packages using the following commands:

```python
!pip install youtube-transcript-api
!pip install pytube
!pip install langchain
!pip install openai
!pip install reportlab
```

Additionally, you'll need API keys for ThirdAI and OpenAI. Replace the placeholders in the code with your actual API keys.

## Setup ThirdAI API

```python
from thirdai import licensing, neural_db as ndb

# licensing.deactivate()
licensing.activate("1FB7DD-CAC3EC-832A67-84208D-C4E39E-V3")
db = ndb.NeuralDB(user_id="my_user")

# Set up a cache directory for Bazaar models
import os
from pathlib import Path
from thirdai.neural_db import Bazaar

if not os.path.isdir("bazaar_cache"):
    os.mkdir("bazaar_cache")

bazaar = Bazaar(cache_dir=Path("bazaar_cache"))
bazaar.fetch()
print(bazaar.list_model_names())

# Load the General QnA model
db = bazaar.get_model("General QnA")
```

## Extract YouTube Video Transcript

The following function can be used to fetch the transcript of a YouTube video given its URL:

```python
def get_youtube_transcript(youtube_url, language=["en"], translation="en"):
    # Fetch the transcript using YouTubeTranscriptApi
    try:
        transcript = YouTubeTranscriptApi.get_transcript(youtube_url, languages=language)
    except Exception as e:
        raise ValueError(f"Error fetching captions: {str(e)}")

    # Combine the transcript text
    text_data = " ".join([caption['text'] for caption in transcript])
    return text_data
```

## Query with ThirdAI

Use the following function to query the video transcript using ThirdAI's General QnA model:

```python
def query_youtube_transcript(youtube_url, language=["en"], translation="en", query=""):
    transcript_text = get_youtube_transcript(youtube_url, language, translation)
    result = db.search(
        query=transcript_text + query,
        top_k=1,
        on_error=lambda error_msg: print(f"Error! {error_msg}")
    )
    return result[0].text
```

## Query with OpenAI (GeneralQnA)

The notebook also demonstrates how to use OpenAI's GeneralQnA model for querying the transcript:

```python
# Replace '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' with your OpenAI API key
openai.api_key = "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"

def query_youtube_transcript_openai(youtube_url, language=["en"], translation="en", query=""):
    transcript_text = get_youtube_transcript(youtube_url, language, translation)
    response = openai.Completion.create(
        engine="text-davinci-002",
        prompt=transcript_text + query,
        max_tokens=150,
    )
    return response.choices[0].text.strip()
```

## Example Queries

You can now use the functions to query the transcript and get answers. For example:

```python
youtube_url = "mbryl4MZJms"

query_1 = "which software is being used, and which version is being used?"
response_1 = query_youtube_transcript(youtube_url, query=query_1)
print(response_1)

query_2 = "Tell me about the main points discussed in the video."
response_2 = query_youtube_transcript(youtube_url, query=query_2)
print(response_2)
```

## Note

Please note that this notebook uses both ThirdAI and OpenAI's GeneralQnA models. Ensure that you have the necessary API keys and credits to access the models. It is also recommended to follow the API usage guidelines and terms of service for both providers.
