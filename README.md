# **Color-Based Object Tracking**

This project demonstrates **real-time object tracking** using color detection with the **HSV (Hue-Saturation-Value)** color model.  
It is inspired by **self-driving concepts**, where object position and distance are interpreted to provide direction.

---

## Key Features
- Tracks objects based on selected color using HSV range.
- Provides directions like **Left, Right, Front, Stop** based on object position and size.
- Uses **OpenCV contours**, moments, and minimum enclosing circles for accurate tracking.
- Includes a **color calibration tool (`colorCalibrationforHSV.py`)** to find HSV values for any color.

---

## **Core Concepts & Formulas**

### 1. **Minimum Enclosing Circle**
```python
((x, y), radius) = cv2.minEnclosingCircle(contour)
```
### 2. Moments to Find Object Center
Image moments help compute the center of mass and other geometric features of an object:
```python
M = cv2.memonts(c)
center = (int(M["m10"]/M["m00"]), int(M["m01"] / M["m00"]))
```
## **HSV Color Scale**
* Hue: Represents the color type (0°–360°).
  Example: * Cyan: 181-240°
           * Magenta: 301–360°
* Saturation: Intensity of the color.
* Value: Brightness level.

Use colorCalibrationforHSV.py to determine the HSV range for your desired color, then use those values in ObjectTrackingBasedOnColor.py.

## **Direction Logic**
* Front → Object moves farther away.

* Stop → Object is very close (radius is large).

* Left → Object is on the left side of the frame.

* Right → Object is on the right side of the frame.
## **Steps to Run**

1. Capture frames from the camera.

2. Apply pre-processing (Gaussian blur + HSV conversion).

3. Detect contours based on the color mask.

4. Draw the minimum enclosing circle around the detected object.

5. Find the center of the contour area.

6. Draw the circle and center point.

7. Determine movement direction based on radius & position.

8. Run the code and view the output window.
## **Output**
* Real-time video with tracking circle and direction printed in the console.

* Check the media/ folder for recorded output samples.
## **Requirements**
```bash
pip install opencv-python imutils numpy pillow pyautogui
```
