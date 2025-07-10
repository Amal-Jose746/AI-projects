# OCR-Enabled Engineering Drawing Metadata Extractor
This project automates the extraction of key metadata fields from engineering drawing PDFs using Tesseract OCR and LLMs (Large Language Models). The goal is to eliminate manual data entry and reduce errors in document handling workflows by extracting fields like Drawing Number, Title, Revision, Date, and Description directly from scanned drawings.

📌 Features
Extracts structured metadata from engineering drawing PDFs

Uses Tesseract OCR for text extraction

Leverages NVIDIA-hosted LLM (e.g., LLaMA-4 Maverick) for intelligent data parsing

Outputs results in CSV format

Batch processing of all PDFs in a directory

Fallback logic for malformed LLM responses

# Setup Instructions

2. Python Dependencies
Install required packages:
-pytesseract \
-pdf2image \
-Pillow \
-pandas \
-requests

3. Install Poppler for PDF-to-Image Conversion
Windows:

Download from: https://github.com/oschwartz10612/poppler-windows/releases/

Extract to a location, e.g., C:\poppler-24.08.0\Library\bin

Add this path to the system environment variable PATH

4. Install Tesseract OCR
Windows:

Download installer: https://github.com/tesseract-ocr/tesseract/wiki

Recommended version: v5.3.0 or above

Install to: C:\Program Files\Tesseract-OCR

Add C:\Program Files\Tesseract-OCR to your PATH environment variable:

Go to System Properties → Environment Variables

Edit the PATH variable and add the Tesseract folder

Test it in a new Command Prompt:

tesseract --version

📂 Directory Structure

project_root/
│
├── drawings/                  # Folder with PDF files
├── main.py                    # Main script to run extraction
├── output/
│   └── All_Drawings_Metadata.csv
├── README.md
└── requirements.txt
▶️ How to Run
Place your scanned drawing PDFs inside the drawings/ folder.

Open terminal and run:

## data_parser_4.py
The script will:

Convert PDFs to images

Use Tesseract OCR to extract text

Send the OCR output to the LLM

Parse the returned JSON

Save the final structured output in:
drawings/All_Drawings_Metadata.csv

🧪 Output Sample
Filename	Drawing Number	Title	Revision	Date	Description
DRG_001.pdf	ABC123	Pump Assembly Schematic	A	12-Mar-2023	Initial release

🚀 Future Scope & Enhancements
While Tesseract is effective, it has several limitations in layout-sensitive or low-quality scans. For better accuracy and robustness, the following enhancements are recommended:

1. Use TrOCR (Transformer-based OCR)
Advantage: Deep learning-based; understands visual structure and semantics

Suggested Models:

microsoft/trocr-base-stage1 (for balanced performance)

microsoft/trocr-small-printed (for faster CPU inference)

Can be integrated with Hugging Face’s transformers library.

2. Layout-aware Models
Tools like DocTR, Donut, or LayoutLMv3 can preserve and understand document structure (tables, blocks, labels).

Useful when metadata fields are spatially dependent (e.g., “REV” near bottom right).

3. Multimodal Vision-Language Models
Models like LLaVA or BLIP-2 combine visual and textual understanding for even more accurate field association.

Ideal for drawings with both diagrams and complex labels.

4. Cloud/On-Premise Deployment
Build a Streamlit dashboard or FastAPI service for users to upload and view drawing metadata interactively.

Integrate with SharePoint, ERP, or PLM systems for real-time syncing.

📞 Support & Contact
For questions, integration support, or collaboration opportunities, feel free to reach out via [email@example.com] or open an issue in the GitHub repository.
