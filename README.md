# Fake-News-Detection-System

🔍 Multimodal Fake News Detection System
An advanced, end-to-end framework that detects fake news by combining Natural Language Processing (NLP), Computer Vision (CV), and Real-Time Web Fact-Checking.

This system uses a weighted ensemble of multiple deep learning models (BERT, CNN, LSTM, and Attention mechanisms) along with image manipulation detection (Error Level Analysis) and automated web search verification to provide a comprehensive credibility verdict on news claims.

🚀 Key Features
Multi-Model Text Classification: Implements and compares multiple architectures trained on the FakeNewsNet dataset (GossipCop & PolitiFact):
DistilBERT (Transformer-based sequence classifier)
FNDNet (Deep CNN with parallel multi-kernel Conv1D layers)
Bidirectional LSTM (BiLSTM)
Hybrid CNN + LSTM
Self-Attention C-BiLSTM
Multimodal Verification (Text + Image):
OCR Text Extraction: EasyOCR & Tesseract extract text from screenshots (e.g., Twitter posts, WhatsApp forwards).
Image Captioning (BLIP): Generates semantic descriptions of uploaded images to verify if they match the news context.
Semantic Alignment (CLIP): Uses OpenAI's CLIP to check similarity between the text claim and the uploaded image.
Image Forensics (Manipulation Check):
Error Level Analysis (ELA): Detects digital modifications, photoshopped regions, and compression inconsistencies.
Statistical Noise Analysis: Analyzes texture smoothness and color uniformity to identify potential AI-generated or CGI images.
Real-Time Fact-Checking:
Automatically searches the web via DuckDuckGo API.
Scrapes content from trusted fact-checking domains (e.g., Snopes, Politifact, FactCheck.org).
Evaluates web results for supporting or contradicting evidence.
Interactive UI: Built using Gradio, providing an intuitive, web-based dashboard supporting both plain text claims and direct image uploads.
🛠️ System Architecture
Mermaid diagram
📈 Analysis Pipeline (How It Works)
Step	Method	Description
1	BERT / NLP	Analyzes linguistic patterns and writing style within the text claim.
2	OCR	Extracts text embedded in images/screenshots to verify against the claim.
3	CLIP & BLIP	Generates an AI caption and checks if the image matches the context of the claim.
4	Image Forensics	Runs Error Level Analysis (ELA) and texture checks to search for edits/AI generation.
5	Real-Time Fact Check	Live-checks fact-checking databases for matching debunks or articles.
6	Weighted Ensemble	Computes a final probability score and prints a detailed analysis report.
📦 Installation & Setup
Prerequisites
Make sure you have Python 3.8+ installed. You will also need Tesseract-OCR installed on your system if you plan to use Tesseract fallback for OCR.

Install Dependencies
bash

pip install -q tensorflow torch transformers datasets
pip install -q gradio easyocr pytesseract pillow
pip install -q duckduckgo-search newspaper3k beautifulsoup4 lxml_html_clean
Run the App
Launch the Gradio dashboard interface:

bash

python app.py
