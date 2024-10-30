# Mp3-to-MIDI

Made By Luke Borkowski

As a producer and musician, something I need to do suprisingly often is listen to an audio track and either find out what notes are being played, or change the sound of the instrument after recording it. To do both of these, I need to make a MIDI file that follows the performance of the recording by hand, drawing in every single note. After doing this for so long, I wondered if it was possible to automate the process with AI, and thus this project was born.

The project is designed to take an mp3 recording of any musical instrument being played and analize the pitches in the recording to create a MIDI file matching the recording. The code converts the mp3 into a spectogram, and runs the spectogram through a Neural Network trained to recognise the simmilarities between the image and an MIDI file's data. When I began this project, I was unsure of how I would go about this process, but coming off of finishing a previous AI project, I had a better idea of how to set up my data and had the mental framework to hit the ground running. 

For those unaware, a MIDI file is an instructional datafile that is used by digital instruments. It can be easily edited in any number of Digital Audio Workspaces, and is used to give instructions on what notes to play, when, how long, and how strong to play them. This is hugely helpful when writing music by letting any computer play any instrument, with customization of the performance or the instruemt at any point in the process.

I started on finding a good dataset to work with. I knew I would need a huge number of MIDI files with a wide range of complexity. Eventually I found a huge set of MIDI covers of real songs. In order to use the files, however, I would need the audio that they created as well. At first, I was considering downloading a dataset with the original audio from the songs that the MIDI covered. I soon realized, however, that there was a tool, "FluidSynth", that could record out a MIDI file and save it as a .wav file. This was very helpful, but the next issue I ran into was the size of the .wav file. Because it was uncompressed, each file took up upwards of 50MB. This filled up my Google Drive account, which was limited to only 15GB. To solve this, I added converter "AudioSegment" to convert the .wav file into a .mp3 file, and I deleted the .wav file. Once I had enough .mp3's, I began working on a way to correlate the music to the MIDI. While reaserching, I remembered Spectograms, which visualize audio by showing a 3D graph: Time along the X, pitch along the Y, and volume represented by color. If I could convert these Mp3 files into Spectograms, I could use an image processing Nearual Network, which is one of the most saturated field of AI developement at the moment. After finding a tool, "Librosa", which could develop a Spectogram from an Mp3, it was a matter of running through all of the data again with the Mp3s, adding the PNG of the spectogram to the data. 

The biggest issue I ran into during this project was the amount of time that the data collection took. The dataset I began with contained over 20,000 midi files, and each file took aproxx. 30 seconds of processing to create a mp3, and another 30 seconds to generate the spectogram. This added up to 334 hours of processing, which was only made harder by Google Colab's limited runtime per day, and frequent crashing. For this reason, I dont have as much data as I would have liked, and the project is still in progress.


- Objective: Convert MP3 recordings of musical instrument performances into MIDI files by analyzing pitches with a neural network that compares spectrogram images to MIDI data.

- Data Preparation: Chose a large dataset of MIDI files and generated corresponding audio files using "FluidSynth" to avoid dependence on original song recordings.

- File Management: Reduced file sizes by converting uncompressed WAV files to MP3 using "AudioSegment" to manage limited storage.

- Spectrogram Generation: Created spectrograms from MP3 files with "Librosa" to leverage image-processing neural networks trained to recognize audio-visual patterns.

- Challenges: Processing over 20,000 files for spectrogram and MP3 generation led to long runtimes and frequent interruptions on Google Colab, impacting data collection and progress.
