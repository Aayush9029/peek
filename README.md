# peek

Describe and rename images from the terminal using vision LLMs.

## Install

```bash
brew install aayush9029/tap/peek
```

Requires `OPENROUTER_API_KEY` environment variable ([get one](https://openrouter.ai/keys)).

## Usage

```bash
# Describe a single image
peek photo.png

# Detailed description with a larger model
peek shot.png -m qwen72b -d detailed

# With context hint
peek ui.png -c "iOS settings screen"

# Brief description
peek chart.png -d brief

# Just the name (no description)
peek image.png --name-only

# List available models
peek --list-models
```

Piped output is tab-separated (`name\tdescription`):

```bash
peek image.png | cut -f1    # just the name
peek image.png | cut -f2    # just the description
```

## Directory Mode

Pass a directory to batch-rename files using vision. Rename and timestamp context are enabled by default.

```bash
peek ./screenshots                  # rename all images in dir
peek ./screenshots --no-rename      # describe only, no rename
peek ./images -r -j 4               # parallel recursive
peek ./photos --no-timestamp-context  # skip timestamp/neighbor context
```

## Options

| Flag | Description | Default |
|------|-------------|---------|
| `-m, --model <name>` | Model shorthand | `qwen32b` |
| `-d, --detail <level>` | `brief` \| `normal` \| `detailed` | `normal` |
| `-c, --context <text>` | Context to guide the description | |
| `--name-only` | Print only the name | |
| `--list-models` | List supported models | |
| `-r, --recursive` | Recurse into subdirectories | |
| `-j, --jobs <n>` | Parallel jobs | `1` |
| `--no-rename` | Don't rename files (describe only) | |
| `--no-timestamp-context` | Skip timestamp/neighbor context | |

## Models

| Shorthand | Model |
|-----------|-------|
| `qwen32b` (default) | `qwen/qwen3-vl-32b-instruct` |
| `qwen72b` | `qwen/qwen3-vl-235b-a22b-instruct` |
| `llama11b` | `meta-llama/llama-3.2-11b-vision-instruct` |
| `gemma12b` | `google/gemma-3-12b-it` |
