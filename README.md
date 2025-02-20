# filterbib

Package to filter out particular fields from a bib-file (e.g., exported from zotero). Cleans up the file so that only relevant fields are shown in the bibliography.

## Installation
```bash
# install package
pip install git+https://github.com/gjheij/filterbib
```

This will place 2 scripts in the `bin` folder of the current anaconda environment: `filter_bib` and `read_bib`:
- `filter_bib`: main shell script that calls upon `read_bib`. This is a shell script to deal with `ampersands` properly, which turned out to be tricky with python.
- `read_bib`: python script that uses `pybtex` to do most of the actual filtering.

## Usage
The usage is simple: export a file from Zotero as `bibtex`, which generates a `bib`-file. This file can then be passed to `filter_bib`:

```bash
# simplest call
filter_bib exported_file.bib exported_file_clean.bib
```

By default, the following fields are removed:
```python
fields_to_remove = [
    "abstract",
    "note",
    "file",
    "extra",
    "keywords",
    "copyright",
    "url",
    "doi",
    "urldate",
    "issn",
    "shorttitle",
    "language",
    "pmid"
]
```

For some instances, it's nice to keep the `doi`-field, in which case you can copy this list and exclude `doi`:

```bash
filter_bib exported_items.bib exported_items_clean.bib abstract,note,file,extra,keywords,copyright,url,urldate,issn,shorttitle,language,pmid
```
