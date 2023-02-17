# Useful-audio-scripts

This repository shows useful commands to process audio datasets. 

## I. Information / statistics


#### Get whole audio duration (.wav) of folders and subfolders:

```
afinfo **/*.wav | awk '/estimated duration/ { print $3 }' | paste -sd+ - | bc | awk '{printf("%d:%02d:%02d:%02d\n",($1/60/60/24),($1/60/60%24),($1/60%60),($1%60))}'
```

## II. Conversion


### Convert all MP3 files to wav (mono, 44.1kHz, 16bits) using sox:

```
for file in `ls *.MP3`; do echo 'convert ' $file ' into ' ${file%.*}.wav;  sox $file -r 44100 -c 1 -b 16 ${file%.*}.wav; done
```

### Convert all WMA files to wav (mono, 44.1kHz, 16bits) using ffmpeg:

```
for file in `ls *.WMA`; do echo 'convert ' $file ' into ' ${file%.*}.WAV;  ffmpeg -i $file ${file%.*}.WAV; done
```