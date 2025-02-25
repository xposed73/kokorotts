# KOKORO TTS - Simple usage

# Installation

## create a project using uv

```bash
uv init myProject -p 3.12.0
cd myProject
uv add kokoro
```

## Sample code
### copy and paste this code inside main.py

```python
from kokoro import KPipeline
import soundfile as sf
# 🇺🇸 'a' => American English, 🇬🇧 'b' => British English
# 🇯🇵 'j' => Japanese: pip install misaki[ja]
# 🇨🇳 'z' => Mandarin Chinese: pip install misaki[zh]
pipeline = KPipeline(lang_code='b') # <= make sure lang_code matches voice

# This text is for demonstration purposes only, unseen during training
text = '''
Blaa, blaa, blaa, blaa....
'''
generator = pipeline(
    text, voice='bf_lily',
    speed=1, split_pattern=r'\n+'
)
for i, (gs, ps, audio) in enumerate(generator):
    sf.write(f'{i}.wav', audio, 24000) # save each audio file

```

### open your terminal and hit the command
```bash
uv run main.py
```
