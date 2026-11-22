# Sleep Detector (Windows)

A real-time drowsiness alarm. It uses your webcam to watch your eyes and plays a loud alarm if they stay closed for too long.

**Developer:** Abdulhamiid

## How it works

- Uses [MediaPipe](https://developers.google.com/mediapipe) Face Mesh to track facial landmarks.
- Calculates the **Eye Aspect Ratio (EAR)** for both eyes.
- If the EAR stays below the threshold for **2.5 seconds**, the alarm starts and the screen flashes red.
- The alarm stops as soon as you open your eyes.

## Features

- Live webcam view with a status banner (AWAKE / SLEEPING! WAKE UP!)
- Face tracking box with colour feedback (green = awake, red = alarm)
- On-screen EAR value and a progress bar showing how long your eyes have been closed
- Looping alarm sound using `pygame`

## Requirements

- Windows 10 / 11
- Python 3.9 or newer
- A webcam

## Installation

```bash
pip install -r requirements.txt
```

## Setup

Open `sleep_detector_windows.py` and check these settings near the top:

```python
EAR_THRESHOLD = 0.22        # lower = eyes must be more closed to trigger
EYE_CLOSED_SECONDS = 2.5    # seconds of closed eyes before the alarm
DISPLAY_SCALE = 0.75        # window size (1.0 = 1280x720)
ALARM_SOUND_FILE = "dragon-studio-censor-beep-3-372460.mp3"  # or a full path
```

Keep the alarm MP3 in the same folder as the script, or set `ALARM_SOUND_FILE` to its full path (for example `r"C:\Users\you\Downloads\alarm.mp3"`).

If the wrong camera opens, change the camera index in `cv2.VideoCapture(0, cv2.CAP_DSHOW)` (try `1`).

## Usage

```bash
python sleep_detector_windows.py
```

Press **Q** in the video window to quit.

## Troubleshooting

| Problem | Fix |
| --- | --- |
| "Cannot open webcam" | Close other apps using the camera, or change the camera index to `1`. |
| No alarm sound | Check the `ALARM_SOUND_FILE` path and your volume. Run `pip install --upgrade pygame`. |
| Alarm triggers too easily | Lower `EAR_THRESHOLD` (for example `0.20`) or raise `EYE_CLOSED_SECONDS`. |
| Alarm never triggers | Raise `EAR_THRESHOLD` (for example `0.25`) and make sure your face is well lit. |

## Credits

Developed by **Abdulhamiid**.
