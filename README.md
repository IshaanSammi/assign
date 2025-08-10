AI‑Enabled PowerPoint Inconsistency Checker
This is a Python‑based command‑line tool that analyzes PowerPoint decks (.pptx) and/or slide images to detect factual, numerical, textual, and timeline inconsistencies across slides.

It uses:

python-pptx for extracting text from .pptx files.

Tesseract OCR (pytesseract) for reading slide images.

Google Gemini 2.5 Flash API for advanced semantic and logical comparison.

Features
Works with both PPTX files and image slides.

Detects:

Conflicting numerical data (e.g., mismatched revenue figures, incorrect percentages)

Contradictory statements across slides

Timeline/date mismatches

Outputs a clear, structured, terminal‑friendly report with slide references.

Generalised, extensible design for different subjects or industries.

No UI — runs purely in the terminal as per requirements.

How It Works
Extracts Text from PPTX

Opens .pptx using python-pptx.

Reads slide shapes containing text along with their slide numbers.

Extracts Text from Images

Reads .png/.jpg files via pytesseract OCR.

Assigns slide numbers based on file names.

Combines & Cleans Data

Merges all extracted text blocks.

Deduplicates where same slide is present in both formats.

Sends Data to Gemini

Constructs a structured prompt listing all slide contents.

Asks Gemini to identify:

Conflicting figures or percentages

Contradictory claims

Mismatched dates or timelines

Calls the endpoint:
https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent

Parses AI Response

Receives JSON output from Gemini with an array of issues including:

slides: list of involved slide numbers

issue: short description

Displays in Terminal

Prints each inconsistency in a clean format with slide references.
