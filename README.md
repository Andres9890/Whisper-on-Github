# Whisper on Github

A GitHub template repository for automatic audio file transcription using OpenAI's Whisper on Github, powered by GitHub Actions

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
[![Transcribe Audio with Whisper](https://github.com/Andres9890/Whisper-on-Github/actions/workflows/transcript.yml/badge.svg)](https://github.com/Andres9890/Whisper-on-Github/actions/workflows/transcript.yml)

## Features

- Automatic transcription when audio files are pushed to the repo
- Support for multiple audio formats (MP3, WAV, etc)
- Manual workflow dispatch with custom settings
- Organized transcript output with github artifacts
- Customizable Whisper model selection (tiny to large)
- Zero-config setup

## Quick Start

1. **Use this template** to create your own repository
2. **Add audio files** to the `audio/` directory
3. **Push to GitHub** - transcription happens automatically
4. **Download transcripts** from the workflow artifacts

## Supported Audio Formats

- MP3 (`.mp3`)
- WAV (`.wav`)
- M4A (`.m4a`)
- FLAC (`.flac`)

## Available Whisper Models

| Model  | Parameters | Relative Speed | Accuracy | Use Case |
|--------|------------|----------------|----------|----------|
| tiny   | 39M        | ~32x           | Good     | Quick preview & testing |
| base   | 74M        | ~16x           | Better   | General use (default) |
| small  | 244M       | ~6x            | Good     | Balanced speed/quality |
| medium | 769M       | ~2x            | High     | High-quality transcription |
| large  | 1550M      | ~1x            | Highest  | Maximum accuracy |

## How to Use

### Automatic Transcription

1. Put your audio files in the `audio/` directory:
   ```
   audio/
   ├── sample.mp3
   ├── sample.wav
   └── sample.m4a
   ```

2. Commit and push file(s) to trigger the workflow:
   ```bash
   git add audio/
   git commit -m "Add audio files for transcription"
   git push
   ```

3. Check the Actions tab for progress and download the transcripts from the github artifacts

### Manual Transcription

You can manually trigger transcription for specific files:

1. Go to the "Actions" tab in your repository
2. Select "Transcribe Audio with Whisper"
3. Click "Run workflow"
4. Select:
   - **Audio path**: Path to your audio file (default is `audio/sample.mp3`)
   - **Model**: Whisper model to use (default is `base`)

## Workflow Details

The GitHub Action workflow:

- Triggers on pushes to the `audio/` directory
- Can be manually triggered with custom settings
- Installs Python 3.9 and the required dependencies
- Uses FFmpeg for audio processing
- Uploads results as workflow artifacts

## Transcript Outputs

Whisper generates multiple output formats:

- `.txt` - Plain text transcript
- `.vtt` - WebVTT subtitles
- `.srt` - SRT subtitles
- `.tsv` - Tab-separated values with timing
- `.json` - Detailed JSON with word-level timestamps

## Configuration

### Modifying the Workflow

Edit `.github/workflows/transcript.yml` to customize:

- Trigger conditions
- Default model settings
- Output formats
- Additional processing steps

### Changing Default Model

Modify the workflow file to use a different default model:

```yaml
default: 'medium'  # You can change from base to any whisper model
```

## Repository Structure

```
whisper-template/
├── .github/
│   └── workflows/
│       └── transcript.yml    # Main workflow
├── audio/                    # audio files here
│   └── (your audio files)
├── transcripts/             # Output directory
├── .gitattributes
├── LICENSE
└── README.md
```

## Troubleshooting

### Workflow Not Triggering

- Ensure audio files are in the `audio/` directory
- Check if that file extensions are supported
- Verify the workflow syntax in `.github/workflows/transcript.yml`

### Transcription Quality Issues

- Try a larger model (e.g., `medium` or `large`) for better accuracy
- Ensure audio quality is good (clear speech, minimal background noise)
- Check if that the audio format is properly supported

### Large File Handling

- GitHub has a file size limit of 25MB on web (100MB if you use the [Git command line](https://git-scm.com/book/en/v2/Getting-Started-The-Command-Line))
- For larger files, consider using [Git LFS](https://docs.github.com/en/repositories/working-with-files/managing-large-files/configuring-git-large-file-storage)
- The `large` model requires more processing time and memory

## Performance Tips

1. **Start with smaller models** for testing, then upgrade for better results
2. **Batch process** multiple files for efficiency
3. **Clean audio** makes better transcriptions
4. **Consider costs**, larger models consume more GitHub Actions minutes (if it's a private repository)

## Contributing

Feel free to improve this template by:

1. Fork the repo
2. Make a pull request

## License

Github On Whisper is licensed under the MIT License, see [`LICENSE`](LICENSE) for more details

## People of Honor

- [OpenAI Whisper](https://github.com/openai/whisper)
- [GitHub Actions](https://github.com/features/actions)

## Support

If issues happen:

1. Check the [Troubleshooting](#troubleshooting) section
2. Check the workflow logs in the Actions tab
3. Open an issue about your problem

---

Made with ❤ and 🧻 by Andres99 using GitHub Actions
