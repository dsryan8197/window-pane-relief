The 32-second ad (images/ad.gif). Open ad.html in a browser to watch it live.

To re-render:

    DUR=32 node capture.mjs ad.html /tmp/wpr-frames 30
    ffmpeg -framerate 30 -i /tmp/wpr-frames/f%04d.png -vf "fps=12,scale=900:-1:flags=lanczos,split[a][b];[a]palettegen=max_colors=128:stats_mode=diff[p];[b][p]paletteuse=dither=bayer:bayer_scale=5:diff_mode=rectangle" ../../images/ad.gif
    ffmpeg -framerate 30 -i /tmp/wpr-frames/f%04d.png -vf scale=1920:1080:flags=lanczos -c:v libx264 -pix_fmt yuv420p -crf 18 -movflags +faststart window-pane-relief-ad.mp4

For a review copy with a timer in the corner: `Q='&stamp' node capture.mjs ...`.
