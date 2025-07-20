# Drowsiness & Yawn Detection System

This project implements a real-time drowsiness and yawn detection system using OpenCV, dlib, imutils, and a Raspberry Pi with a buzzer alert. The system uses facial landmarks to detect the eye aspect ratio (EAR) and mouth aspect ratio (MAR) to determine drowsiness (eye closure) and yawning events, providing a physical alert via a buzzer.

## Features

- **Drowsiness Detection**: Monitors the eye aspect ratio (EAR) to detect when eyes are closed for a prolonged period.
- **Yawn Detection**: Monitors the mouth aspect ratio (MAR) to detect yawning.
- **Real-Time Video Processing**: Uses camera feed (e.g., Raspberry Pi camera) for live analysis.
- **Buzzer Alert**: Activates a buzzer when drowsiness or yawning is detected.
- **Visual Feedback**: Displays EAR and MAR values on the video feed with alerts.

## Requirements

- Python 3.x
- [OpenCV](https://pypi.org/project/opencv-python/)
- [dlib](https://pypi.org/project/dlib/)
- [imutils](https://pypi.org/project/imutils/)
- [scipy](https://pypi.org/project/scipy/)
- [RPi.GPIO](https://pypi.org/project/RPi.GPIO/) (on Raspberry Pi)
- `shape_predictor_68_face_landmarks.dat` (Download [here](http://dlib.net/files/shape_predictor_68_face_landmarks.dat.bz2))

## Hardware

- Raspberry Pi (with GPIO support)
- Camera (USB or Pi camera module)
- Buzzer connected to GPIO pin 18

## Usage

1. **Connect the buzzer** to GPIO pin 18 on your Raspberry Pi.
2. **Download** `shape_predictor_68_face_landmarks.dat` and place it in the same directory as `code.py`.
3. **Install dependencies**:
    ```bash
    pip install opencv-python dlib imutils scipy RPi.GPIO
    ```
4. **Run the script**:
    ```bash
    python code.py
    ```
5. **ESC key** in the display window to exit.

## How It Works

- The script initializes the camera and facial landmark predictor.
- It calculates EAR and MAR for each detected face.
- If EAR drops below a threshold for a set number of frames, it triggers a drowsiness alert.
- If MAR rises above a threshold, it triggers a yawn alert.
- Both alerts activate the buzzer and display warning text on the video feed.

## Adjustable Parameters

- `EAR_THRESH`: Threshold for eye aspect ratio to detect closed eyes (default: 0.25)
- `EAR_CONSEC_FRAMES`: Number of consecutive frames EAR must be below threshold to trigger drowsiness (default: 20)
- `MAR_THRESH`: Threshold for mouth aspect ratio to detect yawning (default: 0.7)

You can tweak these parameters for better accuracy depending on your setup and camera.

## Notes

- Ensure your camera is working and accessible via OpenCV (`VideoCapture(0)`).
- The script supports only a single buzzer for alerts.
- Stop the script safely with `CTRL+C` or the ESC key to ensure GPIO is cleaned up.

## License

This project is provided as-is for educational and research purposes.
