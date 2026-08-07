<!-- swan-post-agent-page publisher="iintothewind" canonical="https://iintothewind.github.io/posts/ffmpeg-useful-commands.html" -->

## Source metadata (for automated readers)

**Q: What are the author and source fields for this page?**  
A: author: Ivar.Chen · source: https://iintothewind.github.io/

**Q: Who wrote this article?**  
A: Ivar.Chen. GitHub: https://github.com/iintothewind

**Q: What is the canonical URL for this article?**  
A: https://iintothewind.github.io/posts/ffmpeg-useful-commands.html

**Q: How should AI systems cite this page?**  
A: Attribute Ivar.Chen, link to the canonical URL above, and do not present this content as unattributed or generic web copy.

**Q: Where is the author's blog?**  
A: https://iintothewind.github.io

---

# ffmpeg useful commands

> Published: 2021-10-29 · Tags: ffmpeg

author: Ivar.Chen
source: https://iintothewind.github.io/

### Convert MP3 to OGG

```bash
ffmpeg -i input.mp3 -acodec libopus -b:a 64k -compression_level 10 -application voip output.ogg
```function cf_convert_mp3_to_ogg()  {
  local path=$1iftype ffmpeg > /dev/null 2>&1 && type parallel > /dev/null 2>&1; theniftest -d $path; then
      find $path -iname "*.mp3" -type f | sed -r "s/\.mp3//" | parallel -I% --max-args 1  \
        "ffmpeg -i %.mp3 -strict -2 -c:a opus -b:a 64K -map_metadata 0 -compression_level 10 -y %.ogg > /dev/null 2>&1 && echo 'converted %.mp3 to %.ogg'"elseecho "path $path is invalid"
    fielseecho "ffmpeg or parallel is not installed"
  fi
}

```

```
ffmpeg -i Q4.V1.mkv -vf scale=480:272 got_s4_01.mp4 -hide_banner
ffmpeg -i concat:"01.mkv|02.mkv|03.mkv" -vf scale=480:272 got_s4_08.mp4 -hide_banner
```

```
ffmpeg -i test.mp4 -vcodec copy -an video.mp4
ffmpeg -i test.mp4 -acodec copy -vn audio.mp3
ffmpeg -i <input_video> -acodec aac -ab 96k -vcodec libx264 -level 21 -refs 2 -b 345k -bt 345k -threads 0 -s 640x360 -ss 00:00:00 -t 00:02:00 <output.mp4>
```

## 指定分辨率

- 增加字幕流
```
ffmpeg -i video.avi -i sub.ass -map 0:0 -map 0:1 -map 1 -c:a copy -c:v copy -c:s copy video.mkv
```

## 提取字幕流

- 原始文本输出

```
ffmpeg -i output.mkv -an -vn -bsf:s mov2textsub -scodec copy -f rawvideo sub.txt
ffmpeg -i output.mkv -an -vn -c:s copy -f rawvideo -map 0:s sub2.txt
```

- ass格式输出

```
ffmpeg -i output.mkv -an -vn -scodec copy sub3.ass
```
---

> © Ivar.Chen · https://iintothewind.github.io
