# display file properties
```bash
ffmpeg -i file -hide_banner	# -i = input
# ffmpeg -i vedio_file.mp4 -hide_banner
# ffmpeg -i audio_file.mp3 -hide_banner
```
# display supported formats
```bash
ffmpeg -formats

ffmpeg -formats -hide_banner	# display main information only
```
# convert
```bash
ffmpeg -i (-qscale 0) input output_1 output_2 ... output_3	# -qscale 0 : used for vedio -> vedio and want to gain high quality veideos
# ffmpeg -i input.mp4 output.avi
# ffmpeg -i input.webm output.flv
# ffmpeg -i input.mp3 output.ogg
# ffmpeg -i input.wav output.flac 
# ffmpeg -i input.wav output_1.mp3 output_2.ogg
```
# extract提取
## extract a audio from a vedio
### For bitrate,  the output audio = the original file 
```zsh
ffmpeg -i vedio -vn audio
```
### specify the bitrate, sampling rate, number of channels and for the output audio
```zsh
ffmpeg -i vedio -vn -ar 44100 -ac 2 -ab 128k audio
# -vn : vedio no = rm the vedio of the vedio
# -ar : audio sampling rate, common value = 22050, 441000, 480000
# -ab : audio bitrate, common value = 96k, 128k, 256k, 320k
# -ac : audio channel, common value = 1, 2
```
## extract pictures from a vedio
```zsh
ffmpeg -i -r n -f image_format image_output
# -r n : extract n images per second
# image_output: if ~ = image-%3d.png, the suffix后缀 of image_output will have three numbers, like 001, 002   
```
# mute静音 the vedio
```zsh
ffmpeg -i vedio_input -an vedio_output
# -an : audio no = rm the audio of the vedio
``` 
# change vedio resolution分辨率 or aspect ratio长宽比
## resolution
```zsh
ffmpeg -i vedio_input -s 640×480 -c:a vedio_output
```
## aspect ratio
```zsh
ffmpeg -i vedio_input -aspect 4:3 vedio_output
```
# rotate the vedio
## upside-down
```zsh
ffmpeg -i input -vf "rotate=PI"
```
## rotate n degrees
```zsh
ffmpeg -i input -vf "rotate=n*PI/180"
```

# convert all .mp4 in the current directory to .wav
```zsh
for file in *.mp4;
	do ffmpeg -i "$file" "${file%.mp4}.wav";
done
```
