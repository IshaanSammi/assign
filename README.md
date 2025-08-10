# Slide Inconsistency Analyzer

This Python project extracts text from PowerPoint presentations (`.pptx`) and associated slide images, then leverages Google Gemini to detect factual or logical inconsistencies across slides. It is useful for auditing presentations for conflicting data, contradictory claims, or timeline mismatches.

## Features

- **Extracts text from PPTX slides** using `python-pptx`.
- **OCR text extraction from slide images** using `pytesseract`.
- **Analyzes slides for inconsistencies** using Gemini Pro API.
- **Outputs a JSON summary** of detected inconsistencies, listing slide numbers and descriptions.

## Requirements

- Python 3.7+
- [Tesseract-OCR](https://github.com/tesseract-ocr/tesseract) installed on your system (for image OCR)
- The following Python packages (install via pip):

  ```bash
  pip install python-pptx pillow pytesseract requests
  ```

## Setup

1. **Clone the Repository**

   ```bash
   git clone https://github.com/IshaanSammi/assign.git
   cd assign
   ```

2. **Install Dependencies**

   ```bash
   pip install -r requirements.txt
   ```

   *If `requirements.txt` is missing, use the pip command above under Requirements.*

3. **Install Tesseract-OCR**

   - On Ubuntu/Debian:  
     `sudo apt-get install tesseract-ocr`
   - On macOS (with Homebrew):  
     `brew install tesseract`
   - On Windows:  
     [Download the installer](https://github.com/tesseract-ocr/tesseract/wiki).

4. **Set Up Your Gemini API Key**

   - Obtain a Gemini API key from Google AI Studio.
   - Edit `code.py` and replace the line:
     ```python
     GEMINI_API_KEY = "Put your api key(i have not put here publically)"
     ```
     with
     ```python
     GEMINI_API_KEY = "YOUR_GEMINI_API_KEY"
     ```

## Usage

1. **Prepare Your Files**

   - Place your PowerPoint file at `slides/sample_deck.pptx`.
   - Place slide images (named like `slide1.png`, `slide2.jpg`, etc.) in `slides/images/`.

2. **Run the Script**

   ```bash
   python code.py
   ```

   The script will:
   - Extract text from the PPTX and images.
   - Send the text to Gemini for inconsistency analysis.
   - Print out any detected inconsistencies.

## Output Example

```
Extracting slide text from PPTX ...
Extracting text from slide images ...
Sending slide text to Gemini for inconsistency detection ...

=== Inconsistencies Detected ===
- Issue on Slide(s): 2, 4
  Description: Slide 2 states revenue as $1M, but Slide 4 states $900K.
...
Analysis complete.
```

## Notes

- **API Limitations:** The Gemini API may have usage limits or rate restrictions.
- **OCR Accuracy:** Text extraction from images depends on image quality and Tesseract configuration.
- **Error Handling:** The script prints errors for API or text parsing failures.

