# Tuya/MOES Dual-Lens Frigate

Community notes for vertically stacked, dual-lens Tuya/MOES cameras used with Frigate and go2rtc.

This repository documents a reusable pattern: keep the camera's combined stream as an input, use go2rtc/FFmpeg to crop the upper and lower lenses into separate virtual streams, and give each virtual stream its own Frigate camera. The example below uses the verified login name `admin`, but never includes a real password or private network address.

## Contents

- [General setup](guides/general-setup.md)
- [Verified MOES ZC-ZK Q09 guide](cameras/moes-zc-zk-q09/README.md)
- [Q09 example Frigate configuration](cameras/moes-zc-zk-q09/frigate.yml)
- [FFmpeg cropping](guides/ffmpeg-cropping.md)
- [Troubleshooting](guides/troubleshooting.md)
- [Compatibility](cameras/compatibility.md)

## Public-safe example values

| Item | Example |
| --- | --- |
| Camera address | `192.0.2.50` (documentation-only TEST-NET address) |
| RTSP username | `admin` |
| RTSP password | `<camera-password>` |
| RTSP port | `8554` |
| ONVIF username | `admin` |
| ONVIF service port | `5000` |
| Main stream | `/stream0` |
| Substream | `/stream1` |

Replace placeholders locally. Do not commit passwords, tokens, MQTT settings, household addresses, private IPs, logs, or complete personal Frigate configurations.

## Status

The MOES ZC-ZK Q09 stream layout and dual-lens crop workflow are verified in the contributor's setup. Exact camera firmware behavior varies. Full-resolution recording from the uncropped 2560x2880 source is **not independently verified** here; treat it as an experiment and confirm recordings locally before relying on it.

## License

MIT. See [LICENSE](LICENSE).
