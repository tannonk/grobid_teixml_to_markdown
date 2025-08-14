# GROBID TEI XML to Markdown Converter

Converts GROBID-generated TEI XML files to clean Markdown format.

## Installation

```bash
git clone https://github.com/tannonk/grobid_teixml_to_markdown.git
cd grobid_teixml_to_markdown
pip install -e .
```

## Usage

Basic conversion:
```bash
python -m tei_to_markdown -i example_data/teixml -o example_data/md
```

With all optional content:
```bash
python -m tei_to_markdown -i example_data/teixml -o example_data/md \
    --include_tables --include_figures --include_bib --include_backmatter
```

**Options:**

- `-i, --input_dir`: Input directory with TEI XML files
- `-o, --output_dir`: Output directory for Markdown files  
- `-f, --force`: Overwrite existing files
- `--include_tables`: Process tables (default: disabled)
- `--include_figures`: Process figures (default: disabled)
- `--include_bib`: Include references (default: disabled)
- `--include_backmatter`: Include acknowledgments/appendices (default: disabled)
- `--log_level`: Set the logging level (default: WARNING)

## Notes

This conversion tool was developed as part of the ENGAGE project at LiRI and is designed to handle GROBID-generated TEI XML files.
[GROBID](https://github.com/kermitt2/grobid) is a Java-based tool for extracting text from PDF files.

To setup GROBID, follow these steps:

```
# Create a new conda environment with Java 11
conda create -n grobid-env openjdk=11 -c conda-forge

# Activate the environment
conda activate grobid-env

# Verify Java installation
java -version

# Download and install the stable release
wget https://github.com/kermitt2/grobid/archive/0.8.2.zip
unzip 0.8.2.zip
cd grobid-0.8.2
./gradlew clean install
```

Once installed, you can run GROBID in batch mode to extract text from a collection of PDF files.

```bash
# Run GROBID in batch mode
java -Xmx4g -jar grobid-core/build/libs/grobid-core-0.8.2-onejar.jar -gH grobid-home -dIn example_data/pdf -dOut example_data/teixml -exe processFullText
```
