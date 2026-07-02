# Face Mask Detection

This project uses a trained TensorFlow model and OpenCV face detection to classify whether a person is wearing a face mask from a webcam feed. It also drives Arduino outputs to indicate the detection state with LEDs and a buzzer.

## Project Files

- `mask_detector.ipynb` - main notebook for loading the model and running live detection
- `StandardFirmata/StandardFirmata.ino` - Arduino sketch for Firmata-based control
- `StandardFirmata/pitches.h` - helper header used by the Arduino sketch

## What You Need

- Python 3.8+
- Jupyter Notebook or JupyterLab
- OpenCV
- TensorFlow
- NumPy
- PyFirmata
- Pyttsx3
- An Arduino board connected over USB
- A webcam

## External Assets

The notebook expects these files or equivalent paths to be available:

- `Untitled/by_Ankush.h5` - trained mask detection model
- `haarcascade_frontalface_default.xml` - OpenCV Haar cascade for face detection

If your files are stored elsewhere, update the paths inside `mask_detector.ipynb`.

## Arduino Setup

1. Upload `StandardFirmata/StandardFirmata.ino` to the Arduino board.
2. Confirm the correct COM port in the notebook.
3. Update the pin numbers in the notebook if your wiring is different.

The notebook currently uses:

- `D2` for the buzzer
- `D7` for the yellow LED
- `D12` for the red LED

## Python Dependencies

Install the required packages with:

```bash
pip install tensorflow opencv-python numpy pyfirmata pyttsx3
```

## Run the Notebook

1. Open `mask_detector.ipynb` in Jupyter.
2. Run the cells in order:
   - import libraries
   - load the model
   - initialize the Arduino connection
   - start the webcam detection loop
3. Press `Esc` in the video window to stop the loop.

## Notes

- The notebook uses `cv2.VideoCapture(0)` in one cell and `cv2.VideoCapture(1)` with a fallback to `0` in another, so you may need to adjust the camera index for your system.
- The notebook assumes the model outputs `1` for `No Mask` and `0` for `Mask`.
- If the notebook is run without the Arduino connected, the pin-write cells will fail.

