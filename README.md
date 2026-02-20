# peek

Identify and name images from the terminal using vision LLMs.

## Install

```bash
brew install aayush9029/tap/peek
```

Requires `OPENROUTER_API_KEY` environment variable ([get one](https://openrouter.ai/keys)).

## Usage

```bash
peek photo.png                              # identify with defaults
peek screenshot.png -m qwen72b -d detailed  # detailed with larger model
peek ui.png -c "iOS settings screen"        # with context hint
peek chart.png -d brief                     # brief description
peek image.png --name-only                  # just the name
peek --list-models                          # show supported models
```

Piped output is tab-separated (`name\tdescription`):

```bash
peek image.png | cut -f1                           # just the name
mv "ugly.png" "$(peek ugly.png --name-only).png"   # rename with peek
```

## Options

| Flag | Description | Default |
|------|-------------|---------|
| `-m, --model <name>` | Model shorthand | `qwen32b` |
| `-d, --detail <level>` | `brief` \| `normal` \| `detailed` | `normal` |
| `-c, --context <text>` | Context to guide the description | |
| `--name-only` | Print only the name | |
| `--list-models` | List supported models | |

## Models

| Shorthand | Model |
|-----------|-------|
| `qwen32b` (default) | `qwen/qwen3-vl-32b-instruct` |
| `qwen72b` | `qwen/qwen3-vl-235b-a22b-instruct` |
| `llama11b` | `meta-llama/llama-3.2-11b-vision-instruct` |
| `gemma12b` | `google/gemma-3-12b-it` |
