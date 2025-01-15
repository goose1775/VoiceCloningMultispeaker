# Voice Cloning Multispeaker

## Descrição do Projeto

O **Voice Cloning Multispeaker** é um sistema automatizado para dublagem utilizando técnicas modernas de manipulação de áudio, transcrição e tradução, bem como modelos de voz neural. Este projeto é capaz de realizar desde a extração de áudio e legendas até a criação de áudios personalizados e sincronizados com base em locutores distintos.

## Principais Funcionalidades

1. **Extração de Áudio e Legendas**:
   - Extração de legendas e trilhas de áudio de arquivos de vídeo.
   - Conversão para formatos padronizados (e.g., `.wav` e `.srt`).

2. **Processamento de Áudio**:
   - Separar fontes de áudio (diálogos, músicas, efeitos sonoros) utilizando o **Demucs**.
   - Diagnóstico da qualidade do áudio segmentado.

3. **Diarização de Locutores**:
   - Identificação e separação de locutores em arquivos de áudio.
   - Alinhamento automático entre segmentos de diálogos e legendas traduzidas.

4. **Transcrição e Tradução**:
   - Utiliza o modelo **Whisper** para transcrever e traduzir segmentos de áudio.
   - Suporte a vários idiomas e melhoria de precisão através de beam search.

5. **Geração de Áudio Personalizado**:
   - Criação de áudios dublados com **VITS Multilingual**.
   - Suporte para múltiplos locutores e idiomas.

6. **Mixagem de Áudio e Vídeo**:
   - Alinhamento de trilhas dubladas com a trilha original.
   - Adição de legendas ao vídeo final.

## Estrutura do Projeto

- `data/`: Diretório para armazenamento de arquivos de entrada e saída.
- `src/`: Contém os scripts Python para processamento de dados, transcrição e geração de áudio.
- `models/`: Diretório para armazenar modelos pré-treinados ou treinados durante o projeto.

## Requisitos

- Python >= 3.9
- GPU com suporte CUDA (recomendado)

### Dependências

Instale as dependências utilizando o comando abaixo:
```bash
pip install -r requirements.txt
```

### Principais Pacotes
- `torch`, `torchaudio`, `TTS`
- `ffmpeg-python`, `pydub`
- `openai-whisper`
- `pyannote.audio`
- `moviepy`

## Como Executar

### 1. Extração de Áudio e Legendas
```python
from src.audio_processing import extract_and_convert_audio
extract_and_convert_audio("video.mkv", "output_dir")
```

### 2. Processamento de Áudio
```python
from src.audio_processing import separate_sources
separate_sources("input_audio.wav", "output_dir", "demucs_model")
```

### 3. Diarização de Locutores
```python
from src.speaker_diarization import diarize_speakers
segments = diarize_speakers("vocals.wav", hf_token="YOUR_HF_TOKEN")
```

### 4. Transcrição e Tradução
```python
from src.transcription import transcribe_and_translate_hf
results = transcribe_and_translate_hf(model, processor, device, "audio.wav", segments)
```

### 5. Geração de Áudio
```python
from src.audio_generation import generate_audio_directly_with_vits
generate_audio_directly_with_vits(segments, tts_model, "output_dir")
```

### 6. Mixagem de Áudio e Vídeo
```python
from src.video_processing import replace_audio_in_video
replace_audio_in_video("input_video.mp4", "final_audio.wav", "output_video.mp4")
```

## Contribuições

Contribuições são bem-vindas! Por favor, abra uma issue ou envie um pull request com melhorias.

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).


