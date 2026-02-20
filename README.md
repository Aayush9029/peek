# peek

Describe images from the terminal using vision LLMs via OpenRouter.

## Installation

```bash
brew install aayush9029/tap/peek
```

Or tap first:

```bash
brew tap aayush9029/tap
brew install peek
```

## Usage

```bash
peek photo.png                            # describe with defaults
peek screenshot.png -m qwen72b -d detailed  # detailed with qwen 72B
peek ui.png -c "iOS settings screen"      # with context hint
peek chart.png -d brief                   # brief description
peek --list-models                        # show supported models
```

## Options

| Flag | Description |
|------|-------------|
| `-h, --help` | Show help |
| `-v, --version` | Show version |
| `-m, --model <name>` | Model shorthand (default: `qwen32b`) |
| `-d, --detail <level>` | `brief` \| `normal` \| `detailed` (default: `normal`) |
| `-c, --context <text>` | Context to guide the description |
| `--list-models` | List supported models |

## Supported Models

| Shorthand | Model |
|-----------|-------|
| `qwen32b` (default) | `qwen/qwen3-vl-32b-instruct` |
| `qwen72b` | `qwen/qwen3-vl-235b-a22b-instruct` |
| `llama11b` | `meta-llama/llama-3.2-11b-vision-instruct` |
| `gemma12b` | `google/gemma-3-12b-it` |

## How it works

1. Base64-encodes the image
2. Sends it to OpenRouter's vision API with a detail-level prompt
3. Prints the model's description to stdout

## Requirements

- macOS (or any system with `curl`, `base64`, `file`, `python3`)
- `OPENROUTER_API_KEY` environment variable ([get one here](https://openrouter.ai/keys))

## License

MIT
