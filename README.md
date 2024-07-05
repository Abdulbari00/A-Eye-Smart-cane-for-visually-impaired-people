# A-Eye-Smart-cane-for-visually-impaired-people
This projet is developed For Graduation Project

By: Abdulbari Khabuli, Youcef Bouken
Under-graduated students, Mechatronics Bachelors

Under the supervision of:  Assist. Prof. Dr. Sina Alp, Istanbul Okan University Turkey


Description :

Visual impairment is affecting around 40 million people worldwide, Governments in 
developed countries have implemented many solutions to make everyday life for visually impaired 
people easier such as spreading the use of Braille code in public areas and building tactile paving 
in most areas just to name a few, Unfortunately this does not apply in 3rd world countries which 
have the majority of visually impaired people in numbers and percentage. This project is aiming 
to give both real-time auditory and haptic feedback for the visually impaired combining both 
computer vision and sensors, implementing the state of the art “YOLOv” algorithm and OpenCV 
library for fast and accurate object detection and providing audio feedback of the distance and the 
class of the object , combined with a haptic vibration alert to ensure timely collision avoidance 
from a vibration motor based on the measurement of an ultrasonic sensor. We believe that this 
design if adapted widely it should grant visually impaired people more confidence and self-reliance 
to their day-to-day life.


Objective:
The primary objective of this project is to design, develop, and evaluate a prototype that 
significantly enhances the mobility and safety of visually impaired individuals. By leveraging 
YOLOv and other technologies, our smart cane aims to provide a comprehensive and intuitive 
solution for obstacle detection and navigation



YOLOv
In the field of computer vision, the You Only Look Once (YOLO) algorithm has 
revolutionized the landscape. It offers real-time object detection with exceptional accuracy, 
rendering it a formidable tool for various applications including surveillance, autonomous 
vehicles, as well as image and video analysis. Many version of YOLOv were released through 
out the years in this project we are using YOLOv3 from Ultralytics, this model is in the goldilock 
zone between speed and accuracy while having fair requirements for computing power. 
The Ultralytics YOLOv3 model represents the forefront of object detection technology, 
building upon the achievements of earlier YOLO versions while introducing new features and 
enhancements to enhance performance and versatility. YOLOv3 prioritizes speed, accuracy, and 
user-friendliness, making it an ideal solution for various tasks including object detection, 
instance segmentation, and image classification.
![map50blue](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/f308bb8c-91ca-4f83-86e9-96f1b1064377)














AI Model YOLOv Algorithm:
The YOLO (You Only Look Once) algorithm, initially implemented using the Darknet 
framework, employs a Convolutional Neural Network (CNN) to predict bounding boxes and 
class probabilities of objects within input images. YOLO operates by partitioning the input 
image into a grid of cells, wherein each cell is tasked with predicting the presence of objects, 
their bounding box coordinates, and respective class labels. Unlike two-stage object detection 
methods like R-CNN, YOLO processes the entire image in a single pass, leading to superior 
efficiency and speed. The algorithm has evolved through multiple iterations, including YOLOv1, 
YOLOv2, YOLOv3, YOLOv4, YOLOv5, YOLOv6, and YOLOv7, each introducing refinements 
aimed at enhancing accuracy, processing speed, and the ability to detect smaller objects.
Convolutional Neural Networks (CNN):
Convolutional Neural Networks (CNNs) are a type of deep neural network primarily 
used for analyzing visual data. Unlike traditional neural networks, CNNs employ 
convolution, a mathematical operation that modifies one function based on another. 
However, understanding the mathematics behind CNNs is not necessary to grasp their 
functionality. Essentially, CNNs reduce images into a more manageable format while 
retaining important features for accurate predictions.
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/cbd8fc04-9924-40f5-a4cc-2140250296eb)
YOLOv3, introduced in 2020, integrates the EfficientDet architecture for enhanced 
efficiency and accuracy. Unlike prior versions, it adopts anchor-free detection, replacing 
anchor boxes with a single convolutional layer for bounding box prediction, ensuring 
adaptability to diverse object shapes and sizes. Additionally, it incorporates Cross minibatch normalization (CmBN), a variant of batch normalization, to refine model accuracy. 
YOLOv3 leverages transfer learning, initially training on a large dataset and fine-tuning on a 
smaller one, facilitating improved generalization to new data.

















COCO Dataset:
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-
people/assets/103534402/7749eb36-2f3a-4f6d-9530-d8329369a2b0)
The COCO (Common Objects in Context) dataset serves as a cornerstone in computer 
vision research, specifically tailored for object detection, segmentation, and captioning 
tasks. It stands as a pivotal benchmarking resource, facilitating exploration into diverse 
object categories.
Key Features:
Boasting a vast repository of over 330K images, COCO includes annotations for 200K 
images, spanning object detection, segmentation, and captioning. Encompassing 80 
object categories, ranging from commonplace entities like automobiles and fauna to 
specialized items such as parasols and athletic gear, it provides annotations inclusive of 
object bounding boxes, segmentation masks, and textual descriptors. Standardized 
evaluation metrics such as mean Average Precision (mAP) and mean Average Recall (mAR) 
ensure consistent model assessment across tasks.
Dataset Structure:
COCO's architecture is stratified into three distinct subsets:
- Train2017: Constituting 118K images, this segment serves as the training corpus for 
model development.
- Val2017: With a contingent of 5K images, this subset operates as the validation set during 
model training.
- Test2017: Comprising 20K images, this division is designated for model benchmarking. 
Devoid of publicly accessible ground truth annotations, model performance is assessed 
through submissions to the COCO evaluation server.
Applications:
The COCO dataset finds extensive utility in training and evaluating a spectrum of deep 
learning models across manifold applications, including object detection (e.g., YOLO, 
Faster R-CNN, SSD), instance segmentation (e.g., Mask R-CNN), and key point detection 
(e.g., OpenPose). Its comprehensive repertoire of object categories, exhaustive 
annotations, and standardized evaluation metrics solidify its status as an indispensable 
asset within the domain of computer vision research and application.



















