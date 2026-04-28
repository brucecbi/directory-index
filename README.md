# directory-index

A local directory indexing tool that generates Markdown or interactive HTML file indexes for any folder. Cross-platform (macOS / Windows / Linux).

## Features

- **Markdown mode**: Static `.md` file with hierarchical headings (`##` → `###` → `####`), suitable for embedding in notes, docs, or wikis
- **HTML mode**: Interactive `.html` page with a local HTTP server — collapsible tree, click-to-open files, search filter
- Natural numeric sorting (avoids `10.0` before `2.0`)
- Auto-skip `node_modules`, `.git`, `__pycache__`, `venv`, `dist`, `build`, `.cache`
- Custom tags (readonly / main / backup / pending / custom)
- Cross-platform file open / reveal / browser launch
- Zero external dependencies (pure Python 3 standard library)

## Usage

### Markdown mode

```bash
python3 scripts/generate_index.py "/path/to/target/directory" --format md
```

Output: `INDEX_<dirname>.md` in the target directory.

### HTML mode

```bash
python3 scripts/generate_index.py "/path/to/target/directory" --format html
```

Output: `INDEX_<dirname>.html` + `INDEX_<dirname>_server.py` — auto-starts a local server and opens the browser.

### Options

| Option | Description |
|--------|-------------|
| `--format` | `md` or `html` (required) |
| `--max-depth` | Max recursion depth (default: unlimited) |
| `--port` | Server port, HTML mode only (default: 8427) |
| `--no-open` | Don't auto-open browser, HTML mode only |
| `--tags` | Custom tag rules as JSON |

### Examples

```bash
# Markdown index
python3 scripts/generate_index.py ~/Documents --format md

# HTML index with depth limit
python3 scripts/generate_index.py ~/Documents --format html --max-depth 3

# With custom tags
python3 scripts/generate_index.py ~/Documents --format html \
  --tags '{"readonly": ["report_*.xlsx"], "main": ["main_*.xlsx"]}'
```

## Requirements

- Python 3 (standard library only, no pip install needed)
- A web browser (Safari / Chrome / Edge / Firefox) for HTML mode

## Use Cases

- Due diligence data room indexes
- Project deliverable file inventories
- Personal folder browsing with click-to-open
- Knowledge base / wiki directory listings

## License

MIT
