# text-to-talk

Video toolkit for Claude Code.

## Skills (`.claude/skills/`)
- `moneyprinterturbo-video` — topic → finished short video (MoneyPrinterTurbo, macOS/Windows).
- HyperFrames core skills v0.9.41 (`hyperframes`, `hyperframes-cli`, `hyperframes-registry`,
  `media-use`, `reverse-any-video`, `style-sampling`) — HTML/three.js compositions rendered to video.
  Copied from heygen-com/hyperframes tag v0.9.41; keep in sync with the `hyperframes` version in package.json.

## Setup
```sh
npm install                                    # hyperframes CLI + three.js
uv venv .venv && uv pip install -p .venv -r requirements.txt   # Kokoro TTS (kokoro-onnx)
export HYPERFRAMES_PYTHON=$PWD/.venv/bin/python
npx hyperframes doctor                         # checks ffmpeg, Chrome, Kokoro
```
ffmpeg/ffprobe must be on PATH (system package).

## Tools
- Voiceover (Kokoro, on device): `npx hyperframes tts "text" -o voice.wav -v af_heart`
- Sound effects (Openverse → mostly Freesound, no key; bundled fallback offline):
  `npx hyperframes media-use resolve --type sfx --intent "whoosh"`
- three.js: `import * as THREE from "three"`; drive it from HyperFrames time (see
  `.claude/skills/hyperframes/references/runtimes.md`), no requestAnimationFrame clock.
