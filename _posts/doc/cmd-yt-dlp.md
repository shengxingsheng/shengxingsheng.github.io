---
layout: post
title: yt-dlp
date: 2025-06-01 14:02 +0800
description:
image:
category: []
tags: []
published: false
sitemap: false
---



```bash
yt-dlp --cookies ../www.bilibili.com_cookies.txt -F "https://www.bilibili.com/video/BV1FMkqYHEmK"
yt-dlp -f "bestvideo[fps<=40]+bestaudio" --cookies ../www.bilibili.com_cookies.txt --output "%(title)s.%(ext)s" --sub-lang "all" --write-sub --convert-subs srt --embed-thumbnail --add-metadata --merge-output-format mp4 "https://www.bilibili.com/video/BV1BU411Z7u5"

yt-dlp --cookies www.bilibili.com_cookies.txt --list-subs "https://www.bilibili.com/video/BV1BU411Z7u5"
下载自动生成字幕档的指令：
yt-dlp --output "%(title)s.%(ext)s" --write-auto-subs --write-sub --convert-subs srt --embed-thumbnail --add-metadata --merge-output-format mp4 "https://www.bilibili.com/video/BV1GoHdeZEaU"
yt-dlp --cookies space.bilibili.com_cookies.txt --output "%(title)s.%(ext)s" --write-auto-subs --write-sub --convert-subs srt --skip-download "https://www.bilibili.com/video/BV1GoHdeZEaU"
只下载字幕档不下载影片的指令
yt-dlp --cookies www.bilibili.com_cookies.txt --output "%(title)s.%(ext)s" --sub-lang "all" --write-sub --convert-subs srt --skip-download "https://www.bilibili.com/video/BV1BU411Z7u5"

yt-dlp -f "bestvideo[fps<=40]+bestaudio" --cookies ../www.bilibili.com_cookies.txt --output "%(title)s.%(ext)s" --batch-file urls.txt  --sub-lang "all" --write-sub --convert-subs srt --embed-thumbnail --add-metadata --merge-output-format mp4


```

## 字幕

1. 因为Youtube有时候会有自动生成的字幕，不只一国语言，建议先用参数--list-subs列出可下载的字幕：

```bash
yt-dlp --list-subs "https://www.youtube.com/watch?v=NzTEZgFEr9k" --cookies ../../cookie/cookie_yt.txt 
```

2. 对照Language的栏位，找到要的字幕代号后，下载影片，用--sub-lang选取「正体中文」的字幕，并转成srt档

```bash
yt-dlp --output "%(title)s.%(ext)s" --sub-lang en --write-sub --convert-subs srt --embed-thumbnail --add-metadata --merge-output-format mp4 "https://www.youtube.com/watch?v=FfgT6zx4k3Q" --cookies ../../cookie/cookie_yt.txt 

```

下载自动生成字幕档的指令：

```bash
yt-dlp --output "%(title)s.%(ext)s" --write-auto-subs --write-sub --convert-subs srt --embed-thumbnail --add-metadata --merge-output-format mp4 "https://www.youtube.com/watch?v=FWI9GEwJNzc" --cookies ../../cookie/cookie_yt.txt 

```

只下载字幕档不下载影片的指令：

```shell
#下载指定字幕档 不下视频
yt-dlp --cookies ../../cookie/cookie_yt.txt  --output "%(title)s.%(ext)s" --sub-lang all --write-sub --convert-subs srt --skip-download "https://www.youtube.com/watch?v=ohJCdihPWqc"
# 下载自动生成字幕档 不下视频
yt-dlp --output "%(title)s.%(ext)s" --write-auto-subs --write-sub --convert-subs srt --skip-download "https://www.youtube.com/watch?v=NzTEZgFEr9k" --cookies ../../cookie/cookie_yt.txt 

```

下载所有字幕+视频

```shell
yt-dlp --cookies ../../cookie/cookie_yt.txt  --output "%(title)s.%(ext)s" --sub-lang all --write-sub --convert-subs srt --embed-thumbnai --merge-output-format --add-metadata -f "bestvideo[height<=1080]+bestaudio" --merge-output-format mp4 "https://www.youtube.com/watch?v=duZDsG3tvoA"

https://www.youtube.com/watch?v=FWI9GEwJNzc&list=PLbvnlSJNf_DYpgoG7UIkb0UAHegp6niLK&index=2
https://www.youtube.com/playlist?list=PLbvnlSJNf_DYpgoG7UIkb0UAHegp6niLK

--embed-thumbnail 加上Youtube上的縮圖
--merge-output-format mp4指定轉檔為.mp4格式（也可以用.mkv格式）
--add-metadata 嵌入影片資訊
-f "bestvideo[height<=1080]+bestaudio[ext=m4a]"的參數，指定影片最大高度為1080。至於其他畫質，2160為4K，1080為1080p，720為720p，以此類推。
```





下载播放列表+字幕

```shell
yt-dlp 
--cookies "../cookie/cookie_yt.txt"  
--output "%(playlist)s/%(playlist_index)s. %(title)s.%(ext)s" 
--write-auto-subs --write-sub --convert-subs srt 
--embed-thumbnai --merge-output-format --add-metadata --merge-output-format mp4 -f "bestvideo[height<=1080]+bestaudio" 
"https://www.youtube.com/playlist?list=PLd9hCvj34W5gfXecA2uPRsKv9q5L5nQng"

PLd9hCvj34W5hWkRym8sljiEvEBJ1JGIu5
https://www.youtube.com/watch?v=FWI9GEwJNzc&list=PLd9hCvj34W5hWkRym8sljiEvEBJ1JGIu5
```

