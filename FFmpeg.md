## YouTube

1、下载最佳视频和音频，并自动合并

```sh
yt-dlp -f "bv*+ba/b" [视频链接]
```

2、合并视频

```sh
ffmpeg -i 视频.mp4 -i 音频.mp3 -c:v copy -c:a copy 合并视频.mp4
```

3、1440p 或者 2160p 视频

```sh
ffmpeg -i video.webm -i audio.m4a -c:v copy -c:a copy output.mkv
```

```sh
ffmpeg -i video.webm -i audio.m4a -c:v libx264 -c:a copy out.mp4
```

```sh
ffmpeg -i video.m4a -ab 128000 -vn music.mp3
```

## 安装 FFmpeg

### Fedora

1、查询是否已安装 RPM Fusion

```sh
dnf repolist | grep rpmfusion
```

2、安装 RPM Fusion

```sh
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
```

```sh
sudo dnf install https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

3、安装 ffmpeg

```sh
sudo dnf install ffmpeg
```

### Ubuntu

```sh
sudo apt install ffmpeg
```

### Arch

```sh
sudo pacman -S ffmpeg
```

### 查询版本，确认是否安装成功

```sh
ffmpeg -version
```

### 显示文件信息

```sh
ffmpeg -i 文件
```

### 视频格式转换

```sh
ffmpeg -i input.mkv -vcodec copy -acodec copy output.mp4
```

或者

```sh
ffmpeg -i input.mkv -c:v copy -c:a copy output.mp4
```

### 编码

- 默认

```sh
ffmpeg -i input.mkv -c:v libx264 output.mp4
```

- 显卡加速

```sh
ffmpeg -i input.mkv -c:v h264_nvenc output.mp4
```

### 禁用

- 禁用音频

```sh
ffmpeg -i input.mp4 -an output.mp4
```

- 禁用视频

```sh
ffmpeg -i input.mp4 -vn output.mp3
```

- 禁用字幕

```sh
ffmpeg -i input.mp4 -sn output.mp4
```

### 合并（分两步）

1、先消音

```sh
ffmpeg -i input.mp4 -vcodec copy -an output.mp4
```

2、再合并

```sh
ffmpeg -i output.mp4 -i input.mp3 -vcodec copy -acodec copy new_output.mp4
```

## ffmpeg -h

```sh
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Getting help:
    -h      -- print basic options
    -h long -- print more options
    -h full -- print all options (including all format and codec specific options, very long)
    -h type=name -- print all options for the named decoder/encoder/demuxer/muxer/filter/bsf/protocol
    See man ffmpeg for detailed description of the options.

Print help / information / capabilities:
-L                  show license
-h topic            show help
-? topic            show help
-help topic         show help
--help topic        show help
-version            show version
-buildconf          show build configuration
-formats            show available formats
-muxers             show available muxers
-demuxers           show available demuxers
-devices            show available devices
-codecs             show available codecs
-decoders           show available decoders
-encoders           show available encoders
-bsfs               show available bit stream filters
-protocols          show available protocols
-filters            show available filters
-pix_fmts           show available pixel formats
-layouts            show standard channel layouts
-sample_fmts        show available audio sample formats
-dispositions       show available stream dispositions
-colors             show available color names
-sources device     list sources of the input device
-sinks device       list sinks of the output device
-hwaccels           show available HW acceleration methods

Global options (affect whole program instead of just one file):
-loglevel loglevel  set logging level
-v loglevel         set logging level
-report             generate a report
-max_alloc bytes    set maximum size of a single allocated block
-y                  overwrite output files
-n                  never overwrite output files
-ignore_unknown     Ignore unknown stream types
-filter_threads     number of non-complex filter threads
-filter_complex_threads  number of threads for -filter_complex
-stats              print progress report during encoding
-max_error_rate maximum error rate  ratio of decoding errors (0.0: no errors, 1.0: 100% errors) above which ffmpeg returns an error instead of success.
-vol volume         change audio volume (256=normal)

Per-file main options:
-f fmt              force format
-c codec            codec name
-codec codec        codec name
-pre preset         preset name
-map_metadata outfile[,metadata]:infile[,metadata]  set metadata information of outfile from infile
-t duration         record or transcode "duration" seconds of audio/video
-to time_stop       record or transcode stop time
-fs limit_size      set the limit file size in bytes
-ss time_off        set the start time offset
-sseof time_off     set the start time offset relative to EOF
-seek_timestamp     enable/disable seeking by timestamp with -ss
-timestamp time     set the recording timestamp ('now' to set the current time)
-metadata string=string  add metadata
-program title=string:st=number...  add program with specified streams
-target type        specify target file type ("vcd", "svcd", "dvd", "dv" or "dv50" with optional prefixes "pal-", "ntsc-" or "film-")
-apad               audio pad
-frames number      set the number of frames to output
-filter filter_graph  set stream filtergraph
-filter_script filename  read stream filtergraph description from a file
-reinit_filter      reinit filtergraph on input parameter changes
-discard            discard
-disposition        disposition

Video options:
-vframes number     set the number of video frames to output
-r rate             set frame rate (Hz value, fraction or abbreviation)
-fpsmax rate        set max frame rate (Hz value, fraction or abbreviation)
-s size             set frame size (WxH or abbreviation)
-aspect aspect      set aspect ratio (4:3, 16:9 or 1.3333, 1.7777)
-vn                 disable video
-vcodec codec       force video codec ('copy' to copy stream)
-timecode hh:mm:ss[:;.]ff  set initial TimeCode value.
-pass n             select the pass number (1 to 3)
-vf filter_graph    set video filters
-ab bitrate         audio bitrate (please use -b:a)
-b bitrate          video bitrate (please use -b:v)
-dn                 disable data

Audio options:
-aframes number     set the number of audio frames to output
-aq quality         set audio quality (codec-specific)
-ar rate            set audio sampling rate (in Hz)
-ac channels        set number of audio channels
-an                 disable audio
-acodec codec       force audio codec ('copy' to copy stream)
-vol volume         change audio volume (256=normal)
-af filter_graph    set audio filters

Subtitle options:
-s size             set frame size (WxH or abbreviation)
-sn                 disable subtitle
-scodec codec       force subtitle codec ('copy' to copy stream)
-stag fourcc/tag    force subtitle tag/fourcc
-fix_sub_duration   fix subtitles duration
-canvas_size size   set canvas size (WxH or abbreviation)
-spre preset        set the subtitle options to the indicated preset
```
