# YouTube Video Transcript Retrieval and Query Project

![YouTube Video Transcript](https://example.com/video_thumbnail.png)

Welcome to the YouTube Video Transcript Retrieval and Query Project! This project aims to help you extract transcripts from YouTube videos and then query them using both ThirdAI and OpenAI's GeneralQnA models to get insightful answers.

## Project Overview

The primary goal of this project is to provide a user-friendly interface to:

1. Extract the transcript of a YouTube video.
2. Use ThirdAI to answer specific questions related to the video's content.
3. Use OpenAI's GeneralQnA model to get additional answers to your queries.

## How to Use

To get started, follow these steps:

1. **Clone the Repository:**
   Clone this repository to your local machine using the following command:

   ```
   git clone https://github.com/sarvagnakadiya/youtube-transcript-querying
   ```

2. **Install Dependencies:**
   Navigate to the project directory and install the required dependencies:

   ```
   cd YouTubeTranscriptQuery
   pip install -r requirements.txt
   ```

3. **Get YouTube API Key:**
   In order to extract video transcripts, you'll need a YouTube Data API Key. Get your API key by following the instructions [here](https://developers.google.com/youtube/registering_an_application).

4. **Set Up ThirdAI API:**
   Sign up for ThirdAI and get your API key from their website (https://thirdai.com).

5. **Set Up OpenAI API:**
   Obtain your OpenAI API key from the OpenAI developer portal (https://openai.com/).

6. **Configure the Environment:**
   Create a new file named `.env` in the project root and add your API keys to it:

   ```
   YOUTUBE_API_KEY=your_youtube_api_key
   THIRDAI_API_KEY=your_thirdai_api_key
   OPENAI_API_KEY=your_openai_api_key
   ```

7. **Run the Application:**
   Launch the application by running the following command:

   ```
   python app.py
   ```

8. **Using the Application:**
   - Enter the YouTube video URL you want to analyze.
   - The application will extract the transcript for you.
   - Enter your questions related to the video's content.
   - The application will provide answers using both ThirdAI and OpenAI's GeneralQnA models.

## Disclaimer

This project is developed for educational and demonstration purposes only. The accuracy of the answers provided by ThirdAI and OpenAI's GeneralQnA models depends on the quality of the models and the data they are trained on. Keep in mind that the models might not always provide accurate or reliable answers.

## Contributions

Contributions to this project are welcome! If you find any issues or have suggestions for improvement, feel free to create a pull request or open an issue.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

We would like to express our gratitude to ThirdAI and OpenAI for providing their powerful language models and APIs for this project.

Enjoy using the YouTube Video Transcript Retrieval and Query Project! If you have any questions or need assistance, please don't hesitate to contact us. Happy querying!
