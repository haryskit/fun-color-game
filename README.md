🧠 Fun Match Study: Adaptive Cognitive Load Assessment Game
This repository contains a single-file, interactive HTML/JavaScript application designed to measure the cognitive performance, sustained attention, and inhibitory control of young children (specifically 5-year-old and related age groups) for medical and functional analysis.
The core game is a simple "Color & Shape Match" task, but the underlying mechanism dynamically adjusts difficulty and logs detailed behavioral metrics to determine the player's Cognitive Load Ceiling.
✨ Key Features
Single-File Application: All HTML, CSS (Tailwind), and JavaScript are contained within index.html for easy deployment.
Adaptive Difficulty: The game dynamically increases the number of distractors (shapes on screen, ranging from 5 to 10) based on the child's real-time performance (accuracy and reaction time). This effectively identifies the point of cognitive overload.
Detailed Behavioral Logging: Every tap (correct or incorrect) is logged internally with timestamps, target attributes, and tapped attributes.
Firestore Integration: Securely saves player high scores and complete session logs (including raw click data and generated analysis) using Firebase Firestore.
Error Tolerance: The game ends after 3 misses, preventing excessive frustration and focusing the study on the critical error threshold.
📊 Behavioral Analysis Report
Upon game completion, a detailed report is generated to summarize the session's functional performance:
Core Performance Metrics
Accuracy: Overall percentage of correct taps.
Average Reaction Time (RT): Mean time taken to correctly tap the target.
Reaction Time Variability (Standard Deviation): A key metric indicating consistency of attention. High variability suggests fluctuating focus.
Error Attribution Analysis
Dominant Error Type: Identifies whether the majority of errors were due to difficulty recognizing the Color or the Shape.
Pure Color/Shape Errors: Tracks instances where only the color was wrong (shape was correct) or vice-versa, providing insight into which attribute caused the confusion.
Temporal & Specific Confusion
Reaction Time Trend: Compares the average RT of the first half versus the second half of the game to detect learning effects (improvement) or fatigue (worsening performance).
Most Confused Pair: Identifies the specific target/distractor pair (e.g., "Triangle -> Star") that led to the highest number of miss-taps.
🛠️ Setup and Running
The application is designed to run within an environment that provides Firebase initialization variables (such as the Google Canvas environment).
Clone the Repository:
git clone [your-repo-link]
cd fun-match-study


Deployment: Deploy the index.html file to a secure web environment capable of providing Firebase configuration and custom authentication tokens (__app_id, __firebase_config, __initial_auth_token).
Authentication: The application uses Firebase Anonymous Sign-In, falling back to custom token authentication if provided, ensuring every session is uniquely tracked and data is securely saved under the corresponding userId.
🎨 Game Configuration
The following constants can be easily adjusted within the <script type="module"> block in index.html:
Constant
Description
Default Value
COLORS
Array of all available colors. Currently 8 colors are used to increase cognitive load.
{ Red, Blue, Green, Yellow, Orange, Cyan, Pink, Brown }
SHAPES
Array of shapes used in the game.
['Circle', 'Square', 'Triangle', 'Star']
MIN_SHAPE_COUNT
Easiest difficulty (fewest distractors).
5
MAX_SHAPE_COUNT
Hardest difficulty (most distractors).
10
ACCURACY_THRESHOLD_UP
Minimum accuracy (over the last 5 rounds) to increase difficulty.
0.85 (85%)
RT_THRESHOLD_DOWN
Maximum Reaction Time (over the last 5 rounds) to decrease difficulty.
3500ms


