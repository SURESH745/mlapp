# Swoleboi 💪

A real-time deadlift form tracker and rep counter using computer vision and machine learning. Swoleboi analyzes your workout form through your webcam and provides instant feedback on your deadlift technique while automatically counting your repetitions.

## Features

- **Real-time Form Analysis**: Uses MediaPipe pose estimation to track your body movements
- **Automatic Rep Counting**: Intelligently counts deadlift repetitions based on movement patterns
- **Form Classification**: Distinguishes between "up" and "down" phases of the deadlift
- **Confidence Scoring**: Shows probability scores for movement classification
- **Live Video Feed**: Real-time camera feed with pose landmark visualization
- **Dark Mode UI**: Modern, easy-to-read interface built with CustomTkinter

## How It Works

1. **Pose Detection**: MediaPipe captures 33 body landmarks from your webcam feed
2. **Feature Extraction**: Landmark coordinates (x, y, z, visibility) are processed into feature vectors
3. **Machine Learning Classification**: A trained model classifies movements as "up" or "down" phases
4. **Rep Counting**: Tracks transitions from "down" to "up" positions to count completed reps
5. **Real-time Feedback**: Displays current stage, rep count, and confidence scores

## Requirements

- Python 3.7+
- Webcam/Camera
- Required Python packages:
  - `tkinter` (usually included with Python)
  - `customtkinter`
  - `pandas`
  - `numpy`
  - `pickle`
  - `mediapipe`
  - `opencv-python`
  - `Pillow`

## Installation

1. Clone this repository:
```bash
git clone <repository-url>
cd swoleboi
```

2. Install required dependencies:
```bash
pip install customtkinter pandas numpy mediapipe opencv-python Pillow
```

3. Ensure you have the trained model file (`deadlift.pkl`) in the project directory

## Usage

1. Run the application:
```bash
python app.py
```

2. Position yourself in front of your camera so your full body is visible
3. Start performing deadlifts - the app will automatically:
   - Track your form in real-time
   - Count your repetitions
   - Display confidence scores
4. Use the "RESET" button to reset the rep counter

## Interface Elements

- **STAGE**: Shows current movement phase ("up" or "down")
- **REPS**: Displays total repetition count
- **PROB**: Shows confidence probability of current classification
- **Video Feed**: Live camera feed with pose landmarks overlay
- **RESET Button**: Resets the repetition counter

## Technical Details

### Model Training
The application uses a pre-trained machine learning model (`deadlift.pkl`) that was trained on deadlift movement data. The model analyzes pose landmarks to classify movement phases.

### Pose Landmarks
The system tracks 33 body landmarks using MediaPipe, including:
- Face and head points
- Upper body (shoulders, elbows, wrists)
- Core and hip points
- Lower body (knees, ankles, feet)

### Classification Logic
- **Down Phase**: Detected when the model predicts "down" with >70% confidence
- **Up Phase**: Detected when transitioning from "down" to "up" with >70% confidence
- **Rep Count**: Incremented on each complete "down" to "up" transition

## Camera Configuration

The application is currently configured to use camera index 3:
```python
cap = cv2.VideoCapture(3)
```

You may need to adjust this value (typically 0, 1, or 2) depending on your system's camera setup.

## Troubleshooting

- **No camera feed**: Check camera permissions and try different camera indices (0, 1, 2)
- **Poor detection**: Ensure good lighting and full body visibility
- **Low accuracy**: Make sure you're performing standard deadlift form
- **Application crashes**: Verify all dependencies are installed correctly

## Future Enhancements

- Support for multiple exercise types
- Form correction suggestions
- Workout session tracking
- Performance analytics
- Mobile app version

## Contributing

Feel free to submit issues, feature requests, or pull requests to improve Swoleboi!

## License

This project is open source and available under the [MIT License](LICENSE).

---

**Disclaimer**: This application is for fitness tracking purposes only. Always consult with a qualified trainer for proper form instruction and safety guidelines.