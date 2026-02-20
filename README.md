# peek

Describe images from the terminal using vision LLMs via OpenRouter.

## Installation

```bash
brew install aayush9029/tap/peek
```

## Usage

```bash
peek photo.png                            # describe with defaults
peek screenshot.png -m qwen72b -d detailed  # detailed with qwen 72B
peek ui.png -c "iOS settings screen"      # with context hint
peek chart.png -d brief                   # brief description
peek image.png --name-only                # just the name
peek --list-models                        # show supported models
```

Piped output is tab-separated (`name\tdescription`), easy to parse:

```bash
peek image.png | cut -f1                  # just the name
peek image.png | cut -f2                  # just the description
mv "ugly.png" "$(peek ugly.png --name-only).png"  # rename with peek
```

## Options

| Flag | Description |
|------|-------------|
| `-h, --help` | Show help |
| `-v, --version` | Show version |
| `-m, --model <name>` | Model shorthand (default: `qwen32b`) |
| `-d, --detail <level>` | `brief` \| `normal` \| `detailed` (default: `normal`) |
| `-c, --context <text>` | Context to guide the description |
| `--name-only` | Print only the name (no description) |
| `--list-models` | List supported models |

## Supported Models

| Shorthand | Model |
|-----------|-------|
| `qwen32b` (default) | `qwen/qwen3-vl-32b-instruct` |
| `qwen72b` | `qwen/qwen3-vl-235b-a22b-instruct` |
| `llama11b` | `meta-llama/llama-3.2-11b-vision-instruct` |
| `gemma12b` | `google/gemma-3-12b-it` |

## Requirements

- macOS (or any system with `curl`, `base64`, `file`, `python3`)
- `OPENROUTER_API_KEY` environment variable ([get one here](https://openrouter.ai/keys))
