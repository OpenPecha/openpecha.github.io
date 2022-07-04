## Dowloading a corpus

### Install

```bash
pip install openpecha
```

### Download
```python
from pathlib import Path
from openpecha.corpus.download import download_corpus

# setup output path
BASE_DIR = Path(__file__).parent.parent
output_path = BASE_DIR / "data"

# download
download_corpus(
  corpus_name="literary_bo",
  output_path=output_path
)
```

### More features coming soon!