Hardware & Software
RASPBERRY PI
The **Raspberry Pi** is a series of small 
single-board computers developed in the United 
Kingdom by the Raspberry Pi Foundation to 
promote the teaching of basic computer science in 
schools and in developing countries. The original 
model became far more popular than anticipated, 
selling outside its target market for uses such as 
robotics. It does not include peripherals (such as 
keyboards and mice) or cases.
However, some accessories have been included in several official and unofficial bundles.
The Raspberry Pi is a credit-card-sized computer that plugs into your TV and a keyboard. It is a 
capable little device that enables people of all ages to explore computing and to learn how to 
program in languages like Scratch and Python. It’s capable of doing everything you’d expect a 
desktop computer to do, from browsing the internet and playing high-definition video, to making 
spreadsheets, word-processing, and playing games.
Furthermore, In the prototype of this project a Raspberry pi 4 model B 4GB ram is being utilized 
with a cooling case and a camera module and a 16 GB memory card for storage alongside a 
power source, either two batteries or a power bank.
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/25bdb8bd-a421-4112-8953-d974308bfba5)
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/d3bfc1c4-adda-4381-a337-df6244005d55)
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/88cd4d94-0886-4bb4-91ca-4b59ac1a2078)





















Ultrasonic sensor
The Ultrasonic Sensor is a cost-effective proximity and distance sensor widely employed 
for object avoidance in robotics projects. Its versatility extends to applications such as turret 
control, water level sensing, and even parking assistance. Power source 
It operates by emitting sound waves at a frequency beyond human hearing. The sensor's 
transducer serves as both a transmitter and receiver of these ultrasonic signals. Like other 
ultrasonic sensors, ours utilizes a single transducer to emit a pulse and detect the echo. By 
measuring the time interval between transmission and reception, the sensor calculates the 
distance to the target.
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/8a80d4fd-ee6f-47d7-aae8-5b80521156ea)
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/46910730-c0f0-4d69-b356-758db16ee979)
















Mini vibrating motor
That's your little buzzing motor, and for any haptic feedback project you'll want to pick up a few 
of them. These vibe motors are tiny discs, completely sealed up so they're easy to use and embed.
Two wires are used to control/power the vibe. Simply provide power from a battery or 
microcontroller pin (red is positive, blue is negative) and it will buzz away. The rated voltage is 
2.5 to 3.8V and for many projects, we found it vibrates from 2V up to 5V, higher voltages result 
in more current draw but also a stronger vibration.
Technical Details
Dimension: 10mm diameter, 2.7mm thick
Voltage: 2V - 5V/5V current draw: 100mA, 4V current draw: 80mA, 3V current draw: 60mA, 2V 
current draw: 40mA/11000 RPM at 5V/Weight: 0.9 gram
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/a61753e7-4392-4a4a-b78e-6a0ad0b0c72d)























3D Design
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/0386a339-8dce-4982-a009-ea8e4da878d4)
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/647e9654-984e-4c23-acc6-09bea508f930)
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/2d066221-6bb8-4b3d-ad86-7c6f698bcb34)
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/a3ef9351-6430-4aca-9e4d-2800919d4e6a)
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/05d77604-5a0a-42e5-956e-b91b207e5ea4)























3D-printing the casing
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/054980b3-f0bf-4541-be8a-99c7247d86e8)
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/00df3e63-26e5-46d1-8c42-211157503834)
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/f8cd371f-e084-49da-83c7-78a209993d93)






















Finale assembly
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/1bbd6433-dcca-49c5-8b51-f90ab94c9cfa)
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/5dc84442-8f81-4b04-b9d0-86f039432f45)
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/884c6214-5e4b-4929-9934-a20ef9865a30)
![image](https://github.com/Abdulbari00/A-Eye-Smart-cane-for-visually-impaired-people/assets/103534402/4d9bdfb8-b26b-4618-9505-78fdcb4600c9)















Future Scope
In future implementations, we hope to add many features we see very effective in achieving the
essential purpose of this project and improve life quality alongside it:
-panic button pressing which will notify the relatives of the person about the GPS co-ordinates 
via SMS message
-train the object detection algorithm to detect other objects that are not present on the COCO 
dataset the current model is trained on, objects that will improve the quality of life of the user 
such as, Food recognition, currency identification, face recognition, color identifier and OCR 
(text recognition). 
- make a smaller version for kids and have a live video feed transmission for parents.
- make the design more compact and shrink it enough to fit in a glasses format to be used indoor,
glasses format will give the camera more stability and enabling the user to benefit from the same 
features without having to hold a cane on one hand so the user will have both his hands for other 
tasks. 
- add an AI voice recognition assistant such as SIRI or ALEXA to enable the user to ask about 
directions, weather situation, time, make phone calls, get info about transportation and the 
battery life left in the cane.
- train the model on night vision footage so the cane could be used at low light situations as well. 
-add a LIDAR instead of the ultrasonic sensor for more accurate distance sensing.
-add a camera with wide angle so it detects the environment on a wider scale.
-train the model to understand and turn sign language into voice output so the visually impaired 
person could communicate with a deaf person if needed. 
- add multiple languages to the voice output so that non-English speakers could use it.
- Ensuring user privacy and compliance with data protection regulations.
-make it detect when an accident happens, it should notify relatives through SMS or voice 
message and include medical ID and make the cane say it to the specialized authorities.
- pair it with a phone app that stores stats and improve overall experience.
