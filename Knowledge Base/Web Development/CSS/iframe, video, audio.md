## iframe

```html
<iframe id="inlineFrameExample"
    title="Inline Frame Example"
    width="300"
    height="200"
    src="https://www.openstreetmap.org/export/embed.html?bbox=-0.004017949104309083%2C51.47612752641776%2C0.00030577182769775396%2C51.478569861898606&layer=mapnik">
</iframe>

```

## video

```html
<video src="https://code.s3.yandex.net/web-developer/Web_sprint2_videos/Keyframes.mp4"></video>
```

Если браузер не поддерживает формат, то указываем дополнительные рессурсы

```html
<video width="320" height="240" controls>
     <source src="clip.mp4" type="video/mp4">
     <source src="clip.ogg" type="video/ogg">
     <!--if the mp4 format doesn't work, the browser will try the ogg format --> 
</video>
```

#### video element attributes
```html
<video autoplay></video>
<video controls></video>
<video loop></video>
<video muted></video>
<video src="URL"></video>
<video height="250px"></video>
<video width="250px"></video>
<video poster="/images/example.gif"></video>
```

## audio
You can use the `<audio>` tag to add sound to your webpage. This tag works with three audio formats: `.mp3`, `.wav`, and `.ogg`.

Если что-то не поддерживается:
```html
<audio>
   <source src="sound.mp3" type="audio/mp3">
   <source src="sound.ogg" type="audio/ogg">
   <!--if .mp3 files aren't compatible, a browser will try the .ogg format--> 
</audio>
```

#### audio element attributes

```html
<audio autoplay>
<audio controls>
<audio loop>
<audio muted>
<audio src="https://code.s3.yandex.net/audio-sample.mp3">
<audio type="audio/ogg">
```

## YouTube API
```html
<iframe id="ytplayer" type="text/html" width="720" height="405" src="https://www.youtube.com/embed/wsWYVhIFFCw?start=3" frameborder="0" allowfullscreen></iframe>
```