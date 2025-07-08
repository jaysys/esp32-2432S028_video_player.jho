# Cheap Yellow Display Video Player (ESP32-2432S028)

<a href="https://www.buymeacoffee.com/thelastoutpostworkshop" target="_blank">
<img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee">
</a>

## Youtube Tutorial
>Make sure sure you have the board with the **ILI9341 Display controller** and not the ST7789 (parallel) Display controller, which is not supported by the graphics library

[<img src="https://github.com/thelastoutpostworkshop/images/blob/main/Cheay%20Yellow%20Display-3.png" width="500">](https://youtu.be/jYcxUgxz9ks)

## 🎬 How to Use These FFmpeg Commands

Each of the following commands generates a `.mjpeg` file — a Motion JPEG video format — from an input `.mp4` or `.mov` video, optimized for use in frame-by-frame playback with an SD card reader.

Make sure you have [FFmpeg](https://ffmpeg.org/download.html) installed and accessible from your terminal or command prompt.

---

## Convert video of 16:9 (horizontal) to aspect ratio to 4:3
```cmd
ffmpeg -y -i input.mp4 -pix_fmt yuvj420p -q:v 7 -vf "transpose=1,fps=24,scale=-1:320:flags=lanczos" output.mjpeg
```

## Convert video of 9:16 (vertical) to aspect ratio to 3:4
```cmd
ffmpeg -y -i input.mp4 -pix_fmt yuvj420p -q:v 7 -vf "fps=24,scale=-1:320:flags=lanczos" output.mjpeg
```
## Command for a horizontal video already of aspect ratio 4:3
```cmd
ffmpeg -y -i cropped_4x3.mp4 -pix_fmt yuvj420p -q:v 7 -vf "transpose=1,fps=24,scale=240:320:flags=lanczos" final_240x320.mjpeg
```

## Command for a vertical video already of aspect ratio 3:4
```cmd
ffmpeg -y -i cropped.mp4 -pix_fmt yuvj420p -q:v 7 -vf "fps=24,scale=240:320:flags=lanczos" scaled.mjpeg
```

### Options explained
- -pix_fmt yuvj420p: Ensures JPEG-compatible pixel format
- -q:v 7: Controls image quality (lower is better; 1 = best, 31 = worst)
- -vf: Specifies the video filters:
- fps=24: Extracts 24 frames per second
- scale: Resizes the video
- transpose=1: Rotates the video 90° clockwise
- .mjpeg: Output format used when streaming or storing a series of JPEG frames as a video