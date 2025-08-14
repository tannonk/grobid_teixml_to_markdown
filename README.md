# GROBID TEI XML to Markdown Converter

Converts GROBID-generated TEI XML files to clean Markdown format.

## Installation

```bash
pip install -e .
```

Or with pip from the repository:
```bash
pip install .
```

## Usage

Basic conversion:
```bash
python -m tei_to_markdown -i example_data/grobid_teixml -o example_data/md
```

With all optional content:
```bash
python -m tei_to_markdown -i example_data/grobid_teixml -o example_data/md \
    --include_tables --include_figures --include_bib --include_backmatter
```

## Options

- `-i, --input_dir`: Input directory with TEI XML files
- `-o, --output_dir`: Output directory for Markdown files  
- `-f, --force`: Overwrite existing files
- `--include_tables`: Process tables (default: disabled)
- `--include_figures`: Process figures (default: disabled)
- `--include_bib`: Include references (default: disabled)
- `--include_backmatter`: Include acknowledgments/appendices (default: disabled)