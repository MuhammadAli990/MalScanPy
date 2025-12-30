# malScanPy

**malScanPy** is a Python-based static malicious file analyzer. It is designed as a tool for advanced users to inspect files and identify potential malicious indicators using both **signature-based** and **heuristics-based** approaches.

---

## Features

- **Multi-format support:** Currently supports APK, PDF, Office documents (e.g., DOCX, DOCM), and EXE files.
- **Signature-based detection:** Uses [YARA](https://virustotal.github.io/yara/) rules to detect known malware signatures from previously analyzed malicious files.
- **Heuristics-based analysis:** Applies general rules to detect suspicious patterns. Examples include:
  - Office macros
  - PDF objects and streams
  - EXE PE file characteristics
  - APK permissions (e.g., camera access)

> **Note:** Heuristics alone cannot definitively determine if a file is malicious. They provide indicators that allow an advanced user to make an informed judgment.

- **Modular design:**

  - Each file type has its own module (APK, EXE, PDF, Office).
  - Heuristics configurations are stored in separate JSON files for each module.
  - Signature rules are stored in separate `.yar` files, making updates easy without modifying code.

- **Engine-driven:** The main engine file `engine.py` handles:

  1. Checking if the file exists at the given path.
  2. Detecting the actual file type by reading magic bytes using `python-magic`.
  3. Passing the file to the appropriate module for analysis.

- **Output:** Returns a detailed list of matched signatures and heuristics for review.
