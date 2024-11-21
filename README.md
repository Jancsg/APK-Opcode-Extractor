# APK-Opcode-Extractor
A Bash script that automates the extraction and cleanup of opcodes from Android APK files. This tool decompiles APKs, processes .smali files, and generates a cleaned list of unique opcodes for further analysis.

Features

	•	Batch decompiles APK files in the current directory using apktool.
	•	Extracts opcodes from .smali files generated during decompilation.
	•	Cleans and formats opcode data through multiple processing steps.
	•	Outputs a final list of unique, cleaned opcodes for each APK.


Requirements

To use this script, ensure the following dependencies are installed on your system:
	1.	Bash shell
	•	The script is written in Bash and requires a Unix-like environment (Linux, macOS, or WSL on Windows).
	2.	Apktool
	•	Required for decompiling APKs. Install it via:
 
 sudo apt install apktool  # (Debian/Ubuntu)
 brew install apktool      # (macOS)

	3.	Core Utilities
	•	Standard utilities like grep, sed, and find.

 Installation

	1.	Clone the repository:

 git clone https://github.com/yourusername/apk-opcode-extractor.git
 cd apk-opcode-extractor
 
 	2.	Make the script executable:

  Usage

	1.	Place all APK files you want to process in the same directory as the script.
	2.	Run the script:

  ./extract-opcodes.sh

  	3.	The script will:
	•	Decompile each APK file.
	•	Extract opcodes from .smali files.
	•	Generate cleaned opcode files in the smali/opcodes directory for each decompiled APK.

 Output

The script produces the following output structure for each APK:

<apk_name>/
├── smali/
│   ├── opcodes/
│   │   ├── opcodes.txt      # Raw opcode list
│   │   ├── opcodesv1.txt    # Without 'vX' prefixes
│   │   ├── opcodesv2.txt    # Without 'pX' prefixes
│   │   └── opcodesv3.txt    # Final cleaned opcodes

  
Processing Steps

	1.	Decompile APKs: Uses apktool to decompile each APK file into a directory with its resources and .smali files.
	2.	Extract Opcodes:
	•	Searches for .smali files in the decompiled APK directory.
	•	Removes unnecessary symbols and lines using grep and sed.
	•	Outputs a sorted, unique list of opcodes.
	3.	Clean Opcodes:
	•	Removes prefixes (e.g., vX, pX) and trailing numbers from opcode names in three steps, producing a final cleaned file.

 Example

Input:

Directory containing two APKs:

app1.apk
app2.apk

Execution:

Run the script:

./extract-opcodes.sh

Output:

Decompiled APKs and cleaned opcodes:

app1/
├── smali/
│   ├── opcodes/
│   │   ├── opcodes.txt
│   │   ├── opcodesv1.txt
│   │   ├── opcodesv2.txt
│   │   └── opcodesv3.txt

app2/
├── smali/
│   ├── opcodes/
│   │   ├── opcodes.txt
│   │   ├── opcodesv1.txt
│   │   ├── opcodesv2.txt
│   │   └── opcodesv3.txt


Notes

	•	Ensure you have proper permissions to run apktool and read the APK files.
	•	This script processes APKs and .smali files in the current directory. Avoid running it in directories with non-APK files to prevent unintended processing.

 Contributing

If you’d like to contribute:

	1.	Fork this repository.
	2.	Create a feature branch:

 git checkout -b feature-name

 	3.	Submit a pull request.





















 
