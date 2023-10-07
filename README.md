# Audiobook Maker
This repo utilizes SOTA AI voice generation tools such as Tortoise and RVC to generate the audio required to make an audiobook.  To my knowledge, Tortoise and RVC combined replicates speech in a way that is currently unparalleled to anything else that exists out there that is open-sourced and able to be ran locally. *Eleven labs is absolutely fantastic... one of the best IMO, but it's not "free" and it's not open-source*

To get this going is relatively installation heavy, but at this stage, I lack the proper skills and knowledge needed to get this packaged up and working in a way that is simply a one folder install.

## Features:
:heavy_check_mark: Sentence generation using Tortoise -> RVC

:heavy_check_mark: RVC AI Voice model compatibility (V1 & V2 as well as 40k & 48k trained models)

:heavy_check_mark: Generation of an entire text file with some basic sentence parsers and sorters

:heavy_check_mark: Selectively playback sentences by clicking and choosing them

:heavy_check_mark: Selectively regenerate audio for sentences by clicking and choosing them

:heavy_check_mark: Progress saving and continuing for audiobook generation in case of a crash or want to continue later

:heavy_check_mark: Audiobook loading from previous generations

:heavy_check_mark: Export of Audiobooks to a single wave file

:heavy_check_mark: Audiobook can be updated with a new text file in case sentences need to be changed or order adjusted

## To-do:
- [ ] Add additional languages (limited to only English ATM)
- [ ] Simpler installation, making it into release
- [ ] Add an option to convert audiobook to another voice 
- [ ] Find a way to do "multiple speakers" for dialogue in the book

## Prerequisites:
- **NVidia GPU:** I say this is a requirement as I've only developed testing with Nvidia.  The lowest I've tested is an RTX 3060 12B which is more than sufficient, but I reckon that 10 & 20 series cards should still be fine as well.
    - I don't have MAC or AMD so it would be a lot of guess-work for me to get this going and emulation won't work.
- CUDA 11.7
    - I believe even if you have CUDA 12.1, it might still be fine as long as you get the correct pytorch version 
- Python 3.10: https://www.python.org/downloads/release/python-31011/ 
- git: https://git-scm.com/downloads 
- mrq's Tortoise Fork: https://git.ecker.tech/mrq/ai-voice-cloning/wiki/Installation
    - YouTube video guide: https://youtu.be/6sTsqSQYIzs?si=0NYteSephE1ePiFg
    - Audio generation MUST be working as we will be calling tortoise via an API
- 7zip extractor
    - Download from here: https://www.7-zip.org/

# Package Installation
TBD

## Manual Installation:

1. Open a powershell/cmd window, clone, and then cd into the repo:
```
git clone https://github.com/JarodMica/audiobook_maker.git
cd audiobook_maker
```

2. Download and extract rvc to the audiobook_maker folder:
    - Link: https://huggingface.co/Jmica/rvc/resolve/main/rvc_lightweight.7z
        - Extract and double-click into ```rvc_lightweight```, and then copy the ```rvc``` folder into the ```audiobook_maker``` folder 
        - It should look like ```audiobook_maker/rvc``` and NOT like ```audiobook_maker\rvc_lightweight```
    - You can delete rvc_lightweight.7z and the folder once the copy is finished

3. Set-up and activate virtual environment
```
python -m venv venv
venv\Scripts\activate
```
4. Install pytorch using command below (recommended) or get from https://pytorch.org/get-started/locally/:

```pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu117```

5. Install requirements:

```pip install -r requirements.txt```

```pip install -r rvc/requirements.txt``` (if you get an error here, check to make sure you copied the rvc folder correctly)

```pip install https://huggingface.co/Jmica/rvc/resolve/main/fairseq-0.12.2-cp310-cp310-win_amd64.whl```

```pip install git+https://github.com/JarodMica/rvc-tts-pipeline.git@lightweight#egg=rvc_tts_pipe```

6. Download and install ffmpeg: https://ffmpeg.org/download.html
    - Place ffmpeg.exe and ffprobe.exe inside of audiobook_maker OR make sure they are in your environment path variable

7. Place whatever RVC AI voices (.pth) you want into the ```voice_models``` directory and indexes into ```voice_indexes```

## Acknowledgements
I am able to build these tools thanks to all of the fantastic open source repos out there, borrowing from different projects to get this all frankensteined and hashed together.  Without these, it wouldn't be possible for me to have gotten the functionality needed to create such a fantastic tool:
- mrq's AI Voice Cloning / Tortoise branch: https://git.ecker.tech/mrq/ai-voice-cloning
- Retrieval Based Voice Conversion: https://github.com/RVC-Project/Retrieval-based-Voice-Conversion-WebUI

And of course, this goes without saying, but ChatGPT has guided and helped me form my ideas into implementation.  The amount of time saved from using such a tool is unparalleled to any tool that I've ever used up until this point and the ability of it to turn sheer ideas into reality is absolutely mind boggling.  
