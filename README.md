
# WhisperX Audio Transcription

This repository contains a Jupyter Notebook designed for processing and transcribing audio files using the WhisperX library. The notebook includes features for handling audio files, converting phoneme dictionaries, and managing transcription data.

## Features

- **Audio File Processing:** The notebook processes `.mat` and `.wav` files, extracting relevant audio data for transcription.
- **Phoneme Dictionary Conversion:** Converts a phoneme dictionary from `.txt` format to `.csv`.
- **Directory Management:** Automatically creates directories for storing output files.
- **Error Handling:** Includes basic error handling to manage missing files or directories.
- **Integration with WhisperX:** Uses WhisperX for advanced audio transcription.

## Requirements

- Python 3.x
- Jupyter Notebook or Google Colab
- Google Drive (for cloud storage)
- Libraries: `os`, `csv`, `scipy`, `numpy`, `matplotlib`, `librosa`, `pandas`, `soundfile`, `whisperx`, `whisper`

## Setup

1. **Clone the repository:**

   ```bash
   git clone https://github.com/your-username/WhisperX.git
   ```

2. **Install the required libraries:**

   Use pip to install the necessary Python libraries:

   ```bash
   pip install git+https://github.com/m-bain/whisperx.git
   pip install git+https://github.com/openai/whisper.git
   ```

3. **Change Runtime to T4 GPU (Google Colab):**

   - Go to `Runtime` > `Change runtime type`
   - Set the `Hardware accelerator` to `GPU`
   - Ensure the `GPU type` is set to `T4` for optimal performance.

4. **Run the Colab Notebook:**

   Open the notebook file (`WhisperX.ipynb`) in Google Colab.

5. **Install Additional Dependencies:**

   If you are using Google Colab, run the following command to install additional dependencies:

   ```python
   !pip install -r "requirements.txt" #Add own path to requirements.txt
   ```

6. **Configure Google Drive:**

   If you are using Google Colab, make sure to mount your Google Drive to access and save files:

   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```

## Logic and Code Flow

### 1. **Audio File Processing**

The notebook processes audio files, primarily `.wav` and `.mat` formats. The main function responsible for this is `audio_trans(filepath)`. This function performs the following steps:

- **Extracts Filename and Paths:**
  - The function extracts the base filename and constructs paths for saving output files.
  - It checks for the existence of directories and creates them if they don’t exist.

- **Phoneme Dictionary Handling:**
  - The function converts a given phoneme dictionary from a `.txt` file to a `.csv` file, making it easier to handle.
  - It skips lines that do not conform to the expected format (word followed by phoneme).

- **File Processing:**
  - The function handles `.mat` files, extracting audio data and saving them in the designated directory.
  - For `.wav` files, it checks if the corresponding `.mat` file exists, processes the audio, and saves the `.wav` file.

- **Transcription with WhisperX:**
  - The notebook uses the WhisperX library to transcribe audio files, extracting words, phonemes, and their corresponding time offsets and probabilities.

### 2. **Phoneme Dictionary Conversion**

The notebook includes logic to handle a phoneme dictionary, converting it from a text file to a CSV format. This is done within the `audio_trans` function:

- **Reads the `.txt` file:**
  - The phoneme dictionary is read line by line.
  - Each line is split into a word and its corresponding phoneme.

- **Writes to a `.csv` file:**
  - The word-phoneme pairs are written to a CSV file.
  - Lines that don't conform to the expected format are skipped, ensuring data integrity.

### 3. **Error Handling and Directory Management**

The notebook includes logic to ensure smooth operation, even when files or directories are missing:

- **Directory Creation:**
  - If the target directories for storing `.mat`, `.wav`, and CSV files do not exist, the notebook automatically creates them.
  
- **File Existence Check:**
  - Before processing, the notebook checks whether necessary files exist to prevent runtime errors.
  - If a file is missing, an appropriate message is displayed.

### 4. **Visualization and Analysis**

The notebook may include sections for visualizing the phoneme data or analyzing the audio files. Common tools for this might include `matplotlib` for plotting or `librosa` for audio analysis.

## Usage

- **Audio File Transcription:**
  - Use the `audio_trans(filepath)` function to process and transcribe audio files located at the specified `filepath`.

- **Phoneme Dictionary Conversion:**
  - The phoneme dictionary is automatically converted from `.txt` to `.csv` format during the transcription process.

## Output

- **Processed Files:**
  - The processed `.mat` and `.wav` files are saved in newly created directories under the specified parent directory.

- **Phoneme CSV:**
  - The phoneme dictionary is saved as a `.csv` file in the designated directory.


