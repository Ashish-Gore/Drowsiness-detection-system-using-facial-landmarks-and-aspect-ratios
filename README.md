# Drowsiness-detection-system-using-facial-landmarks-and-aspect-ratios
A basic implementation of a drowsiness detection system using facial landmarks and aspect ratios. The system triggers an alert if it detects signs of drowsiness, such as closed eyes or an open mouth, for a consecutive number of frames.


## Project objectives:
The primary objective of this project is to implement a real-time drowsiness detection system using computer vision techniques. The system aims to enhance safety by identifying signs of drowsiness in individuals, particularly when operating vehicles or engaging in activities that require sustained attention.


## The Key Features of the project are:

- Monitors facial landmarks, specifically eyes and mouth, in real-time video frames.
- Computes eye aspect ratio (EAR) and mouth aspect ratio (MAR) to detect signs of drowsiness.
- Draws contours around eyes and mouth for visual representation.
- Triggers an alert when consecutive frames exhibit drowsiness conditions.
- Adjustable thresholds for eye and mouth conditions.


## Implementation:

Here's a breakdown of the code:

### 1. Importing Libraries:

`scipy.spatial.distance`: Used for computing distances between points.

`imutils.face_utils`: Contains utility functions for working with facial landmarks.

`imutils`: Provides convenience functions for OpenCV operations.

`dlib`: A library for machine learning, computer vision, and image processing.

`cv2`: OpenCV, a popular computer vision library.

### 2. Defining Helper Functions:

`eye_aspect_ratio(eye)`: Computes the eye aspect ratio (EAR) given the coordinates of the eye landmarks.

`mouth_aspect_ratio(mouth)`: Computes the mouth aspect ratio (MAR) given the coordinates of the mouth landmarks.

### 3. Setting Thresholds and Constants:

`thresh_eyes`: Threshold for detecting drowsiness based on eye aspect ratio.

`thresh_mouth`: Threshold for detecting an open mouth based on mouth aspect ratio.

`frame_check`: Number of consecutive frames for which the conditions must be met to trigger an alert.

Facial landmark indices for left eye (`lStart`, `lEnd`), right eye (`rStart`, `rEnd`), and mouth (`mStart`, `mEnd`).

### 4. Initializing Video Capture and Flags:

`cap`: Captures video from the default camera (index 0).

`flag_eyes` and `flag_mouth`: Counters for consecutive frames where drowsiness conditions are met.

### 5. Main Loop:

- Continuously captures frames from the video stream.
- Resizes each frame for efficient processing.
- Converts the frame to grayscale for face detection.
- Uses the dlib face detector to identify faces in the frame.
- For each detected face:
  - Retrieves facial landmarks using the shape predictor.
  - Computes eye aspect ratio (EAR) and mouth aspect ratio (MAR).
  - Draws contours around the eyes and mouth on the frame.
  - Checks if drowsiness conditions are met, increments counters, and displays an alert if conditions persist for a certain number of frames.
  - Resets counters if conditions are not met.
  - 
### 6. Displaying the Result:

- Shows the processed frame with contours and alerts.
- Pressing "q" exits the program.

  
### 7. Cleanup:

- Destroys all OpenCV windows and releases the video capture object when the program is terminated.


## Usage:

In the given code, EAR (Eye Aspect Ratio) and MAR (Mouth Aspect Ratio) are used as metrics to assess the state of a person's eyes and mouth, respectively. These ratios are computed based on the spatial relationships between specific facial landmarks.

<img src="https://github.com/Ashish-Gore/Drowsiness-detection-system-using-facial-landmarks-and-aspect-ratios/blob/main/assets/Facial%20Landmarks.png"/>

**Facial landmarks Detection output on input Image:**

<img src="https://github.com/Ashish-Gore/Drowsiness-detection-system-using-facial-landmarks-and-aspect-ratios/blob/main/assets/Detected%20Landmarks.png"/>

### Eye Aspect Ratio (EAR):
The Eye Aspect Ratio is a measure that helps quantify the openness of the eyes. It is calculated using the formula:

<img src="https://github.com/Ashish-Gore/Drowsiness-detection-system-using-facial-landmarks-and-aspect-ratios/blob/main/assets/EAR_Aspect%20ratio.png"/>


Where:

- v,z,w,y,u,x are specific landmarks corresponding to the eye.
- ∣v−z∣ represents the vertical distance between the upper and lower eyelids.
- ∣w−y∣ represents the horizontal distance between the inner and outer corners of the eye.
- ∣u−x∣ represents the diagonal distance between the top-left and bottom-right corners of the eye.
The EAR is used as a reliable indicator of eye closure. A lower EAR indicates closed eyes, while a higher EAR corresponds to open eyes. In the context of drowsiness detection, a significant decrease in EAR may suggest that the person's eyes are closing, indicating drowsiness or fatigue.


### Mouth Aspect Ratio (MAR):
The Mouth Aspect Ratio is a measure that quantifies the width of the mouth relative to its height. The formula for MAR is:

<img src="https://github.com/Ashish-Gore/Drowsiness-detection-system-using-facial-landmarks-and-aspect-ratios/blob/main/assets/MAR_Aspect%20ratio.png"/>


Where:

- t,z,u,y,v,x are specific landmarks corresponding to the mouth.
- ∣s−w∣ represents the horizontal distance between the corners of the mouth.
- ∣t−z∣ ∣u−y∣ ∣v−x∣ represents the vertical distance between the upper and lower lips.

A higher MAR indicates a more open mouth, and a lower MAR suggests a closed or partially closed mouth. In the drowsiness detection context, an increase in MAR may indicate yawning, which is often associated with drowsiness.

## Application in the Code:
The code uses these ratios to monitor the eyes and mouth of a person in real-time video frames. If the computed EAR falls below a certain threshold or the MAR exceeds a specified threshold for a certain number of consecutive frames, the system triggers an alert, as this behavior is indicative of potential drowsiness. Adjusting the threshold values allows for customization based on specific use cases or preferences.



### Real Time Output Sleepy state:

<img alt="GIF" src="https://github.com/Ashish-Gore/Drowsiness-detection-system-using-facial-landmarks-and-aspect-ratios/blob/main/assets/Sleepy%20state.gif" />

### Real Time Output Yawning state:

<img alt="GIF" src="https://github.com/Ashish-Gore/Drowsiness-detection-system-using-facial-landmarks-and-aspect-ratios/blob/main/assets/Yawning%20State.gif" />



## Contributions:
Contributions to this project are welcome. If you have suggestions, improvements, or bug fixes, please submit a pull request.

## License:
This project is licensed under the GNU General Public License.

## Acknowledgments:
We would like to express our gratitude to the open-source community and the developers of Dlib, OpenCV, SciPy for their contributions to computer vision. 

Feel free to customize the above sections according to your project specifics.
