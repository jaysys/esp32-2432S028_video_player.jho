# esp32-2432S028_video_player


The aspect ratio of the screen is 3:4 (240x320)
## Command for vertical video, scale the width to at least 240, then crop the center vertically.
ffmpeg -y -i .\lions.mp4 -pix_fmt yuvj420p -q:v 7 -vf "fps=24,scale=240:-1:flags=lanczos,crop=240:320:0:(in_h-320)/2" lions.mjpeg

## Command for a horizontal video
ffmpeg -y -i .\wide_video.mp4 -pix_fmt yuvj420p -q:v 7 -vf "transpose=1,fps=24,scale=-1:320:flags=lanczos,crop=240:320:(in_w-240)/2:0" wide_video.mjpeg

## Command for a video of aspect ratio 4:3
ffmpeg -y -i cropped.mp4 -pix_fmt yuvj420p -q:v 7 -vf "fps=24,scale=240:320:flags=lanczos" scaled.mjpeg
