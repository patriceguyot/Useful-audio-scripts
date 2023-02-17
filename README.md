# Useful-audio-scripts


## Get whole duration of folders and subfolders with sound files

"""
afinfo **/*.wav | awk '/estimated duration/ { print $3 }' | paste -sd+ - | bc | awk '{printf("%d:%02d:%02d:%02d\n",($1/60/60/24),($1/60/60%24),($1/60%60),($1%60))}'
"""
