# AI Workout Form Corrector 💪

A real-time AI-powered workout form analyzer that uses computer vision to track and correct your exercise form for Squats and Push-ups.

## Features

- **Real-time Pose Detection**: Uses MediaPipe Pose to track 33 body keypoints
- **Automatic Rep Counting**: Counts reps based on joint angles and movement patterns
- **Form Feedback**: Provides instant corrections for:
  - Squat depth and knee angle
  - Push-up elbow angle and back alignment
  - Core engagement and posture
- **Live Webcam Feed**: Mirror view with skeletal overlay
- **Exercise Modes**: Switch between Squat and Push-up tracking

## Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/ai-workout-corrector.git
cd ai-workout-corrector

# Install dependencies
pip install -r requirements.txt

# Run the app
streamlit run app.py
```

## Requirements

- Python 3.8+
- Webcam
- Dependencies listed in `requirements.txt`

## How It Works

### Squat Mode
- **UP Position**: Knee angle > 160°
- **DOWN Position**: Knee angle < 80° (parallel or below)
- **Feedback**: Alerts if you're not going low enough

### Push-up Mode
- **UP Position**: Elbow angle > 160°
- **DOWN Position**: Elbow angle < 90°
- **Feedback**: 
  - Checks back alignment (hip sag detection)
  - Alerts if chest isn't low enough
  - Ensures proper plank position

## Technology Stack

- **Frontend**: Streamlit
- **Pose Detection**: MediaPipe Pose
- **Image Processing**: OpenCV
- **Math/Calculations**: NumPy

## Usage Tips

1. Position yourself so your full body is visible in the frame
2. Stand/position sideways to the camera for best angle detection
3. Ensure good lighting for optimal pose detection
4. Start with the "UP" position for each exercise

## License

MIT License - feel free to use and modify!

## Author

Qi-Han Wong - AI Product Manager specializing in GenAI Deployments
