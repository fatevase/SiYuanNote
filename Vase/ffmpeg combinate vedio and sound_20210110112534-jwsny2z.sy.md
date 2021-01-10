视频音频合并

FFmpeg -i /Users/fate/Downloads/wf.mp4  -i /Users/fate/Downloads/wf.mp3  -c:v copy -c:a aac -strict experimental -map 0:v:0 -map 1:a:0 /Users/fate/Downloads/output.mp4
{: id="20201120095601-rkqzd4t" type="doc"}
