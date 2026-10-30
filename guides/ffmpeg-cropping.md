# FFmpeg and go2rtc cropping

The templates below preserve the source codec where possible and crop the combined vertical frame into two lens views. They assume the upper lens occupies the top half and the lower lens occupies the bottom half.

## Dimensions

| Source | Upper crop | Lower crop |
| --- | --- | --- |
| 640x720 substream | `crop=640:360:0:0` | `crop=640:360:0:360` |
| 2560x2880 main stream | `crop=2560:1440:0:0` | `crop=2560:1440:0:1440` |

If your image is rotated or the lenses are side-by-side, change the crop geometry after verifying a local frame.

## go2rtc example

```yaml
go2rtc:
  streams:
    q09_sub_upper:
      - "ffmpeg:rtsp://admin:<camera-password>@192.0.2.50:8554/stream1#video=h264#filter=crop=640:360:0:0"
    q09_sub_lower:
      - "ffmpeg:rtsp://admin:<camera-password>@192.0.2.50:8554/stream1#video=h264#filter=crop=640:360:0:360"
    q09_main_upper:
      - "ffmpeg:rtsp://admin:<camera-password>@192.0.2.50:8554/stream0#video=h264#filter=crop=2560:1440:0:0"
    q09_main_lower:
      - "ffmpeg:rtsp://admin:<camera-password>@192.0.2.50:8554/stream0#video=h264#filter=crop=2560:1440:0:1440"
```

The exact go2rtc release and FFmpeg build may require a slightly different template syntax. If the stream fails, test the equivalent command locally:

```bash
ffmpeg -rtsp_transport tcp -i 'rtsp://admin:<camera-password>@192.0.2.50:8554/stream1' -vf 'crop=640:360:0:0' -f null -
```

Do not expose the RTSP URL in logs or issue reports. Redact credentials and addresses first.
