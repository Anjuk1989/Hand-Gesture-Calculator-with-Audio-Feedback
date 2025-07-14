# 🤖 Gesture-Controlled Voice Calculator

**Tech That Talks, Learns, and Grows with You!**

A touchless, voice-assisted calculator built using Python, OpenCV, and MediaPipe. Control it using just your hand gestures — no keyboard, no buttons. Ideal for accessibility, contactless environments, and exploring human-computer interaction.

---

## 🎥 Demo

https://www.youtube.com/watch?v=fMxcOvfYBkE&t=2s
> Recognizes hand gestures to input digits (0–9), operators (+, –, ×, ÷), equals (=), undo (U), and speaks the result aloud.

---

## 📌 Features

- 👋 Real-time gesture recognition using **MediaPipe**
- 🧠 Stable gesture detection using **buffering and cooldown logic**
- 🔢 Supports digits, arithmetic operations, undo & evaluation
- 🗣️ Speaks input and result using **pyttsx3**
- 🖥️ Displays input expression and result on screen using OpenCV

---

## 🛠️ Tech Stack

- Python 3.x  
- OpenCV  
- MediaPipe  
- pyttsx3 (offline Text-to-Speech)  
- NumPy, deque (for buffering gestures)

---

## 🧠 Working Steps

1. **Start Webcam**:  
   The application uses OpenCV to access the webcam and capture real-time video frames.

2. **Hand Detection**:  
   MediaPipe detects hands and landmarks for each finger using the captured frames.

3. **Finger Counting**:  
   A function analyzes which fingers are raised based on hand orientation (left/right) to count fingers and identify gestures.

4. **Gesture Mapping**:  
   - Right hand: Used for digits 0–9  
   - Left hand: Used for operators and special controls  
     - 1 finger → '+'  
     - 2 fingers → '-'  
     - 3 fingers → '*'  
     - 4 fingers → '/'  
     - 5 fingers → '='  
     - 0 fingers → Undo

5. **Gesture Stability Check**:  
   Gestures are buffered using a `deque`, and only registered when the same gesture is detected in consecutive frames (for stability).

6. **Cooldown Mechanism**:  
   Each gesture has a cooldown period to avoid repeated inputs when the hand remains in the same position.

7. **Expression Building**:  
   Detected digits and operators are appended to a string expression.

8. **Voice Feedback**:  
   The input (digit or operator) and the final result are spoken using `pyttsx3`.

9. **Expression Evaluation**:  
   When '=' is detected, the expression is evaluated using Python’s `eval()` function, and the result is displayed and read aloud.

10. **Undo Functionality**:  
    When gesture 'U' is shown (0 fingers on the left hand), the last character is removed from the expression.
