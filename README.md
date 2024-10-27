Here's an English adaptation of the GLM-4-Voice documentation with personalized clarity:

---

# GLM-4-Voice

GLM-4-Voice is an advanced end-to-end voice model by Zhipu AI, designed for real-time Chinese and English speech understanding and generation. It can perform live voice conversations, adjusting characteristics like emotion, tone, speed, and dialect according to user preferences. Here's a breakdown:

## Model Architecture

The GLM-4-Voice model is divided into three main components:
1. **GLM-4-Voice-Tokenizer**: Using [Whisper](https://github.com/openai/whisper) as a base, this tokenizer adds Vector Quantization, turning continuous audio into discrete tokens with only about 12.5 tokens needed per second of audio.
2. **GLM-4-Voice-Decoder**: Based on [CosyVoice](https://github.com/FunAudioLLM/CosyVoice) with Flow Matching, this decoder converts the tokens back into continuous speech. It’s optimized for low-latency conversations, needing just 10 tokens to start generating output.
3. **GLM-4-Voice-9B**: This builds on [GLM-4-9B](https://github.com/THUDM/GLM-4), aligning with audio training to handle both understanding and generating speech.

### Training Insights
To enhance intelligence and synthesis in speech, the model separates tasks: understanding spoken prompts and synthesizing responses. Pre-trained on vast datasets, GLM-4-Voice-9B can handle complex speech modeling with high precision.

### Alignment for Real-Time Dialogue
With a unique "streaming thinking" approach, the model uses text as a reference for quality control and delivers spoken responses that can adapt in tone and speed. It achieves high accuracy while remaining efficient, taking just 20 tokens to generate speech.

---

## Available Models

|         Model         | Type |                                                                     Download                                                                     |
|:---------------------:| :---: |:------------------------------------------------------------------------------------------------------------------------------------------------:|
| GLM-4-Voice-Tokenizer | Speech Tokenizer | [🤗 Huggingface](https://huggingface.co/THUDM/glm-4-voice-tokenizer) [🤖 ModelScope](https://modelscope.cn/models/ZhipuAI/glm-4-voice-tokenizer) |
|    GLM-4-Voice-9B     | Chat Model |                                          [🤗 Huggingface](https://huggingface.co/THUDM/glm-4-voice-9b) [🤖 ModelScope](https://modelscope.cn/models/ZhipuAI/glm-4-voice-9b)                                           
| GLM-4-Voice-Decoder   | Speech Decoder |                                        [🤗 Huggingface](https://huggingface.co/THUDM/glm-4-voice-decoder) [🤖 ModelScope](https://modelscope.cn/models/ZhipuAI/glm-4-voice-decoder)                                        

---

## Using GLM-4-Voice

### Web Demo Setup
A Web Demo allows direct interaction with the model. Just input text or voice, and it replies in both forms.

![Web Demo](./resources/web_demo.png)

#### Setup Steps

1. Clone the repository:
   ```shell
   git clone --recurse-submodules https://github.com/THUDM/GLM-4-Voice
   cd GLM-4-Voice
   ```
2. Install dependencies:
   ```shell
   pip install -r requirements.txt
   ```
3. Since the Decoder model doesn’t support `transformers`, download its checkpoint:
   ```shell
   git clone https://huggingface.co/THUDM/glm-4-voice-decoder
   ```

### Start the Demo
1. **Start Model Server**:
   ```shell
   python model_server.py --model-path glm-4-voice-9b
   ```
2. **Launch Web Service**:
   ```shell
   python web_demo.py
   ```
   Now you can access the demo at [http://127.0.0.1:8888](http://127.0.0.1:8888).

---

## Known Issues
- Gradio audio playback may be inconsistent during streaming but performs well after generation completion.

## Examples of GLM-4-Voice in Action

Examples include adjusting tone, speed, and dialect:

- Relaxing voice prompts for meditation
- High-energy narration for sports events
- A chilling voice for ghost stories

## Acknowledgments
GLM-4-Voice draws on work from:
- [CosyVoice](https://github.com/FunAudioLLM/CosyVoice)
- [transformers](https://github.com/huggingface/transformers)
- [GLM-4](https://github.com/THUDM/GLM-4)

---

With this personalized walkthrough, you’re set to try GLM-4-Voice and explore how it can be customized for your own use or for professional tools like EntrakitLLC. This AI marvel honors the original creators for their innovation, making it yours to build on from here.
