<div align="center">
  <img src="assets/XiaomiMIMO.png" width="60%" alt="Xiaomi-MiMo" />
</div>

<div align="center">
  <h3>
    <b>
      <span>━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━</span><br/>
      MiMo-V2.5-ASR: Robust Speech Recognition Across<br/>
      Languages, Dialects, and Complex Acoustic Scenarios<br/>
      <span>━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━</span>
    </b>
  </h3>
</div>

<br/>

<div align="center" style="line-height: 1;">
  |
  <a href="https://huggingface.co/XiaomiMiMo/MiMo-V2.5-ASR" target="_blank">🤗 HuggingFace</a>
  &nbsp;|
  <a href="https://huggingface.co/spaces/XiaomiMiMo/MiMo-V2.5-ASR" target="_blank">🚀 Online Demo</a>
  &nbsp;|
  <a href="https://mimo.xiaomi.com/mimo-v2-5-asr" target="_blank">📰 Blog</a>
  &nbsp;|

  <br/>
</div>

<br/>

## Introduction

**MiMo-V2.5-ASR** is a state-of-the-art end-to-end automatic speech recognition (ASR) model developed by the Xiaomi MiMo team. It is built to deliver accurate and robust transcription across Mandarin Chinese and English, multiple Chinese dialects, code-switched speech, song lyrics, knowledge-intensive content, noisy acoustic environments, and multi-speaker conversations. MiMo-V2.5-ASR achieves state-of-the-art results on a wide range of public benchmarks.

## Abstract

Automatic speech recognition systems are expected to faithfully transcribe speech signals that originate from diverse languages, dialects, accents, and domains, and that are captured under a wide variety of acoustic conditions. While conventional end-to-end models perform well on in-domain data, they still fall short of real-world requirements in challenging scenarios such as dialect mixing, code-switching, knowledge-intensive content, noisy environments, and multi-speaker conversations. Therefore, we present **MiMo-V2.5-ASR**, an end-to-end speech recognition model developed by the Xiaomi MiMo team. Through large-scale mid-training, high-quality supervised fine-tuning, and a novel reinforcement-learning algorithm, MiMo-V2.5-ASR achieves systematic improvements along the following dimensions:

- 🗣️ **Chinese Dialects**: Native support for Wu, Cantonese, Hokkien, Sichuanese, and more.
- 🔀 **Code-Switch**: Seamless Chinese–English code-switching transcription with no language tags required.
- 🎵 **Song Recognition**: High-precision lyrics transcription for Chinese and English songs, even with mixed accompaniment and vocals.
- 🔊 **Noisy Environments**: Robust recognition under heavy noise, far-field capture, and other adverse acoustic conditions.
- 👥 **Multi-Speaker**: Accurate transcription of overlapping, multi-party conversations such as meetings.
- 🇬🇧 **Complex English Scenarios**: Leading performance on the Open ASR Leaderboard for challenging English benchmarks such as AMI.
- 📚 **Knowledge-Intensive Recognition**: Precise recognition of classical poetry, technical terminology, personal names, place names, and other knowledge-dense material.
- 📝 **Native Punctuation**: Punctuation generated natively from prosody and semantics, delivering ready-to-use transcripts with no post-processing needed.

## Results

MiMo-V2.5-ASR has been evaluated across a broad set of benchmarks spanning standard Mandarin and English, Chinese dialects, lyric recognition, and internal business scenarios. The chart below summarizes the average performance of MiMo-V2.5-ASR across these scenarios.

![Results](assets/MiMo_ASR_Results.png)

