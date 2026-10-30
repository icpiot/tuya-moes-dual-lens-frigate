# MOES ZC-ZK Q09

This is the dedicated guide for the MOES ZC-ZK Q09 vertically stacked dual-lens camera.

## Known connection values

| Setting | Value |
| --- | --- |
| RTSP username | `admin` |
| ONVIF username | `admin` |
| RTSP port | `8554` |
| ONVIF service port | `5000` |
| Main stream path | `/stream0` |
| Substream path | `/stream1` |
| Substream source size | 640x720 |
| Main source size | 2560x2880 |

The password is the camera password chosen during setup. It is intentionally represented by `<camera-password>` in this repository.

## Recommended Frigate layout

Use the substream crops for detection and the main-stream crops for recording only after testing resource usage. The included [frigate.yml](frigate.yml) has two independent cameras, `q09_upper` and `q09_lower`, each with a detection crop and a recording crop.

## Important verification note

The crop geometry and dual-camera arrangement are verified for the Q09 workflow. Full-resolution recording from the main stream is **unverified** in this public guide. Test playback, retention, CPU load, and reconnects before enabling it permanently.

## Setup checklist

1. Pair the camera in Tuya/Smart Life and set a local camera password.
2. Confirm the camera's address locally; do not publish it.
3. Confirm RTSP and ONVIF access with username `admin`.
4. Add the go2rtc streams from the example configuration.
5. Check the upper and lower crops independently.
6. Start with detection on the 640x360 crops.
7. Trial the 2560x1440 recording crops and confirm that recordings are valid.
