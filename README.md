# LOQ - Speech-to-Text Hotkey for Linux

LOQ is a single script that provides an easy way to transcribe your speech to text using the OpenAI Whisper API. The script is designed to be bound to a hotkey in a Linux desktop environment but should work on macOS or the Windows Linux Subsystem as well.

## Setup Instructions:

1. **Clone this repository** to your desired location:
    ```bash
    git clone https://github.com/yourusername/loq.git
    cd loq
    ```

2. **Create a configuration file** named `keys` in your configuration directory `~/.loq` and add your OpenAI API key:
    ```bash
    mkdir -p ~/.loq
    echo "OPENAI_API_KEY=sk-YOUR_API_KEY" > ~/.loq/keys
    chmod 600 ~/.loq/keys
    ```

3. **Install the required dependencies**:
    - `sox` (`rec`): for audio recording
    - `lame`: for MP3 conversion
    - `curl`: for making HTTP requests
    - `xclip`: for clipboard manipulation
    - `xdotool`: for simulating keyboard input
    - `notify-send` and `gdbus`: for notifications

    You can install them all with:
    ```bash
    sudo apt install sox lame curl xclip xdotool libnotify-bin
    ```

4. **Set up key bindings** in your settings (e.g., keyboard settings on Ubuntu GNOME Shell) to run the `loq` script with the `toggle` subcommand when a particular key or key combination is pressed (e.g., F10).

5. **Make the script executable**:
    ```bash
    chmod +x loq
    ```

6. **Move the script to a directory in your PATH** (optional):
    ```bash
    sudo mv loq /usr/local/bin/
    ```

## Usage:

1. **Start or stop recording**: Press your hotkey to toggle recording your speech.
2. **Transcription process**: When you stop the recording, the transcription process will be triggered automatically.
3. **Clipboard**: The transcribed text will be automatically copied to your clipboard.
4. **Paste**: Paste the transcribed text into your desired application by using the appropriate keyboard shortcut (e.g., Ctrl+V).

### Directory Structure:
- `~/.loq/recordings`: Stores the recorded MP3 files.
- `~/.loq/transcripts`: Stores the transcriptions of the recordings.
- `~/.loq/stats`: Stores the statistics of the recordings.
- `~/.loq/tmp`: Temporary files for ongoing processes.
- `~/.loq/stats.tsv`: Aggregated statistics of all recordings.
- `~/.loq/loq.log`: Log file for errors and important messages.

## Customization:

You can modify the script to suit your specific needs. For example, you can change the audio recording format, bit rate, or other options in the `rec` command. Additionally, you can customize the keyboard shortcuts or add additional functionality to suit your workflow.

## Troubleshooting:

- If you encounter issues with the clipboard not pasting in GNOME Terminal or other applications, ensure that the necessary permissions are granted for clipboard access. You may also need to adjust the keyboard shortcut settings in your GNOME Shell configuration.
- If the automatic pasting doesn't work in your terminal, you might need to manually paste the transcribed text.

## Problems:

For some reason, automatic pasting might not work in some terminals. In such cases, you will have to manually paste the text.

## Contributing:

Contributions are welcome! Please feel free to open issues, submit pull requests, or suggest improvements to make LOQ even better.

Happy speaking and typing!
