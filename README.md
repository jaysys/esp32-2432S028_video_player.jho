# esp32-2432S028_video_player


## Convert video of 16:9 aspect ratio to 4:3
ffmpeg -y -i input.mp4 -pix_fmt yuvj420p -q:v 7 -vf "transpose=1,fps=24,scale=-1:320:flags=lanczos" output.mjpeg

## Command for a horizontal video, scale the height to at least 320, then crop the center vertically (zoom occur)
ffmpeg -y -i .\wide_video.mp4 -pix_fmt yuvj420p -q:v 7 -vf "transpose=1,fps=24,scale=-1:320:flags=lanczos,crop=240:320:(in_w-240)/2:0" wide_video.mjpeg

## Command for a vertical video already of aspect ratio 4:3
ffmpeg -y -i cropped.mp4 -pix_fmt yuvj420p -q:v 7 -vf "fps=24,scale=240:320:flags=lanczos" scaled.mjpeg

## Command for a horizontal video already of aspect ratio 4:3
ffmpeg -y -i cropped_4x3.mp4 -pix_fmt yuvj420p -q:v 7 -vf "transpose=1,fps=24,scale=240:320:flags=lanczos" final_240x320.mjpeg
