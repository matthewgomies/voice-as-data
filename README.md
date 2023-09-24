# voice-as-data
Voice features extraction

1. Video and Audio Extraction
The initial phase of our voice analysis started with the collection of various video and audio files
for processing. We collected the Golden Balls recordings from YouTube and obtained Real-life Trial
Data video clips from the University of Michigan’s Language and Information Technologies website.
Numerous third-party online extractors are available for obtaining video and audio recordings from
YouTube and thus we were able to collect a portion of the Golden Balls recordings directly in WAV
audio format. While, for the files originally collected in video format (MP4 format), we utilized
the multi-platform audio editor Audacity® to extract the audio clips. We processed all these video
recordings by converting them into audio clips (WAV format) with a frequency of 16,000 Hz, a bit
rate of 128 kbps, and in mono channel format.

2. Cleaning Audio Clips
After compiling the audio clips, our next step involved cleaning them by utilizing Audacity®.
To achieve this, we first removed any voices that did not originate from the primary speaker. This
included manually editing the audio recordings to trim sections where voices other than the main
speaker’s were present (i.e., the host’s voice in GB, the judges’, attorneys’ and prosecutors’ voice
in RT). Next, we addressed background noise in the Golden Balls audio clips by performing noise
reduction process. This involved selecting a sample of the background music and applying the noise
reduction method to the entire Golden Balls audio clips. We configured the noise reduction settings
as follows: DB: 25, Sensitivity: 6, and Frequency Smoothing: 3. And lastly, we also normalized
the volume of the audio clips by using the same application with the setting of perceived loudness
-23 LUFS (treating mono as dual mono and treating stereo independently).
8

3. Main Voice Features
After cleaning the audio clips, we proceeded to extract the main acoustic features for our
analysis. To obtain these, we employed a Python library called Parselmouth, which emulates
PRAAT (program for the analysis and reconstruction of acoustic speech signals). Our extraction
encompassed key voice attributes, including Pitch (Fundamental Frequencies, F0), Harmonic-to-
Noise Ratio, Voice Perturbation (Shimmer and Jitter), as well as an additional set of four formants.
Moreover, to provide an approximate quantification of intonation, we used the standard deviation of
fundamental frequencies as a measure of pitch variation. For a detailed explanation of the settings
used to obtain these features, please refer to Appendix A1.

4. Additional Features
Additional features that could be extracted from the audio clips include the voice emotion and
the scripted speech (only for Golden Balls audio clips). We used Voice Emotion AI, Empath, to
automatically detect four emotions: joy, calmness, anger, and sorrow from real-time speech in any
language, even in high-noise environments. We also extracted the energy levels present in the
voice using the same application. We then selected two most distinct variables among the four:
calm (positive, low intensity) and anger (negative, high intensity) for our analysis. These emotion
parameters were extracted from the first 5 seconds of each audio clip.
Additionally, we also collected scripted text from the Golden Balls audio clips using the IBM
Speech to Text algorithm to extract initial transcripts for each audio. These transcripts were then
manually refined due to limitations in the automatic conversion capability.
Lastly, we conducted sentiment analysis on the transcripts for Golden Balls and Real-life trial
data using the Valence Aware Dictionary and Sentiment Reasoner (VADER) tool in Python.
VADER is a lexicon and rule-based sentiment analysis tool specifically designed for texts and
is accessible through a Python library. It accepts a text input and provides a dictionary of scores
in four categories: negative, neutral, positive, and compound. The positive, negative, and neutral
scores reflect the proportion of text falling into these categories, while the compound score is a
normalized value ranging from -1 to 1.
