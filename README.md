# ExeSteganography

A Python tool for educational demonstration of executable file steganography in images using LSB (Least Significant Bit) technique.

The ExeSteganography tool implements LSB (Least Significant Bit) steganography to hide executable files within images. It modifies the least significant bits of image pixels to store binary data from the executable, along with an MD5 hash for integrity verification. The code features type hints and comprehensive documentation, using NumPy and PIL for image processing. Key functionalities include capacity verification, error handling, and integrity checking. The tool provides both embed_exe() and extract_exe() methods, with the former hiding executables in carrier images and the latter recovering them while verifying their integrity through MD5 hashing.

## Video Demonstration

https://github.com/user-attachments/assets/a156eadd-143f-4073-85bb-1e0de15371e2

⚠️ **WARNING: This tool is for educational purposes only. Use in controlled environments.**

## Features

- Hide executable files within carrier images
- Extract hidden executables from stego images
- MD5 hash verification for file integrity
- Type-annotated codebase with comprehensive documentation
- Progress indicators and detailed error reporting
- Automatic capacity verification

## Requirements

```
Python 3.7+
NumPy
Pillow (PIL)
```

## Installation

1. Clone the repository:
```bash
git clone https://github.com/god233012yamil/ExeSteganography.git
cd ExeSteganography
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

## Usage

### Basic Usage

```python
from exe_steganography import ExeSteganography

# Create an instance
stego = ExeSteganography()

# Embed an executable
stego.embed_exe(
    image_path="path/to/carrier.png",
    exe_path="path/to/program.exe",
    output_path="path/to/output.png"
)

# Extract the executable
stego.extract_exe(
    stego_image_path="path/to/output.png",
    output_exe_path="path/to/extracted.exe"
)
```

### Command Line Usage

```bash
python exe_steganography.py
```

## Security Considerations

1. **Isolated Environment**: Always run this tool in an isolated environment (virtual machine recommended)
2. **Antivirus**: Scan all files before and after operations
3. **File Verification**: Always verify MD5 hashes match after extraction
4. **Source Control**: Only process executables from trusted sources
5. **Educational Use**: This tool is meant for educational purposes to demonstrate security concepts

## How It Works

1. **Embedding Process**:
   - Reads the executable file and calculates its MD5 hash
   - Converts file data and hash to binary
   - Modifies the least significant bits of image pixels
   - Adds an end marker for extraction
   - Saves the modified image

2. **Extraction Process**:
   - Reads the LSBs from the image
   - Reconstructs the executable and hash
   - Verifies file integrity using MD5
   - Saves the extracted executable

## Technical Details

### LSB Steganography

The tool uses Least Significant Bit (LSB) steganography, which works by replacing the least significant bits of pixel values in the carrier image with bits from the executable file. This method ensures minimal visual impact on the carrier image while allowing for significant data storage.

### File Integrity

MD5 hashing is used to verify the integrity of extracted files:
- Original MD5 hash is stored with the executable
- After extraction, a new hash is calculated and compared
- Any mismatch indicates potential corruption

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit changes (`git commit -am 'Add new feature'`)
4. Push to branch (`git push origin feature/improvement`)
5. Create Pull Request

## License

MIT License - see [LICENSE](LICENSE) file for details

## Disclaimer

This tool is provided for educational purposes only. The authors are not responsible for any misuse or damage caused by this program. Users are responsible for complying with all applicable laws and regulations.

## Author

[Your Name]
- GitHub: [@yourusername]
- Email: your.email@example.com

## Acknowledgments

- Thanks to the Python community for providing excellent imaging and numpy libraries
- Special thanks to contributors and testers

---

## API Documentation

### Class: ExeSteganography

#### Methods

##### `__init__(self) -> None`
Initializes the ExeSteganography object with default end marker.

##### `calculate_md5(self, file_path: str) -> str`
Calculates MD5 hash of a file.

Parameters:
- `file_path`: Path to the file

Returns:
- Hexadecimal string of MD5 hash

##### `embed_exe(self, image_path: str, exe_path: str, output_path: str) -> bool`
Embeds an executable file into a carrier image.

Parameters:
- `image_path`: Path to carrier image
- `exe_path`: Path to executable file
- `output_path`: Path for output stego image

Returns:
- `True` if successful, `False` otherwise

##### `extract_exe(self, stego_image_path: str, output_exe_path: str) -> bool`
Extracts an executable from a stego image.

Parameters:
- `stego_image_path`: Path to stego image
- `output_exe_path`: Path for extracted executable

Returns:
- `True` if successful and verified, `False` otherwise

## Development

### Project Structure
```
ExeSteganography/
├── exe_steganography.py
├── requirements.txt
├── tests/
│   ├── __init__.py
│   └── test_steganography.py
├── examples/
│   ├── carrier.png
│   └── example.py
├── LICENSE
└── README.md
```

### Testing

Run tests using pytest:
```bash
pytest tests/
```

### Future Improvements

1. Add support for multiple file embedding
2. Implement alternative steganography algorithms
3. Add GUI interface
4. Improve error handling and recovery
5. Add support for other file types
6. Implement encryption for additional security

## Troubleshooting

Common issues and solutions:

1. **Image Capacity Error**
   - Use a larger carrier image
   - Compress the executable before embedding

2. **Extraction Fails**
   - Verify the image hasn't been modified or compressed
   - Check if the original format was preserved

3. **MD5 Verification Fails**
   - The stego image may have been modified
   - The extraction process may have been interrupted

For more issues, please check the GitHub Issues page.