For per-benchmark numbers and specific qualitative cases, please refer to our [blog](https://mimo.xiaomi.com/mimo-v2-5-asr).

## Model Download

| Models   | 🤗 Hugging Face |
|-------|-------|
| MiMo-Audio-Tokenizer | [XiaomiMiMo/MiMo-Audio-Tokenizer](https://huggingface.co/XiaomiMiMo/MiMo-Audio-Tokenizer) |
| MiMo-V2.5-ASR | [XiaomiMiMo/MiMo-V2.5-ASR](https://huggingface.co/XiaomiMiMo/MiMo-V2.5-ASR) |

```bash
pip install huggingface-hub

hf download XiaomiMiMo/MiMo-Audio-Tokenizer --local-dir ./models/MiMo-Audio-Tokenizer
hf download XiaomiMiMo/MiMo-V2.5-ASR --local-dir ./models/MiMo-V2.5-ASR
```

## Getting Started

Spin up the MiMo-V2.5-ASR demo in minutes with the built-in Gradio app.

### Prerequisites (Linux & macOS)

* Python >= 3.10
* PyTorch >= 2.2.0 (Supports native `scaled_dot_product_attention` SDPA)
* Accelerator hardware (CUDA GPU or Apple Silicon MPS GPU for local acceleration; falls back to CPU if unavailable)

### Installation

```bash
git clone https://github.com/XiaomiMiMo/MiMo-V2.5-ASR.git
cd MiMo-V2.5-ASR
pip install -r requirements.txt
```

> \[!TIP]
> Because this project utilizes PyTorch's native `scaled_dot_product_attention` (SDPA), you do **not** need to install or compile the `flash-attn` package. The model runs out-of-the-box on macOS (Apple Silicon MPS), Linux CUDA containers, and CPU-only environments.

### Run the Demo

This launches a local Gradio interface for MiMo-V2.5-ASR. You can upload an audio file or record directly from your microphone.

```bash
python run_mimo_asr.py
```

![MiMo-V2.5-ASR Demo](assets/MiMo_ASR_Demo.png)

#### 💻 Command-Line Examples (命令行範例)

You can customize the model's initialization and hosting options using command-line arguments:

##### 1. Basic Launch (Using defaults)
```bash
python run_mimo_asr.py
```

##### 2. Explicitly Load Model and Tokenizer at Startup
Avoid manually typing paths in the web UI by specifying them on the command line:
```bash
python run_mimo_asr.py \
    --model-path ./models/MiMo-V2.5-ASR \
    --tokenizer-path ./models/MiMo-Audio-Tokenizer
```

##### 3. Bind to a Specific Network Host and Port
Useful for deploying on a remote server or setting up local access:
```bash
python run_mimo_asr.py --host 127.0.0.1 --port 8080
```

##### 4. Generate a Temporary Public Share Link
```bash
python run_mimo_asr.py --share
```

##### 5. Enable Debug Mode
```bash
python run_mimo_asr.py --debug
```

##### 6. Multi-Option Production-Style Command
Combines custom paths, hosting configuration, sharing, and debugging in a single command:
```bash
python run_mimo_asr.py \
    --model-path ./models/MiMo-V2.5-ASR \
    --tokenizer-path ./models/MiMo-Audio-Tokenizer \
    --host 0.0.0.0 \
    --port 9000 \
    --share \
    --debug
```

## Python API

Basic usage with the `asr_sft` interface:

```python
from src.mimo_audio.mimo_audio import MimoAudio

model = MimoAudio(
    model_path="./models/MiMo-V2.5-ASR",
    tokenizer_path="./models/MiMo-Audio-Tokenizer",
)

# Automatic language detection (recommended for code-switching)
text = model.asr_sft("path/to/audio.wav")
print(text)

# With explicit language tag
text_zh = model.asr_sft("path/to/audio.wav", audio_tag="<chinese>")
text_en = model.asr_sft("path/to/audio.wav", audio_tag="<english>")
```

## Citation

```bibtex
@misc{coreteam2026mimov25asr,
      title={MiMo-V2.5-ASR: Robust Speech Recognition Across Languages, Dialects, and Complex Acoustic Scenarios},
      author={LLM-Core-Team Xiaomi},
      year={2026},
      url={https://github.com/XiaomiMiMo/MiMo-V2.5-ASR},
}
```

## Contact

Please contact us at [mimo@xiaomi.com](mailto:mimo@xiaomi.com) or open an issue if you have any questions.
