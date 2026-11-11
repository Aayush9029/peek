# peek

`peek` is a Bash CLI that describes images and videos with vision models on OpenRouter. It can also rename files from the description. It ships through the Homebrew tap `aayush9029/tap`. Status: shipped.

## Commands

| Task | Command |
|------|---------|
| Run | `bin/peek photo.png` |
| Directory mode | `bin/peek ./screenshots --rename -r -j 4` |
| List models | `bin/peek --list-models` |
| Release | Load the `oss-cli-release` skill |

## How it works

- `bin/peek` is the full tool. `resolve_model_id` maps a short name (`qwen32b`, `qwen72b`, `llama11b`, `gemma12b`) to an OpenRouter model ID. The default is `qwen32b`.
- Images go through `sips`: resize to `MAX_WIDTH` (1280) and convert to JPEG at quality 60. `--raw` sends the original file.
- Videos need `ffmpeg` and `ffprobe`. The tool extracts `--frames` frames (default 6) and sends them as images.
- When stdout is a pipe, output is tab-separated: `name\tdescription`.

## Rules

- Read the key from `OPENROUTER_API_KEY`. Never write a key into the repository.
- Keep `ffmpeg` optional. Check for it only when the input is a video.
- Keep `VERSION` in `bin/peek` the same as the git tag. The tap formula is `../../homebrew-tap/Formula/peek.rb`.
