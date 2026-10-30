# Compatibility

| Camera/model | Combined vertical stream | RTSP/ONVIF values | Status |
| --- | --- | --- | --- |
| MOES ZC-ZK Q09 | 640x720 substream and 2560x2880 main stream | `admin`, RTSP 8554, ONVIF 5000, `/stream0`, `/stream1` | Verified workflow; full-resolution recording unverified |
| Other Tuya/MOES dual-lens models | Must be measured per firmware | Varies | Unverified until a contributor supplies a redacted test report |

To add a model, include firmware-independent observations, stream dimensions, crop geometry, and test results. Never include private addresses, passwords, tokens, unredacted logs, or screenshots containing personal information.
