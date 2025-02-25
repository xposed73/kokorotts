# **KOKORO TTS - Quick Start Guide**  

## **Installation**  

To set up a project using `uv`, follow these steps:  

```bash
uv init myProject -p 3.12.0
cd myProject
uv add kokoro
```

## **Usage Example**  

### **1. Create and edit `main.py`**  

Copy and paste the following code into `main.py`:  

```python
from kokoro import KPipeline
import soundfile as sf

# Language Code Options:
# 🇺🇸 'a' => American English  
# 🇬🇧 'b' => British English  
# 🇯🇵 'j' => Japanese (Requires: pip install misaki[ja])  
# 🇨🇳 'z' => Mandarin Chinese (Requires: pip install misaki[zh])  

pipeline = KPipeline(lang_code='b')  # Ensure the lang_code matches the selected voice  

# Sample text for demonstration
text = '''
Blaa, blaa, blaa, blaa....
'''

# Generate speech
generator = pipeline(
    text, voice='bf_lily',
    speed=1, split_pattern=r'\n+'
)

# Save each generated audio file
for i, (gs, ps, audio) in enumerate(generator):
    sf.write(f'{i}.wav', audio, 24000)
```

### **2. Run the script**  

Open your terminal and execute the following command:  

```bash
uv run main.py
```

This will generate audio files from the provided text.
