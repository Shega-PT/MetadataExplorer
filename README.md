# 🔍 Metadata Explorer v2

[![Python Version](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-red.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

A powerful, cross-platform Python tool for deep metadata extraction from various file types. Supports JSON, CSV, and log output with multi-threading. Perfect for digital forensics, organization, and curiosity!

## ✨ Features

- **🔍 Deep Metadata Extraction** - Supports images (EXIF, GPS), audio (ID3), video, and **documents**
- **📁 Recursive Scanning** - Explores entire directory structures
- **📊 Detailed Reports** - Generates metadata logs, **JSON**, or **CSV** reports
- **🚀 Cross-Platform** - Works on Windows, macOS, and Linux
- **🛡️ Error Resilient** - Continues scanning even if some files fail
- **📈 Smart Filtering** - Automatically skips system files and directories
- **⚡ Multi-Threading** - Faster scans with parallel processing
- **🎯 Type Filtering** - Scan only images, audio, video, or documents
- **🧭 GPS Conversion** - Converts GPS coordinates to decimal degrees
- **📏 Human-Readable** - File sizes and durations in readable format

## 📁 Supported Formats

| Category | Formats | Metadata Extracted |
|----------|---------|-------------------|
| **Images** | JPG, PNG, HEIC, TIFF, WebP, BMP, GIF | EXIF, GPS, Dimensions, DPI, Camera settings |
| **Audio** | MP3, FLAC, M4A, OGG, WAV, AAC, Opus, WMA | ID3 tags, Duration, Bitrate, Sample rate |
| **Video** | MP4, MOV, AVI, MKV, WMV, FLV, WebM | Duration, Resolution, Codec, Framerate |
| **Documents** | PDF, DOCX, XLSX | Author, Pages, Title, Created/Modified dates |
| **RAW** | CR2, CR3, NEF, ARW, DNG, ORF, RW2, RAF | EXIF metadata via exifread |
| **All Files** | Any file type | Size, MIME type, Creation/modification dates |

## 🚀 Quick Start

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/Shega-PT/metadata-explorer.git
   cd metadata-explorer
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

### Basic Usage

Scan the current directory:

```bash
python universal.py
```

Scan a specific directory:

```bash
python universal.py /path/to/your/files
```

Scan your entire pictures folder:

```bash
python universal.py ~/Pictures
```

### Output Formats

JSON output:

```bash
python universal.py ~/Pictures --format json
```

CSV output:

```bash
python universal.py ~/Pictures --format csv -o report.csv
```

### Advanced Usage

Filter by file type:

```bash
python universal.py ~/Pictures --type images
```

With progress bar and 4 threads:

```bash
python universal.py ~/Pictures --progress --threads 4
```

Dry-run (list files only):

```bash
python universal.py ~/Pictures --dry-run
```

### Options

| Flag | Description | Default |
|------|-------------|---------|
| `directory` | Directory to scan | `.` (current) |
| `-o, --output` | Output file path | `metadata_report.{format}` |
| `-f, --format` | Output format: `log`, `json`, `csv` | `log` |
| `-t, --type` | File type filter: `all`, `images`, `audio`, `video`, `documents` | `all` |
| `--dry-run` | List files without extracting metadata | off |
| `-p, --progress` | Show progress bar | off |
| `-n, --threads` | Number of worker threads (0 = auto) | 1 |
| `-v, --verbose` | Debug output | off |

## 📊 Example Output

```
============================================================
DIRECTORY: Vacation_Photos
============================================================

FILE: beach_sunset.jpg
PATH: Vacation_Photos/beach_sunset.jpg
METADATA:
  • IMG_Format: JPEG
  • IMG_Dimensions: 1920x1080
  • IMG_EXIF_DateTimeOriginal: 2023:07:15 18:32:45
  • IMG_GPS_LatitudeDecimal: 38.723167
  • IMG_GPS_LongitudeDecimal: -9.154830
  • IMG_Image_Make: Canon
  • IMG_Image_Model: Canon EOS R5
  • FILE_Size: 8.06 MB
  • FILE_MimeType: image/jpeg
  • FILE_Created: 2023-07-15T18:32:45
```

## 🛠️ Advanced Usage

### Customizing Ignored Files

Edit the `ignored_dirs` and `ignored_files` sets in the `FileManager` class to customize what gets skipped.

### Multiple Output Formats

The script defaults to `metadata_report.log`. Use `--format json` for JSON or `--format csv` for CSV output.

### Integrating with Other Tools

Use the `UniversalMetadataExtractor` class independently in your projects:

```python
from pathlib import Path
from universal import UniversalMetadataExtractor

extractor = UniversalMetadataExtractor()
metadata = extractor.get_all_metadata(Path("your_file.jpg"))
print(metadata.get("IMG_EXIF_DateTimeOriginal"))
```

## 📁 Project Structure

```
metadata-explorer/
├── universal.py          # Main script
├── requirements.txt      # Dependencies
├── README.md             # This file
├── LICENSE               # GNU GPLv3 license
├── __init__.py           # Package init
├── metadata_report.log   # Generated report (example)
└── examples/
    └── sample_scan/      # Example directory structure
```

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

- **Report Bugs** - Open an issue with detailed information
- **Suggest Features** - Share your ideas for improvements
- **Submit Pull Requests** - Add support for new file formats or features

### Development Setup

Clone and install in development mode:

```bash
git clone https://github.com/Shega-PT/metadata-explorer.git
cd metadata-explorer
pip install -e .
pip install -r requirements-dev.txt  # Optional dev dependencies
```

## 📄 License

**Metadata Explorer v2** — Copyright (C) 2026  ShegaPT

This program is free software: you can redistribute it and/or modify it under the terms of the **GNU General Public License** as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but **WITHOUT ANY WARRANTY**; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **exifread** for EXIF data extraction
- **mutagen** for audio metadata
- **hachoir** for video metadata analysis
- **pymediainfo** for detailed video metadata
- **Pillow** for image processing capabilities
- **pillow-heif** for HEIC/HEIF image support
- **python-magic** for MIME type detection
- **pypdf** for PDF metadata
- **python-docx** for DOCX metadata
- **openpyxl** for XLSX metadata
- **tqdm** for progress bar

## ⚠️ Disclaimer

This tool is for educational and organizational purposes only. Always respect privacy laws and obtain proper permissions before scanning others' files.

---

Made with ❤️ for digital explorers everywhere
⭐ If you find this useful, please consider starring the repository!
