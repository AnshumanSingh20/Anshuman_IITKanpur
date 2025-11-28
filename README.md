# Bill Extraction and Summarization API

This project provides an automated system for extracting line item details from scanned or uploaded bills (invoices).  
It supports both image files and PDF documents.  
The solution performs OCR on each page, extracts bill items, computes page-wise totals, and produces reconciled final totals without double-counting.

---

## 1. Features

- Accepts document URLs (image or PDF).
- Downloads and processes files directly through the API.
- Extracts text using Tesseract OCR.
- Supports multi-page PDF documents.
- Converts each PDF page to PNG for OCR processing.
- Extracts:
  - Item name
  - Quantity
  - Rate
  - Amount
- Groups extracted items page-wise.
- Computes:
  - Total item count
  - Reconciled total amount
- Returns structured JSON in required format.

---

## 2. Technology Stack

- Java 21 
- Spring Boot 3.x
- Apache PDFBox (PDF to image conversion)
- Tess4J (OCR)
- Maven (Project build and dependency management)

---

## 3. Architecture Overview

1. Input document URL is received by the API.
2. Document is downloaded to a temporary local directory.
3. The file type is detected:
   - If image → processed directly.
   - If PDF → converted into images using PDFBox.
4. OCR is performed on each image using Tesseract.
5. Raw OCR text is parsed to extract structured line items.
6. Page-wise results are aggregated.
7. Totals are computed.
8. The final response is returned in JSON format.

---

## 4. API Endpoint

