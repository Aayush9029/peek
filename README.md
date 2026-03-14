<img src="assets/icon.png" width="128" alt="peek">

# peek

Describe images from the terminal using vision LLMs.

## Install

```bash
brew install aayush9029/tap/peek
```

Requires `OPENROUTER_API_KEY` ([get one](https://openrouter.ai/keys)).

## Usage

```bash
peek photo.png                          # describe an image
peek shot.png -m qwen72b -d detailed    # larger model, detailed description
peek ui.png -c "iOS settings screen"    # with context hint
peek chart.png -d brief                 # brief description
peek image.png --name-only              # just the name
peek --list-models                      # list available models

# directory mode
peek ./screenshots                      # describe all images in dir
peek ./screenshots --rename             # describe + rename files
peek ./images -r -j 4                   # parallel recursive
```

Piped output is tab-separated (`name\tdescription`).

---

*More CLI tools: [`brew tap aayush9029/tap`](https://github.com/Aayush9029/homebrew-tap)*
