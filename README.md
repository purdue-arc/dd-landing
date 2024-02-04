# dd-landing
Drone Delivery Landing Repo

Problem: 
Find and land the drone on some space of land near the target location.

Solution:
Use the onboard Zed 2i camera, assorted sensors, and computer vision techniques to find a suitable area to land and minimize chances of an unsuccessful landing (possible collision or landing on unsuitable ground)

Step 1:
- Use sensors to identify a flat enough area to land

Step 2:
- Employ model to detect objects within the camera’s field of view

Step 3: Continuous Object Detection
- Identify objects that are either too close to the drone or may be moving towards the drone’s landing zone
- Land the drone when there is little collision risk
- Object tracking will be continuously checked as the drone lands
- The field of view will decrease, so the drone will attempt to both “predict” if an object might have entered its zone of landing as well as continuously checking if something has entered it’s landing area
- Zone Identification approach:
    - Use the depth sensor data to identify a flat enough area
    - The landing zone will be a predesignated area on the ground that we ideally want no objects to be within or to enter while the drone is landing
    - The landing zone can be created using OpenCV
- Object Tracking models
    - We have already pre built object detection models
        - These can be repurposed for object tracking
    - OpenCV provides functionality for object tracking
        - This could be a more lightweight solution
    - Custom tracking models
        - Could dig deeper into a custom made object detection/tracking model if other techniques are lacking
- Potential OpenCV Models
    - Rely on built-in zed 2i depth detection (seems to be very accurate and we have the jetson)
    - Plane Detection:
        - https://docs.opencv.org/4.x/dd/dd4/tutorial_detection_of_planar_objects.html
        - https://leomariga.github.io/pyRANSAC-3D/
        - Custom opencv application:
            - scan area within landing space and measure the “flatness” using the depth estimation/depth sensor of the zed 2i
