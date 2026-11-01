ffmpeg video to audio

  ffmpeg -i video-name.mp4 -vn -acodec libmp3lame -ab 256k audio-name.mp3

e.g.

ffmpeg -i mindful.mp4 -vn -acodec libmp3lame -ab 256k mindful.mp3

