# Natural Language Control of Robotic Manipulation

Agentic LLM robot control system using Google 
Gemini API function calling to interpret natural 
language commands and autonomously orchestrate 
computer vision, coordinate transformation, and 
robotic arm execution for pick-and-place operations.

## Demo Video
https://youtu.be/EdfE7P4P3jk?si=_yUq2r9TPfEgWQPP

## Results
| Metric | Value |
|--------|-------|
| Task Success Rate | 95% |
| Positioning Accuracy | ±2.5mm |
| Block Detection Accuracy | 100% |
| End-to-End Cycle Time | 12.3 seconds |
| Detection Speed | 0.3s per frame |
| LLM Processing Time | 1.2 seconds |
| Test Iterations | 20 |

## System Architecture
3-tool agentic pipeline orchestrated by Gemini API:

Tool 1: Computer Vision (OpenCV)
- HSV color space detection
- Connected component analysis
- Block centroid localization
- 100% detection accuracy

Tool 2: Coordinate Transformation
- Affine pixel-to-robot mapping
- Camera calibration with reference markers
- Sub-millimeter workspace accuracy
- ±2.5mm positioning precision

Tool 3: Robot Execution (PyDobot)
- Multi-step pick-and-place sequencing
- Safe Z-axis motion planning
- Suction cup gripper control
- Collision-free trajectory execution

## How It Works
1. User inputs natural language command
   Example: "pick the farthest red block 
   and place it over green"
   
2. Gemini API parses intent via function calling
   - Identifies target blocks
   - Determines spatial relationships
   - Generates tool call sequence

3. Vision tool captures and processes frame
   - Converts to HSV color space
   - Detects all colored blocks
   - Computes centroids and pixel coordinates

4. Coordinate tool transforms pixel to robot space
   - Applies affine transformation matrix
   - Maps camera view to robot workspace
   - Returns robot XY coordinates in mm

5. Robot executes pick-and-place sequence
   - Move above pickup location
   - Descend and activate suction
   - Lift and transport to target
   - Place and release
   - Return to home position

## Tech Stack
| Category | Tool |
|----------|------|
| LLM + Agent | Google Gemini API |
| Function Calling | Gemini Function Framework |
| Computer Vision | OpenCV |
| Robot Control | PyDobot |
| Hardware | Dobot Magician Arm |
| Math | NumPy |
| Language | Python |
| Camera | Webcam 640x480 |

## Supported Commands
- "Pick the farthest red block and place it over green"
- "Move home"
- "Take a picture and show blocks"
- "Stack blue on top of red"
- Any natural language manipulation command

## Hardware Setup
- Dobot Magician robotic arm
- USB webcam (bird's-eye view)
- 5 colored blocks (red, blue, green, yellow)
- Calibrated workspace surface

## Full Report
Complete IEEE format technical report with 
methodology, results, and analysis:
[final report.pdf](final%20report.pdf)

## Reference
- ASU RAS 545 - Robotics and Automation Systems
- Professor Sangram Redkar
- Arizona State University, Tempe AZ
