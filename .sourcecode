import RPi.GPIO as GPIO
import time
import cv2
import numpy as np
import pyttsx3
from imutils.video import VideoStream
import threading
import speech_recognition as sr
# GPIO Mode (BOARD / BCM)
GPIO.setmode(GPIO.BCM)
# Set GPIO Pins
GPIO_TRIGGER = 18
GPIO_ECHO = 24
BUZZER_PIN = 20
# Set GPIO direction (IN / OUT)
GPIO.setup(GPIO_TRIGGER, GPIO.OUT)
GPIO.setup(GPIO_ECHO, GPIO.IN)
GPIO.setup(BUZZER_PIN, GPIO.OUT)
# Initialize PWM
buzzer_pwm = GPIO.PWM(BUZZER_PIN, 100) 
# Initialize the video stream
frameSize = (320, 240)
vs = VideoStream(src=0, resolution=frameSize, framerate=32).start()
time.sleep(2.0)
# Load the COCO class labels our YOLO model was trained on
LABELS = open("/home/grad_project/Desktop/GitHub/Realtime-ObjectDetection-Direction-forBlind-Raspberry-Pi/model2-files/coco.names").read().strip().split("\n")
# Load YOLOv5 model
print("[INFO] loading YOLOv5 from disk...")
net = cv2.dnn.readNet(r"/home/grad_project/Desktop/GitHub/Realtime-ObjectDetectionDirection-for-Blind-Raspberry-Pi/model2-files/yolov5s.torchscript.pt")
# Initialize text-to-speech engine
engine = pyttsx3.init()
# Function to speak text
def speak(voice_prompt):
 if not engine._inLoop:
 engine.say(voice_prompt)
 engine.runAndWait()
# Function to calculate distance
def calculate_distance(known_width, focal_length, pixel_width):
 return (known_width * focal_length) / pixel_width
# Function to measure distance with ultrasonic sensor
def distance():
 # Measurement logic
 GPIO.output(GPIO_TRIGGER, True)
 time.sleep(0.00001)
 GPIO.output(GPIO_TRIGGER, False)
 StartTime = time.time()
StopTime = time.time()
 while GPIO.input(GPIO_ECHO) == 0:
 StartTime = time.time()
 while GPIO.input(GPIO_ECHO) == 1:
 StopTime = time.time()
 TimeElapsed = StopTime - StartTime
 distance = (TimeElapsed * 34300) / 2
 return distance
# Function to control buzzer
def control_buzzer():
 try:
 while True:
 distance_val = distance()
 distance_val = min(200, distance_val) # Limit distance to 200 cm
 distance_val = max(2, distance_val) # Limit distance to 2 cm
 if distance_val < 50:
 duty_cycle = int((50 - distance_val) / 50 * 100)
 buzzer_pwm.start(duty_cycle)
 else:
 buzzer_pwm.stop()
 time.sleep(0.5)
 except KeyboardInterrupt:
 print("Buzzer control stopped by User")
# Function to recognize speech
def recognize_speech():
 recognizer = sr.Recognizer()
with sr.Microphone() as source:
 print("Listening...")
 recognizer.adjust_for_ambient_noise(source)
 audio = recognizer.listen(source)
 try:
 print("Recognizing...")
 command = recognizer.recognize_google(audio)
 print("You said:", command)
 return command.lower()
 except sr.UnknownValueError:
 print("Could not understand audio")
 return None
 except sr.RequestError as e:
 print("Could not request results; {0}".format(e))
 return None
# Function to check if object is detected
def check_object(object_name, boxes, classIDs):
 for i in range(len(boxes)):
 if LABELS[classIDs[i]] == object_name:
 return True
 return False
# Function to detect object
def detect_object(object_name, boxes, classIDs):
 if check_object(object_name, boxes, classIDs):
 speak(f"Yes, there is a {object_name} in front of you.")
 else:
speak(f"No, there is no {object_name} in front of you.")
# Main function
def main():
 threading.Thread(target=control_buzzer).start()
 detect_flag = False
 try:
 while True:
 if not detect_flag:
 command = recognize_speech()
 if command and "detect" in command:
 detect_flag = True
 else:
 frame = vs.read()
 (H, W) = frame.shape[:2]
 blob = cv2.dnn.blobFromImage(frame, 1 / 255.0, (416, 416), swapRB=True, 
crop=False)
 net.setInput(blob)
 outputs = net.forward()
 boxes = []
 confidences = []
 classIDs = []
 for output in outputs:
 for detection in output:
 scores = detection[5:]
 classID = np.argmax(scores)
 confidence = scores[classID]
 if confidence > 0.3:
box = detection[0:4] * np.array([W, H, W, H])
 (centerX, centerY, width, height) = box.astype("int")
 x = int(centerX - (width / 2))
 y = int(centerY - (height / 2))
 boxes.append([x, y, int(width), int(height)])
 confidences.append(float(confidence))
 classIDs.append(classID)
 idxs = cv2.dnn.NMSBoxes(boxes, confidences, 0.5, 0.3)
 voice_prompt = ""
 if len(idxs) > 0:
 for i in idxs.flatten():
 centerX = boxes[i][0] + boxes[i][2] / 2
 object_name = LABELS[classIDs[i]]
 pixel_width = boxes[i][2]
 distance_val = distance()
 distance_val = min(200, distance_val) # Limit distance to 200 cm
 distance_val = max(2, distance_val) # Limit distance to 2 cm
 distance_val = round(distance_val, 2)
 if centerX <= W / 3:
 voice_prompt = f"{object_name} to your left. {distance_val} centimeters away 
. "
 elif centerX <= (W / 3 * 2):
 voice_prompt = f"{object_name} in front of you . {distance_val} centimeters 
away . "
 else:
 voice_prompt = f"{object_name} to your right. {distance_val} centimeters 
away . "
 if object_name in ["cup", "fork", "umbrella"]:
voice_prompt += f"Don't worry about it."
 (x, y, w, h) = boxes[i]
 color = (0, 255, 0)
 cv2.rectangle(frame, (x, y), (x + w, y + h), color, 2)
 text = f"{object_name}: {confidences[i]:.2f}"
 cv2.putText(frame, text, (x, y - 5), cv2.FONT_HERSHEY_SIMPLEX, 0.5, color, 
 cv2.putText(frame, f"Distance: {distance_val} cm", (x, y - 20), cv2.FONT_HERSHEY_SIMPLEX, 0.5, color, 2)
 cv2.imshow("video", frame)
 if voice_prompt:
 threading.Thread(target=speak, args=(voice_prompt,)).start()
 key = cv2.waitKey(1) & 0xFF
 if key == ord("q"):
 break
 command = recognize_speech()
 if command:
 if "how are you" in command:
 speak("I'm fine, thank you. And you?")
 response = recognize_speech()
 if response:
 if "fine" in response or "good" in response:
 speak("That's great!")
 else:
 speak("I hope you feel better soon.")
 elif any(obj in command for obj in LABELS):
 object_name = next((obj for obj in LABELS if obj in command), None)
 detect_object(object_name, boxes, classIDs)
except KeyboardInterrupt:
 print("Measurement stopped by User")
 finally:
 GPIO.cleanup()
 cv2.destroyAllWindows()
if __name__ == "__main__":
 main()
