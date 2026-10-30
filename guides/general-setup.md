# General setup

## 1. Confirm the camera stream

Use the camera's documentation or ONVIF discovery to find the RTSP service and stream paths. A common layout is:

```text
rtsp://admin:<camera-password>@192.0.2.50:8554/stream0
rtsp://admin:<camera-password>@192.0.2.50:8554/stream1
```

`admin` is the documented RTSP and ONVIF username for the supported Q09 workflow. The password is the one configured on your camera and must remain local.

Use an ONVIF client to confirm profiles, media URLs, and service port `5000`. ONVIF discovery is optional for Frigate; it is useful for finding the correct stream and validating credentials.

## 2. Identify the lens arrangement

Vertically stacked cameras commonly expose one combined frame. Check the stream dimensions and make a local test frame. If the frame is 640x720, each lens is typically 640x360. If the main frame is 2560x2880, each lens is typically 2560x1440. Verify the dividing line on your own camera before applying the crop.

## 3. Split the stream with go2rtc

Use the FFmpeg crop templates in [ffmpeg-cropping.md](ffmpeg-cropping.md). Keep the source URL local and use environment variables or a secrets file where supported. Do not place a real password in a tracked YAML file.

## 4. Add separate Frigate cameras

Create one Frigate camera per crop. A practical arrangement is:

- detection cameras use the 640x360 crops from the 640x720 substream;
- recording cameras can use the 2560x1440 crops from the 2560x2880 main stream, subject to CPU/storage testing;
- each camera has a distinct name and its own go2rtc stream.

The example Q09 configuration shows the complete structure.

## 5. Validate before relying on it

Check both crops in go2rtc, then run Frigate for a trial period. Confirm object detection, recording playback, timestamps, CPU load, storage growth, and camera reconnect behavior. Full-resolution recording is marked unverified in this repository until independently confirmed.
