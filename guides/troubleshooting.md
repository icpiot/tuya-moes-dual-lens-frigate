# Troubleshooting

## Authentication fails

- Confirm the camera password locally.
- Use username `admin` for both RTSP and ONVIF in the Q09 workflow.
- Check that the URL is quoted and that special characters in a password are URL-encoded.
- Do not paste the URL into a public issue; redact it first.

## ONVIF discovery finds nothing

- Confirm the camera and client are on the same local network.
- Try the ONVIF service port `5000` explicitly.
- Check whether the camera firmware has ONVIF enabled.
- Frigate does not require ONVIF after you know the RTSP URL.

## Crop is shifted or black

- Confirm whether the source is 640x720 or 2560x2880.
- Verify the lens boundary with a local frame.
- Check that the lower crop starts at `y=360` for 640x720 or `y=1440` for 2560x2880.
- If the camera is side-by-side or rotated, use different crop geometry.

## Frigate detects but does not record

- Confirm the recording input is reachable from Frigate.
- Check that the main crop actually decodes in go2rtc.
- Start with substream-only recording to isolate resource usage.
- Full-resolution recording is unverified by this repository; confirm playback before relying on it.

## CPU or storage is too high

- Use the 640x360 crops for detection.
- Lower detection FPS.
- Prefer hardware decoding where supported.
- Trial one main crop at a time before enabling both.

## What to include in a report

Include model, firmware version, source dimensions, sanitized crop command, and the symptom. Remove passwords, IP addresses, hostnames, MAC addresses, timestamps that identify your household, unrelated cameras, MQTT settings, and raw logs.
