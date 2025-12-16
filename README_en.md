# YouTube ToolKit (youtube_toolGit)

> **Note on AI-assisted development:** Some terminal log messages include emoji symbols and formatted outputs.  
> These were generated with AI assistance purely for debugging convenience, allowing efficient tracking of process steps.  
> All core logic, data processing, and program structure were designed, implemented, and tested by myself.

---

## Project Overview

**youtube_toolGit** is a Python-based toolkit for automatically processing YouTube videos to extract, clean, and summarize subtitles.  
The tool is designed for **batch processing** of multiple videos in a playlist, producing concise summaries of video content using large language models (LLMs).

Key goals of this project:

- Automate the retrieval of video links from YouTube playlists
- Download and process video subtitles
- Remove duplicate lines in scrolling subtitles
- Generate contextual summaries using LLMs for quick understanding of video content

---

## Functionality

### 1. Playlist Extraction (`getVideoInList.py`)

- Extracts video links from a YouTube playlist URL
- Saves all video URLs to a local text file (`urls.txt`)
- Handles invalid URLs gracefully

### 2. Video & Subtitle Processing (youtube.py)

- Downloads subtitles (English auto-generated) for each video in urls.txt  
- Processes .vtt files by removing repeated lines (common in scrolling auto-subtitles)   
- Converts cleaned subtitles into .txt files  
- Sends processed text to an LLM API for contextual summarization  
- Stores output summaries in _summary.txt files in the downloads folder  
- Fully automated batch processing for multiple videos

---

## Subtitle Processing Approach

YouTube auto-generated subtitles are often **scrolling and contain repeated lines**.  
To simplify processing, the tool keeps **only the first occurrence of each line**, producing a clean transcript for subsequent LLM summarization.

> This is a practical shortcut rather than a fully standardized subtitle-to-text pipeline, but it is effective for summarization purposes.

---

## LLM-Based Summarization

- Uses OpenAI-compatible API (`openrouter.ai`)  
- Summarizes multiple `.txt` subtitle files in context  
- Splits long subtitles into chunks for efficient LLM processing  
- Generates detailed summaries, preserving:  
  - Key operational steps mentioned in the video  
  - Important platform/software usage details  
- Output stored in `_summary.txt` files for easy reference

---

## Technology Stack

- **Python 3**: main programming language  
- **yt-dlp**: for YouTube video and subtitle download  
- **OpenAI / OpenRouter API**: for text summarization  
- **subprocess**: invoking external commands for download and processing  
- **Standard libraries**: `os`, `re`, `json` for file handling and text processing

---

## My Contributions

I implemented **all aspects** of this project, including:

1. **Video link extraction**  
2. **Subtitle download and cleaning**  
3. **Duplicate-line handling in scrolling subtitles**  
4. **Integration with LLM API for summarization**  
5. **Automated batch processing workflow**  
6. **Error handling and output management**

**AI-assisted development** was only used for generating debugging log outputs (emoji-enhanced `print()` statements) to streamline testing.  
All functional code, data processing logic, and program structure were fully designed, written, and tested by me.

---

## Usage

### 1. Extract video URLs from a playlist:

```bash
python getVideoInList.py
```

Input: The URL of the playlist which you want to process
Output: A TXT document called urls.txt contains all the URLs of the videos in the playlist
### 2. Process videos and generate summaries:

```bash
python youtube.py
```

Input: urls.txt (video URLs)

Output: cleaned subtitles and _summary.txt summaries

---

## Notes

- This toolkit is intended for **personal and educational use only**.  
- YouTube subtitles are auto-generated; accuracy may vary depending on video content and transcription quality.  
- The current processing approach is optimized for **quick content extraction and LLM summarization**, rather than perfect subtitle reconstruction.  
- Emoji symbols in terminal logs were added for **debugging and visualization convenience**; core program logic was written and verified manually.  
- The duplicate-line handling in scrolling subtitles is a **practical shortcut** to produce clean text for summarization, not a standardized subtitle processing method.
