# Low-Memory-Usage YouTube Video Summarizer with BART

A lightweight Python tool designed to summarize YouTube video transcripts with low memory usage. It extracts transcripts, cleans the text, splits it into sentence-aware chunks using NLTK, and generates concise summaries using the BART model (`facebook/bart-large-cnn`). Ideal for summarizing long videos like lectures, tutorials, or talks efficiently.

## Features

- **Low Memory Usage**: Optimized for efficient processing with sentence-aware chunking to handle long transcripts.
- **Transcript Extraction**: Fetches YouTube captions using `youtube-transcript-api`.
- **Text Cleaning**: Removes noise such as `[Music]`, `[Applause]`, extra spaces, and newlines.
- **Sentence-Aware Chunking**: Uses NLTK's sentence tokenization to ensure coherent chunks without mid-sentence cuts.
- **High-Quality Summarization**: Leverages BART (`facebook/bart-large-cnn`) with beam search for accurate summaries.
- **Flexible URL Support**: Handles both standard (`youtube.com/watch?v=ID`) and shortened (`youtu.be/ID`) YouTube URLs.
- **Customizable Parameters**: Full control over BART's generation settings for tailored summaries.

## Installation

### Prerequisites

- Python 3.8+
- A GPU (optional, recommended for faster BART inference)

### Steps

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/Low-Memory-Usage-YouTube-Video-Summarizer-with-BART.git
   cd Low-Memory-Usage-YouTube-Video-Summarizer-with-BART
   ```

2. Install Dependencies:
   `pip install youtube-transcript-api transformers==4.52.4 torch sentencepiece nltk`
   
3. Download NLTK Data:
  ```
  import nltk
  nltk.download('punkt_tab')
  ```

## Usage

1. Run the Summarizer
2. Input a YouTube URL
- Enter a valid YouTube video URL (e.g., https://www.youtube.com/watch?v=IzQ2siryQrM).
- The tool will:
  - Extract the video ID
  - Fetch and clean the transcript
  - Split into sentence-aware chunks (max 900 words)
  - Summarize each chunk using BART
  - Combine summaries into a final output
 
Below is the complete GitHub README content for your project, formatted as a Markdown file. You can copy and paste this directly into a `README.md` file in your repository.

```markdown
# Low-Memory-Usage YouTube Video Summarizer with BART

A lightweight Python tool designed to summarize YouTube video transcripts with low memory usage. It extracts transcripts, cleans the text, splits it into sentence-aware chunks using NLTK, and generates concise summaries using the BART model (`facebook/bart-large-cnn`). Ideal for summarizing long videos like lectures, tutorials, or talks efficiently.

## Features

- **Low Memory Usage**: Optimized for efficient processing with sentence-aware chunking to handle long transcripts.
- **Transcript Extraction**: Fetches YouTube captions using `youtube-transcript-api`.
- **Text Cleaning**: Removes noise such as `[Music]`, `[Applause]`, extra spaces, and newlines.
- **Sentence-Aware Chunking**: Uses NLTK's sentence tokenization to ensure coherent chunks without mid-sentence cuts.
- **High-Quality Summarization**: Leverages BART (`facebook/bart-large-cnn`) with beam search for accurate summaries.
- **Flexible URL Support**: Handles both standard (`youtube.com/watch?v=ID`) and shortened (`youtu.be/ID`) YouTube URLs.
- **Customizable Parameters**: Full control over BART's generation settings for tailored summaries.

## Installation

### Prerequisites

- Python 3.8+
- A GPU (optional, recommended for faster BART inference)

### Steps

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/Low-Memory-Usage-YouTube-Video-Summarizer-with-BART.git
   cd Low-Memory-Usage-YouTube-Video-Summarizer-with-BART
   ```

2. **Create a Virtual Environment** (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**:
   ```bash
   pip install youtube-transcript-api transformers==4.52.4 torch sentencepiece nltk
   ```

4. **Download NLTK Data**:
   Run the following in a Python shell:
   ```python
   import nltk
   nltk.download('punkt_tab')
   ```

## Usage

1. **Run the Summarizer**:
   - Open the `Youtube_Video_BART_Summarizer.ipynb` notebook in Jupyter or Google Colab.
   - Alternatively, convert the notebook to a script (e.g., `summarizer.py`) and run:
     ```bash
     python summarizer.py
     ```

2. **Input a YouTube URL**:
   - Enter a valid YouTube video URL (e.g., `https://www.youtube.com/watch?v=IzQ2siryQrM`).
   - The tool will:
     - Extract the video ID
     - Fetch and clean the transcript
     - Split into sentence-aware chunks (max 900 words)
     - Summarize each chunk using BART
     - Combine summaries into a final output

3. **Example Output**:
   For the video `https://www.youtube.com/watch?v=IzQ2siryQrM`:
   ```
   Total words: 261
   Total chunks: 1

   Summarizing chunk 1/1...

   ===== FINAL SUMMARY =====

   Adults typically need seven to nine hours of sleep for maximum brain performance. Too little sleep negatively affects your ability to remember and concentrate. It can also make you moodier and more irritable and increase the risk of anxiety and depression. To ensure you're getting enough sleep, practice good sleep hygiene.
   ```

## Project Structure

```
Low-Memory-Usage-YouTube-Video-Summarizer-with-BART/
├── Youtube_Video_BART_Summarizer.ipynb  # Main Jupyter notebook
├── README.md                            # This file
├── requirements.txt                     # (Optional) Dependency list
```

## Dependencies

- `youtube-transcript-api==1.2.3`: Fetches YouTube transcripts.
- `transformers==4.52.4`: Provides BART model and tokenizer.
- `torch`: PyTorch for model inference.
- `sentencepiece`: Required for BART tokenizer.
- `nltk`: Sentence tokenization for coherent chunking.

## How It Works

1. **Video ID Extraction**: Parses YouTube URLs using `urllib.parse` to extract the video ID.
2. **Transcript Fetching**: Retrieves transcripts via `youtube-transcript-api` as a single string.
3. **Text Cleaning**: Uses regex to remove tags (e.g., `[Music]`), extra spaces, and newlines.
4. **Sentence-Aware Chunking**: Splits transcripts into chunks (max 900 words) using NLTK's `sent_tokenize` for coherence.
5. **Summarization**: Processes each chunk with BART (`facebook/bart-large-cnn`) using beam search (4 beams, `max_length=200`, `min_length=60`).
6. **Output**: Combines chunk summaries into a concise, readable summary.
