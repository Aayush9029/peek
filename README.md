<img src="assets/icon.png" width="128" alt="peek">

# peek

Describe images and videos from the terminal using vision LLMs.

## Install

```bash
brew install aayush9029/tap/peek
```

Requires `OPENROUTER_API_KEY` ([get one](https://openrouter.ai/keys)).
Video support requires `ffmpeg` (`brew install ffmpeg`).

## Usage

```bash
peek photo.png                          # describe an image
peek clip.mp4                           # describe a video
peek demo.mov --frames 10              # video with 10 frames
peek shot.png -m qwen72b -d detailed    # larger model, detailed description
peek ui.png -c "iOS settings screen"    # with context hint
peek image.png --name-only              # just the name
peek --list-models                      # list available models

# directory mode (images + videos)
peek ./screenshots                      # describe all files in dir
peek ./screenshots --rename             # describe + rename files
peek ./media -r -j 4                   # parallel recursive
```

Piped output is tab-separated (`name\tdescription`).

---

*More CLI tools: [`brew tap aayush9029/tap`](https://github.com/Aayush9029/homebrew-tap)*
