robotic-car
===========

1 Introduction 1
1.1 Objective . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1
1.2 Problem statement . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1
1.3 Literature review . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2
1.4 Specications . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2
1.4.1 Car Control . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2
1.5 Sub-projects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 3
2 Template Matching 5
2.1 Template-based matching and convolution . . . . . . . . . . . . . . . . . . 6
2.2 Edge based template model . . . . . . . . . . . . . . . . . . . . . . . . . . 9
2.3 Detection and Estimation . . . . . . . . . . . . . . . . . . . . . . . . . . . 10
3 Edge Detection 12
3.1 Canny Edge Detection . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 12
3.1.1 Test Image . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 13
3.1.2 The Canny Edge Detection Algorithm . . . . . . . . . . . . . . . . 13
3.1.2.1 Smoothing . . . . . . . . . . . . . . . . . . . . . . . . . . 14
3.1.2.2 Finding gradients . . . . . . . . . . . . . . . . . . . . . . 15
3.1.2.3 Non-maximum suppression . . . . . . . . . . . . . . . . . 15
3.1.2.4 Double threshold . . . . . . . . . . . . . . . . . . . . . . . 17
3.1.2.5 Edge tracking by hysteresis . . . . . . . . . . . . . . . . . 17
3.1.3 Implementation of Canny Edge Detection . . . . . . . . . . . . . . 18
4 Hough Transforms 20
4.1 Hough Line Transforms . . . . . . . . . . . . . . . . . . . . . . . . . . . . 20
v
Contents vi
4.2 Hough Circle Transforms . . . . . . . . . . . . . . . . . . . . . . . . . . . 24
5 Human Detection 28
5.1 The Viola Jones Algorithm . . . . . . . . . . . . . . . . . . . . . . . . . . 29
5.1.1 Integral Images . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 29
5.1.2 Adaboost . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 29
5.1.3 Cascade Training . . . . . . . . . . . . . . . . . . . . . . . . . . . . 31
6 Hue-Saturation-Value (HSV) 33
6.1 HSV for trac light detection . . . . . . . . . . . . . . . . . . . . . . . . . 34
7 Arduino Programing and Serial Comunication 36
7.1 Arduino Programing . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 36
7.1.1 Power . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 37
7.1.2 Memory . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 38
7.1.3 Input and Output . . . . . . . . . . . . . . . . . . . . . . . . . . . 38
7.1.4 Communication . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 39
7.1.5 Programming . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 39
7.1.6 Servo control in arduino . . . . . . . . . . . . . . . . . . . . . . . . 40
7.1.7 Arduino Serial Communication . . . . . . . . . . . . . . . . . . . . 40
7.1.8 Automatic Software Reset . . . . . . . . . . . . . . . . . . . . . . . 40
7.1.9 USB Overcurrent Protection . . . . . . . . . . . . . . . . . . . . . 41
7.1.10 Physical Characteristics . . . . . . . . . . . . . . . . . . . . . . . . 41
7.2 Serial Comunication . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 41
7.2.1 CSerial class member functions . . . . . . . . . . . . . . . . . . . . 42
8 Hardware Work 43
8.1 Servo motor(SM-SR303R) . . . . . . . . . . . . . . . . . . . . . . . . . . . 43
8.1.1 Servo working Mechanism . . . . . . . . . . . . . . . . . . . . . . . 43
8.1.2 Features . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 44
8.1.3 Dimensions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 44
8.1.4 Servo programming . . . . . . . . . . . . . . . . . . . . . . . . . . 45
8.2 Computer . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 45
8.2.1 Software Required . . . . . . . . . . . . . . . . . . . . . . . . . . . 45
8.2.2 Installation and Integration . . . . . . . . . . . . . . . . . . . . . . 45
8.2.3 Glass shit and other supporting materials . . . . . . . . . . . . . . 46
9 Result and Conclusion 47
9.1 Result . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 47
9.2 Conclusion . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 48
9.3 Recommendation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 49
A Servo controller program 50
Bibliography 52
List of Figures
1.1 Google car . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2
1.2 Over all block diagram . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4
2.1 Source image and template image . . . . . . . . . . . . . . . . . . . . . . . 7
2.2 Comparison of two images . . . . . . . . . . . . . . . . . . . . . . . . . . . 8
2.3 Region of interest . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 8
3.1 Original image for canny detection . . . . . . . . . . . . . . . . . . . . . . 13
3.2 Smoothing eect . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 14
3.3 Illustration of non-maximum suppression. . . . . . . . . . . . . . . . . . . 16
3.4 (a) Gradient values (b) Edges after non-maximum suppression. . . . . . . 16
3.5 (a) Edges after non-maximum suppression (b) Double thresholding. . . . . 17
3.6 (a) Double thresholding (b) Edge tracking by hysteresis (c) Final output . 18
3.7 All steps of the edge detection. . . . . . . . . . . . . . . . . . . . . . . . . 19
4.1 Results of Canny edge detection . . . . . . . . . . . . . . . . . . . . . . . 20
4.2 The Hough line transform . . . . . . . . . . . . . . . . . . . . . . . . . . . 21
4.3 Hough line transform in the image plane . . . . . . . . . . . . . . . . . . . 22
4.4 The Canny edge detector . . . . . . . . . . . . . . . . . . . . . . . . . . . 23
4.5 The Hough circle transform . . . . . . . . . . . . . . . . . . . . . . . . . . 25
5.1 Edge detection . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 28
5.2 Haar features . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 29
5.3 Integral Image . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 30
5.4 Summation of Integrals . . . . . . . . . . . . . . . . . . . . . . . . . . . . 30
7.1 The Arduino Board . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 37
7.2 Servo control scheme in arduino . . . . . . . . . . . . . . . . . . . . . . . . 40
8.1 The robot car with glass frame . . . . . . . . . . . . . . . . . . . . . . . . 46
vii
List of Tables
7.1 Arduino Specications . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 37
viii
Chapter 1
Introduction
Would you trust your car to drive itself? we are asking the peoples to take that chance.
The robot taxi, common in science ction since the 1950s, is now set to become a reality.
The goal of this project was to build a robotic car with the ability to detect and follow
a lane (lines on the road) using a web-cam. A major diculty in this project was being
able to separate the lane of the road in the video and then directing the car to follow it.
Once tracked, a control scheme allowed the car to keep the lane on the screen and follow
it as it turns either left or right.
1.1 Objective
The purpose of our project is to develop a mobile robot that will track and follow
lane (lines on the road) through the use of a camera mounted on a computer that
processes the image. More specically, the goal of the project entails: lane detection,
full body detection, template matching and HSV (hue saturation value) color model
for trac light detection in real-time manner. Ultimately, the robot should be able to
autonomously detect a lane of road and to follow the detected lane in order to move
with out leaving the road. The project provides benets to visually impaired peoples,
material transportation with out drivers and generally to the automotive industry.
1.2 Problem statement
Most automotive deaths are due to human error, not machine error, we have been
seeing that there is a lot of trac congestion and there is a need of trac police and
1
Chapter 1. Introduction 2
insurance. A driverless or robot car can save lives and minimize trac accidents. The
car uses image processing and machine learning algorithm technology that enables the
car to detect objects nearby and in its path, as well as control its speed, direction, and
destination. Due to an autonomous system's increased reliability and decreased reaction
time compared to human drivers and the Removal of constraints on occupants' in an
autonomous car. It would not matter if the occupants were under age, over age, blind,
distracted, intoxicated, or otherwise impaired. So we motivated by this title to work on
our nal project or thesis in passion.
1.3 Literature review
The Google driverless car is a project by Google that involves developing technology for
robotic cars. The project is currently being led by Google engineer Sebastian Thrun,
director of the Stanford Articial Intelligence Laboratory and co-inventor of Google
Street View.[1] Thrun's team at Stanford created the robotic vehicle Stanley which won
the 2005 DARPA Grand Challenge and its US$2 million prize from the United States
Department of Defense.[2] [3]
Once a secret project, Google's autonomous vehicles are now out in the open, quite
literally, with the company test-driving them on public roads and, on one occasion, even
inviting people to ride inside one of the robot cars as it raced around a closed course.[2]
Figure 1.1: Google car
1.4 Specications
1.4.1 Car Control
To control the movement of our car we need to have full rotation servo motors to be
the wheels of the car. In case of turning our car to the left, the tow left servos of the
car rotates backward while the other two right servos rotating in the forward direction;
Chapter 1. Introduction 3
and turning the car to the right will be vice-verse. The speed of the car is equal to the
speed of the servo which is between (SS = 54rpm) and (SS = 70rpm).
Once the camera has sought out the lane, we would like the car to align itself with the
detected lane and follow it. We would like the car to continue following the lane as it
turns, regardless of any turns the lane might make.
1.5 Sub-projects
As an overview, the entire project consists of 6 modules. A block diagram showing how
all of the modules t together is given in gure 1.
1. Computer
 The main form of control is our personal computer (PC) running Windows.
The computer have USB port for communication with the Arduino micro-
controller for interfacing with the web camera.
 The PC handles functions such as receiving data from the web-cam, pro-
cessing the data, and communicating with the servo motors via the Arduino
microcontroller to produce locomotion and to orient the car. The system is a
closed loop in that the drive electronics indirectly aect the camera's or car's
position.
2. Arduino Microcontroller
 To enable the USB port to control the servo motors, arduino microcontroller
is used.
 The arduino microcontroller acts as an intermediary to translate serial data
into arduino control signals for the servo motor control circuits.
 The arduino also receives signal from the proximity sensor through its ana-
logue input and controls the servo with out the intervention of the PC.
3. Servo Motors
 Movement of the robotic car is accomplished via a four servo motor, controlled
directly by the arduino microcontroller, and thus indirectly by the PC.
 To turn on the turning points the left pair of wheels and the right pair of
wheels rotates in opposite direction according to the direction of turning.
4. Vision System
Chapter 1. Introduction 4
 The vision data is provided through the PCs web camera.
 The camera is be relatively simple, running at 320 x 240 resolution and 30
frames per second.
5. Proximity Sensor
 The proximity sensor is used to detect an immediate intrusion of peoples and
animals to protect them from being killed by the car accident.
 The data from the proximity sensor is directly provided to the arduino mi-
crocontroller to its analogue input.
6. Power Source
 The power source from the PC battery supplies the control electronics as well
as drive electronics through the arduino microcontroller.
 +5V power is generated from the arduino the supply the servo motors.
Figure 1.2: Over all block diagram
Chapter 2
Template Matching
Template matching is a technique for nding areas of an image that match (are similar)
to a template image (patch).
If the template image has strong features, a feature-based approach may be consid-
ered; the approach may prove further useful if the match in the search image might
be transformed in some fashion. Since this approach does not consider the entirety of
the template image, it can be more computationally ecient when working with source
images of larger resolution, as the alternative approach, template-based, may require
searching potentially large amounts of points in order to determine the best matching
location.
For templates without strong features, or for when the bulk of the template image
constitutes the matching image, a template-based approach may be eective. As afore-
mentioned, since template-based template matching may potentially require sampling
of a large number of points, it is possible to reduce the number of sampling points by
reducing the resolution of the search and template images by the same factor and per-
forming the operation on the resultant downsized images (multi resolution, or pyramid,
image processing), providing a search window of data points within the search image so
that the template does not have to search every viable data point, or a combination of
both.
Template matching has been a classical approach to the problems of locating and rec-
ognizing of an object in an image. Template matching technique, especially in two
dimensional cases, has many AR lications in object tracking, image compression, stereo
correspondence, and other computer vision applications -). Even now, it is a funda-
mental technique to solve them. Among several matching methods, Normalized Cross
Correlation (NCC) and square root of Sum of Square Dierences SSD) have been used
5
Chapter 2. Template Matching 6
as the measure for similarity. Moreover, many other template matching techniques1-
3), 5-8 such as Sum of Absolute Dierences (SAD) and Sequential Similarity Detection
Algorithm (SSDA) have been adopted in many applications for pattern recognition,
video compression and so on. In addition, template matching has been widely used in
various applications, for example, extraction of container identity codes9), image seg-
mentationS), and so on. Proposed template matching using partial and whole template
to detect the objects with the two-dimensional standard shape under outdoor environ-
ments. Most existing methods suered from extremely deteriorated images under bad
conditions, for example, illumination changes, specular highlights and occlusions. This
fact is a major motivation to pursue this subject in this paper. To overcome these
diculties, we propose the new framework for the novel template matching with two
kinds of sub-templates. Here, we discuss template matching of normalized images after
segmentation.
2.1 Template-based matching and convolution
A basic method of template matching uses a convolution mask (template), tailored to
a specic feature of the search image, which we want to detect. This technique can be
easily performed on grey images or edge images. The convolution output will be highest
at places where the image structure matches the mask structure, where large image
values get multiplied by large mask values. This method is normally implemented by
rst picking out a part of the search image to use as a template: We will call the search
image S(x; y), where (x; y) represent the coordinates of each pixel in the search image.
We will call the template T(xt; yt), where (xt; yt) represent the coordinates of each pixel
in the template. We then simply move the center (or the origin) of the template T(xt; yt)
over each (x; y) point in the search image and calculate the sum of products between the
coecients in S(x; y) and T(xt; yt) over the whole area spanned by the template. As all
possible positions of the template with respect to the search image are considered, the
position with the highest score is the best position. This method is sometimes referred
to as 'Linear Spatial Filtering' and the template is called a lter mask. For example, one
way to handle translation problems on images, using template matching is to compare
the intensities of the pixels, using the SAD (Sum of absolute dierences) measure. A
pixel in the search image with coordinates (xs; ys) has intensity Is(xs; ys) and a pixel
in the template with coordinates (xt; yt) has intensity It(xt; yt). Thus the absolute
dierence in the pixel intensities is dened as Diff(xs; ys; xt; yt) = jIs(xs; ys)It(xt; yt)j.
SAD(x; y) =
TXrows
i=0
TXcols
j=0
Diff(x + i; y + j; i; j)
Chapter 2. Template Matching 7
The mathematical representation of the idea about looping through the pixels in the
search image as we translate the origin of the template at every pixel and take the SAD
measure is the following:
SXrows
x=0
SXcols
y=0
SAD(x; y)
Srows and Scols denote the rows and the columns of the search image and Trows and Tcols
denote the rows and the columns of the template image, respectively. In this method
the lowest SAD score gives the estimate for the best position of template within the
search image. The method is simple to implement and understand, but it is one of the
slowest methods.
We need two primary components:
1. Source image (I): The image in which we expect to nd a match to the template
image
2. Template image (T): The patch image which will be compared to the template
image our goal is to detect the highest matching area:
Figure 2.1: Source image and template image
To identify the matching area, we have to compare the template image against the source
image by sliding it:
By sliding, we mean moving the patch one pixel at a time (left to right, up to down). At
each location, a metric is calculated so it represents how "good" or "bad" the match at
that location is (or how similar the patch is to that particular area of the source image).
For each location of T over I, you store the metric in the result matrix (R). Each location
in R contains the match metric. The image above is the result R of sliding the patch with
a metric TM CCORR NORMED. The brightest locations indicate the highest matches.
As you can see, the location marked by the red circle is probably the one with the
highest value, so that location (the rectangle formed by that point as a corner and
width and height equal to the patch image) is considered the match. In practice, we use
Chapter 2. Template Matching 8
Figure 2.2: Comparison of two images
Figure 2.3: Region of interest
the function minMaxLoc to locate the highest value (or lower, depending of the type of
matching method) in the R matrix.
OpenCV implements Template matching in the function match Template.[4] The avail-
able methods are 6:
A. method=CV TM SQDIFF
R(x; y) =
X
x0;y0
(T(x0; y0) 􀀀 I(x + x0; y + y0))2
B. method=CV TM SQDIFF NORMED
R(x; y) =
P
x0;y0(T(x0; y0) 􀀀 I(x + x0; y + y0))2
qP
x0;y0 T(x0; y0)2 
P
x0;y0 I(x + x0; y + y0)2
Chapter 2. Template Matching 9
C. method=CV TM CCORR
R(x; y) =
X
x0;y0
(T(x0; y0)  I(x + x0; y + y0))
D. method=CV TM CCORR NORMED
R(x; y) =
P
x0;y0(T(x0; y0)  I(x + x0; y + y0))
qP
x0;y0 T(x0; y0)2 
P
x0;y0 I(x + x0; y + y0)2
E. method=CV TM CCOEFF
R(x; y) =
X
x0;y0
(T0(x0; y0)  I(x + x0; y + y0))
where
T0(x0; y0) = T(x0; y0) 􀀀 1=(w  h) 
X
x00;y00
T(x00; y00)
and,
I0(x + x0; y + y0) = I(x + x0; y + y0) 􀀀 i=(w  h) 
X
x00;y00
I(x + x00; y + y00)
F. method=CV TM CCOEFF NORMED
R(x; y) =
P
x0;y0(T0(x0; y0)  I(x + x0; y + y0))
qP
x0;y0 T0(x0; y0)2 
P
x0;y0 I0(x + x0; y + y0)2
2.2 Edge based template model
The next task in the algorithm is to nd the object in the search image using the template
model. We can see the model we created from the template image which contains a set
of points: PT
i = (XT
i ; Y T
i ), and its gradients in X and Y direction GT
i = (GxT
i ; GyT
i ),
where i = 1n, n is the number of elements in the Template (T) data set.
We can also nd the gradients in the search image (S) GS
u;v = (GxS
u;v; GyS
u;v), where
u = 1::: number of rows in the search image, v = 1 number of columns in the search
image. In the matching process, the template model should be compared to the search
image at all locations using a similarity measure.[4] The idea behind similarity measure
is to take the sum of all normalized dot products of gradient vectors of the template
image and search the image over all points in the model data set. This results in a score
Chapter 2. Template Matching 10
at each point in the search image. This can be formulated as follows:
Su;v =
1
n
Xn
i=1
(GxT
i  GxS
(u+Xi;v+Y i)) + (GyT
i  GyS
(u+Xi;v+Y i))
q
GxT2
i + GyT2
i 
q
(GxT
(u+Xi;v+Y i))2 + (GyT
(u+Xi;v+Y i))2
In case there is a perfect match between the template model and the search image, this
function will return a score 1. The score corresponds to the portion of the object visible
in the search image. In case the object is not present in the search image, the score will
be 0. In practical situations, we need to speed up the searching procedure. This can be
achieved using various methods. The rst method is using the property of averaging.
When nding the similarity measure, we need not evaluate for all points in the template
model if we can set a minimum score (Smin) for the similarity measure. For checking
the partial score Su;v at a particular point J, we have to nd the partial sum Sm. Sm
at point m can be denes as follows:
Smu;v =
1
m
Xm
i=1
(GxT
i  GxS
(u+Xi;v+Y i)) + (GyT
i  GyS
(u+Xi;v+Y i))
q
GxT2
i + GyT2
i 
q
(GxT
(u+Xi;v+Y i))2 + (GyT
(u+Xi;v+Y i))2
It is evident that the remaining terms of the sum are smaller or equal to 1. So we can
stop the evaluation if Sm  Smin 􀀀 1 + m=n.
Another criterion can be that the partial score at any point should be greater than the
minimum score. i.e. Sm  Sminm=n. When this condition is used, matching will be
extremely fast. But the problem is, if the missing part of the object is checked rst, the
partial sum will be low. In that case, that instance of the object will not be considered
as a match. We can modify this with another criterion where we check the rst part of
the template model with a safe stopping criteria and the remaining with a hard criteria,
Sminm=n. The user can specify a greediness parameter (g) where the fraction of the
template model is examined with a hard criteria. So that if g = 1, all points in the
template model are checked with the hard criteria, and if g = 0, all the points will be
checked with a safe criteria only. We can formulate this procedure as follows.
The evaluation of the partial score can be stopped at:
Sm < MIN

(Smin 􀀀 1 +
1 􀀀 g  Smin
1 􀀀 g

m
n
); (Smin 
m
n
)

2.3 Detection and Estimation
While a single template can be approximately represented by means of a single image,
a fruitful way to represent the variability of templates belonging to a given class is by
Chapter 2. Template Matching 11
means of a probability distribution. Let us assume that all templates can be represented
by a set of nd pixels at a given position, not necessarily arranged in a rectangular region,
within a monochrome image. We consider each of them as an nd-dimensional random
vector: each pixel represents a random variable whose value corresponds to the image
intensity level. Each template class is then represented by a probability density:
PT (Ii1 ; :::; Iind
)
where ij represents a pixel in the image plane, Iij ) the corresponding random variable,
and I(ij) a specic value of the random variable.
the problem of template detection ts within the statistical elds of detection and es-
timation theory which in turn may be considered as particular cases of game theory.
Broadly speaking, decision and estimation theory can be considered as a two-person
statistical game.
The probability of selecting each possible action based on the observable x. If the mask
probability distribution is concentrated on a single element of 4 the rule is said to be
non-randomized. The game proceeds along the following steps:
1. Nature chooses a state  2 
2. A hint x is generated according to the conditional distribution Px(xj)
3. The computational agent makes its guess (x) = 
4. The agent experiences a loss C(; ).
Two important issues are the choice of the decision function (x) and the assessment
of its quality. Two cases of the above general games are relevant to the problem of
template matching:
1. 4 = f0; 1; :::; k􀀀1g, which corresponds to hypothesis testing, and in particular
the case K=2, corresponding to binary hypothesis testing. Many problems of
pattern recognition fall within this category.
2. 4 = Rn, corresponding to the problem of point estimation of a real parameter
vector, a typical problem being that of model parameter estimation.
The reason why both categories are required for template matching is that the decision
function in the game against nature is usually of a parametric kind, and, in order to be
practical use, it requires the estimation of appropriate values for all the parameters in
its denition.
Chapter 3
Edge Detection
Edges are boundaries between dierent textures. Edge also can be dened as disconti-
nuities in image intensity from one pixel to another. The edges for an image are always
the important characteristics that oer an indication for a higher frequency. Detection
of edges for an image may help for image segmentation ,data compression, and also help
for well matching, such as image reconstruction and so on.
There are many methods to make edge detection. The most common method for edge
detection is to calculate the dierentiation of an image. The rst-order derivatives in an
image are computed using the gradient, and the second-order derivatives are obtained
using the Laplacian. Another method for edge detection uses Hilbert Transform cany
detection.
3.1 Canny Edge Detection
The purpose of edge detection in general is to signicantly reduce the amount of data
in an image, while preserving the structural properties to be used for further image pro-
cessing. Several algorithms exists, and this project focuses on a particular one developed
by John F. Canny (JFC) in 1986. Even though it is quite old, it has become one of the
standard edge detection methods and it is still used in research.[5]
The aim of JFC was to develop an algorithm that is optimal with regards to the following
Criteria:
1. Detection: The probability of detecting real edge points should be maximized
while the probability of falsely detecting non-edge points should be minimized.
This corresponds to maximizing the signal-to-noise ratio.
12
Chapter 3. Edge Detection 13
2. Localization: The detected edges should be as close as possible to the real edges.
3. Number of responses: One real edge should not result in more than one detected
edge.
(One can argue that this is implicitly included in the rst requirement).
With JFCs mathematical formulation of these criteria, Cannys Edge Detector is optimal
for a certain class of edges (known as step edges). A C++ implementation of the algo-
rithm has been written, and this will be further described. The images used throughout
this worksheet are generated using this implementation.
3.1.1 Test Image
The images bellow are used throughout this worksheet to demonstrate how Canny edge
detection works. It depicts a partially assembled pump from Grundfos, and the edge
detection is a step in the process of estimating the pose (position and orientation) of
the pump. The image has been pre-processed as described in the worksheet "Ideas for
Solution to the Pose Estimation Problem". The pre-processing includes:
 Determining ROI (Region of Interest) that includes only white background besides
the pump, and cropping the image to this region.
 Conversion to gray-scale to limit the computational requirements.
Figure 3.1: Original image for canny detection
 Histogram-stretching, so that the image uses the entire gray-scale. This step may
not be necessary, but it is included to counter-compensate for automatic light
adjustment in the used web camera.
3.1.2 The Canny Edge Detection Algorithm
The algorithm runs in 5 separate steps:
Chapter 3. Edge Detection 14
1. Smoothing: Blurring of the image to remove noise.
2. Finding gradients: The edges should be marked where the gradients of the
image has large magnitudes.
3. Non-maximum suppression: Only local maxima should be marked as edges.
4. Double thresholding: Potential edges are determined by thresholding.
5. Edge tracking by hysteresis: Final edges are determined by suppressing all
edges that are not connected to a very certain (strong) edge. Each step is described
in the following subsections.
3.1.2.1 Smoothing
It is inevitable that all images taken from a camera will contain some amount of noise.
To prevent that noise is mistaken for edges, noise must be reduced. Therefore the image
is rst smoothed by applying a Gaussian lter. The kernel of a Gaussian lter with a
standard deviation of  = 1:4 is shown in Equation below. The eect of smoothing on
the test image with this lter is shown in Figure below.
B =
1
159

2
6666666664
2 4 5 4 2
4 9 12 9 4
5 12 15 12 5
4 9 12 9 4
2 4 5 4 2
3
7777777775
Figure 3.2: Smoothing eect
Chapter 3. Edge Detection 15
3.1.2.2 Finding gradients
The Canny algorithm basically nds edges where the gray-scale intensity of the image
changes the most. These areas are found by determining gradients of the image. Gradi-
ents at each pixel in the smoothed image are determined by applying what is known as
the Sobel-operator. First step is to approximate the gradient in the x- and y-direction
respectively by applying the kernels shown in Equation below.
KGX =
2
6664
􀀀1 0 1
􀀀2 0 2
􀀀1 0 1
3
7775
KGY =
2
6664
1 2 1
0 0 0
􀀀1 􀀀2 􀀀1
3
7775
The gradient magnitudes (also known as the edge strengths) can then be determined
as an Euclidean distance measure by applying the law of Pythagoras as shown in the
above equation. It is sometimes simplied by applying Manhattan distance measure as
shown in the equation below to reduce the computational complexity. The Euclidean
distance measure has been applied to the test image. The computed edge strengths are
compared to the smoothed image in the above gure.
jGj =
q
G2
x + G2
y
jGj = jG2
xj + jG2
y j
where: Gx and Gy are the gradients in the x- and y-directions respectively. It is obvious
that an image of the gradient magnitudes often indicate the edges quite clearly. However,
the edges are typically broad and thus do not indicate exactly where the edges are. To
make it possible to determine this the direction of the edges must be determined and
stored as shown in Equation below:
 = arctan

jGyj
jGxj

3.1.2.3 Non-maximum suppression
The purpose of this step is to convert the "blurred" edges in the image of the gradient
magnitudes to "sharp" edges. Basically this is done by preserving all local maxima in
Chapter 3. Edge Detection 16
the gradient image, and deleting everything else. The algorithm is for each pixel in the
gradient image:
1. Round the gradient direction to nearest 45o, corresponding to the use of an 8-
connected neighborhood.
2. Compare the edge strength of the current pixel with the edge strength of the pixel
in the positive and negative gradient direction. I.e. if the gradient direction is
north ( = 90o), compare with the pixels to the north and south.
3. If the edge strength of the current pixel is largest; preserve the value of the edge
strength. If not, suppress (i.e. remove) the value. A simple example of non-
maximum suppression is shown in the gure below. Almost all pixels have gradient
directions pointing north. They are therefore compared with the pixels above and
below. The pixels that turn out to be maximal in this comparison are marked
with white borders. All other pixels will be suppressed.
Figure 3.3: Illustration of non-maximum suppression.
The edge strengths are indicated both as colors and numbers, while the gradient direc-
tions are shown as arrows. The resulting edge pixels are marked with white borders.
Figure 3.4: (a) Gradient values (b) Edges after non-maximum suppression.
Edge-pixels are only preserved where the gradient has local maxima.
Chapter 3. Edge Detection 17
3.1.2.4 Double threshold
The edge-pixels remaining after the non-maximum suppression step are (still) marked
with their strength pixel-by-pixel. Many of these will probably be true edges in the
image, but some may be caused by noise or color variations for instance due to rough
surfaces. The simplest way to discern between these would be to use a threshold, so that
only edges stronger that a certain value would be preserved. The Canny edge detection
algorithm uses double thresholding. Edge pixels stronger than the high threshold are
marked as strong; edge pixels weaker than the low threshold are suppressed and edge
pixels between the two thresholds are marked as weak.
Figure 3.5: (a) Edges after non-maximum suppression (b) Double thresholding.
In the second image strong edges are white, while weak edges are grey. Edges with a
strength below both thresholds are suppressed.
3.1.2.5 Edge tracking by hysteresis
Strong edges are interpreted as "certain edges", and can immediately be included in
the nal edge image. Weak edges are included if and only if they are connected to
strong edges. The logic is of course that noise and other small variations are unlikely
to result in a strong edge (with proper adjustment of the threshold levels). Thus strong
edges will (almost) only be due to true edges in the original image. The weak edges can
either be due to true edges or noise/color variations. The latter type will probably be
distributed independently of edges on the entire image, and thus only a small amount
will be located adjacent to strong edges. Weak edges due to true edges are much more
likely to be connected directly to strong edges. Edge tracking can be implemented
by BLOB-analysis (Binary Large OBject). The edge pixels are divided into connected
BLOBs using 8-connected neighborhood. BLOBs containing at least one strong edge
pixel are then preserved, while other BLOBs are suppressed.
The middle image shows strong edges in white, weak edges connected to strong edges in
blue, and other weak edges in red.
Chapter 3. Edge Detection 18
Figure 3.6: (a) Double thresholding (b) Edge tracking by hysteresis (c) Final output
3.1.3 Implementation of Canny Edge Detection
As noted in Section 1, all images in this worksheet (except the original) are produced
by our implementation.[5] A few things should be noted with regards to this:
1. The (source) image and the thresholds can be chosen arbitrarily.
2. Only a smoothing lter with a standard deviation of  = 1:4 is supported.
3. The implementation uses the "correct" Euclidean measure for the edge strengths.
4. The dierent lters cannot be applied to edge pixels. This causes the output image
to be 8 pixels smaller in each direction. The last step in the algorithm known as
edge tracking can be implemented as either iterative or recursive BLOB analysis.
A recursive implementation can use the grass-re algorithm.
However, our implementation uses the iterative approach. First all weak edges are
scanned for neighbor edges and joined into groups. At the same time it is marked which
groups are adjacent. Then all of these markings are examined to determine which groups
of weak edges are connected to strong edges (directly or indirectly). All weak edges that
are connected to strong edges are marked as strong edges themselves. The rest of the
weak edges are suppressed. This can be interpreted as BLOB analysis where only BLOBs
containing strong edges are preserved (and considered as one BLOB).[5] Figure 8 shows
the complete edge detection process on the test image including all intermediate results.
Chapter 3. Edge Detection 19
Figure 3.7: All steps of the edge detection.
Chapter 4
Hough Transforms
The Hough transform is a method for nding lines, circles, or other simple forms in an
image. The original Hough transform was a line transform, which is a relatively fast way
of searching a binary image for straight lines. The transform can be further generalized
to cases other than just simple lines.
4.1 Hough Line Transforms
The basic theory of the Hough line transform is that any point in a binary image could
be part of some set of possible lines.[6] If we parameterize each line by, for example, in
the gure below:
Figure 4.1: Results of Canny edge detection
for two dierent images when the high and low thresholds are set to 150 and 100,
respectively.
A slope a and an intercept b, then a point in the original image is transformed to a
locus of points in the (a; b) plane corresponding to all of the lines passing through that
20
Chapter 4. Hough Transforms 21
point. If we convert every nonzero pixel in the input image into such a set of points
in the output image and sum over all such contributions, then lines that appear in the
input (i.e., (x; y) plane) image will appear as local maxima in the output (i.e. (a; b)
plane) image. Because we are summing the contributions from each point, the (a; b)
plane is commonly called the accumulator plane.[7] It might occur to you that the slope-
intercept form is not really the best way to represent all of the lines passing through a
point (because of the considerably dierent density of lines as a function of the slope,
and the related fact that the interval of possible slopes goes from (􀀀1to+1). It is for
this reason that the actual parameterization of the transform image used in numerical
computation is somewhat dierent. The preferred parameterization represents each line
as a point in polar coordinates (; ), with the implied line being the line passing through
the indicated point but perpendicular to the radial from the origin to that point. The
equation for such a line is:
 = xcos + ysin
Figure 4.2: The Hough line transform
nds many lines in each image; some of the lines found are expected, but others may
not be.
The OpenCV Hough transform algorithm does not make this computation explicit to
the user.[6] Instead, it simply returns the local maxima in the (; ) plane. However,
we will need to understand this process in order to understand the arguments to the
OpenCV Hough line transform function.
OpenCV supports two dierent kinds of Hough line transform: the standard Hough
transform (SHT) and the progressive probabilistic Hough transform (PPHT). The SHT
is the algorithm we just looked at. The PPHT is a variation of this algorithm that, among
other things, computes an extent for individual lines in addition to the orientation. It is
probabilistic because, rather than accumulating every possible point in the accumulator
Chapter 4. Hough Transforms 22
Figure 4.3: Hough line transform in the image plane
A point (x0; y0) in the image plane (panel a) implies many lines each parameterized by
a dierent ( and ) (panel b) these lines each imply points in the (; ) plane, which
taken together form a curve of characteristic shape (panel c).
plane, it accumulates only a fraction of them. The idea is that if the peak is going to be
high enough anyhow, then hitting it only a fraction of the time will be enough to nd it;
the result of this conjecture can be a substantial reduction in computation time. Both
of these algorithms are accessed with the same OpenCV function, though the meanings
of some of the arguments depend on which method is being used.[6]
Cv Seq* cv HoughLines2( Cv Arr* image, void* line storage, int method, double rho,
double theta, int threshold, double param1 = 0, double param2 = 0);
The rst argument is the input image. It must be an 8-bit image, but the input
is treated as binary information (i.e., all nonzero pixels are considered to be equiva-
lent). The second argument is a pointer to a place where the results can be stored,
which can be either a memory storage or a plain N-by-1 matrix array (the number of
rows, N, will serve to limit the maximum number of lines returned). The next argu-
ment, method, can be CV HOUGH STANDARD, CV HOUGH PROBABILISTIC, or
CV HOUGH MULTI SCALE for (respectively) SHT, PPHT, or a multiscale variant of
SHT.
The next two arguments, rho and theta, set the resolution desired for the lines (i.e.,
the resolution of the accumulator plane). The units of rho are pixels and the units of
theta are radians; thus, the accumulator plane can be thought of as a two-dimensional
histogram with cells of dimension rho pixels by theta radians. The threshold value is
the value in the accumulator plane that must be reached for the routine to report a line.
This last argument is a bit tricky in practice; it is not normalized, so we should expect
to scale it up with the image size for SHT. Remember that this argument is, in eect,
indicating the number of points (in the edge image) that must support the line for the
line to be returned.
The param1 and param2 arguments are not used by the SHT. For the PPHT, param1
sets the minimum length of a line segment that will be returned, and param2 sets
Chapter 4. Hough Transforms 23
Figure 4.4: The Canny edge detector
(param1=50, param2=150) is run rst, with the results shown in gray, and the
progressive probabilistic Hough transform (param1 = 50; param2 = 10) is run next,
with the results overlayed in white; you can see that the strong lines are generally
picked up by the Hough transform.
the separation between co-linear segments required for the algorithm not to join them
into a single longer segment. For the multiscale HT, the two parameters are used to
indicate higher resolutions to which the parameters for the lines should be computed.
The multiscale HT rst computes the locations of the lines to the accuracy given by the
rho and theta parameters and then goes on to rene those results by a factor of param1
and param2, respectively (i.e., the nal resolution in rho is rho divided by param1 and
the nal resolution in theta is theta divided by param2).
What the function returns depends on how it was called. If the line storage value was a
matrix array, then the actual return value will be NULL. In this case, the matrix should
be of type CV32FC2 if the SHT or multi-scale HT is being used and should be CV32SC4
if the PPHT is being used. In the rst two cases, the  and  values for each line will
be placed in the two channels of the array. In the case of the PPHT, the four channels
will hold the x- and y-values of the start and endpoints of the returned segments. In all
of these cases, the number of rows in the array will be updated by cv HoughLines2() to
correctly re
ect the number of lines returned.
If the line storage value was a pointer to a memory storage, then the return value will
be a pointer to a CvSeq sequence structure. In that case, you can get each line or line seg-
ment from the sequence with a command like floatline = (float)cv GetSeqElem(lines; i);
where lines is the return value from cv HoughLines2() and i is index of the line of inter-
est. In this case, line will be a pointer to the data for that line, with line[0] and line[1]
Chapter 4. Hough Transforms 24
being the 
oating-point values  and  (for SHT and MSHT) or Cv Point structures for
the endpoints of the segments (for PPHT).
4.2 Hough Circle Transforms
The Hough circle transform works in a manner roughly analogous to the Hough line
transforms just described. The reason it is only roughly is that if one were to try doing
the exactly analogous thing,the accumulator plane would have to be replaced with an
accumulator volume with three dimensions: one for x, one for y, and another for the circle
radius r. This would mean far greater memory requirements and much slower speed.
The implementation of the circle transform in OpenCV avoids this problem by using a
somewhat more tricky method called the Hough gradient method. The Hough gradient
method works as follows. First the image is passed through an edge detection phase
(in this case, cv Canny()). Next, for every nonzero point in the edge image, the local
gradient is considered (the gradient is computed by rst computing the rst order Sobel
x- and y-derivatives via cv Sobel()). Using this gradient, every point along the line
indicated by this slope from a specied minimum to a specied maximum distance is
incremented in the accumulator. At the same time, the location of every one of these
nonzero pixels in the edge image is noted. The candidate centers are then selected
from those points in this (two-dimensional) accumulator that are both above some given
threshold and larger than all of their immediate neighbors. These candidate centers are
sorted in descending order of their accumulator values, so that the centers with the most
supporting pixels appear rst. Next, for each center, all of the nonzero pixels (recall
that this list was built earlier) are considered. These pixels are sorted according to their
distance from the center. Working out from the smallest distances to the maximum
radius, a single radius is selected that is best supported by the nonzero pixels. A center
is kept if it has sucient support from the nonzero pixels in the edge Image and if it is
a sucient distance from any previously selected center. This implementation enables
the algorithm to run much faster and, perhaps more importantly, helps overcome the
problem of the otherwise sparse population of a three dimensional accumulator, which
would lead to a lot of noise and render the results unstable. On the other hand, this
algorithm has several shortcomings that you should be aware of.
First, the use of the Sobel derivatives to compute the local gradient and the attendant
assumption that this can be considered equivalent to a local tangent is not a numerically
stable proposition. It might be true most of the time, but you should expect this to
generate some noise in the output.
Chapter 4. Hough Transforms 25
Figure 4.5: The Hough circle transform
nds some of the circles in the test pattern and (correctly) nds none in the
photograph.
Second, the entire set of nonzero pixels in the edge image is considered for every can-
didate center; hence, if you make the accumulator threshold too low, the algorithm will
take a long time to run. Third, because only one circle is selected for every center, if
there are concentric circles then you will get only one of them.
Finally, because centers are considered in ascending order of their associated accumu-
lator value and because new centers are not kept if they are too close to previously
accepted centers, there is a bias toward keeping the larger circles when multiple circles
are concentric or approximately concentric. (It is only a bias because of the noise aris-
ing from the Sobel derivatives; in a smooth image at innite resolution, it would be a
certainty).
With all of that in mind, let's move on to the OpenCV routine that does all this for us:
CvSeq* cv HoughCircles( CvArr* image, void* circle storage, int method, double dp,
double mindist, double param1 = 100, double param2 = 300, int min radius = 0, int
max radius = 0 );
The Hough circle transform function cv HoughCircles() has similar arguments to the
line transform. The input image is again an 8-bit image. One signicant dierence
between cv HoughCircles() and cv HoughLines2() is that the latter requires a binary
image. The cv HoughCircles() function will internally (automatically) call cv Sobel()*
for you, so you can provide a more general gray-scale image.
The circle storage can be either an array or memory storage, depending on how you
would like the results returned. If an array is used, it should be a single column of
Chapter 4. Hough Transforms 26
type CV 32FC3; the three channels will be used to encode the location of the circle and
its radius. If memory storage is used, then the circles will be made into an OpenCV
sequence and a pointer to that sequence will be returned by cv HoughCircles(). (Given
an array pointer value for circle storage, the return value of cv HoughCircles() is NULL.)
The method argument must always be set to CV HOUGH GRADIENT.
The parameter dp is the resolution of the accumulator image used. This parameter
allows us to create an accumulator of a lower resolution than the input image. (It
makes sense to do this because there is no reason to expect the circles that exist in
the image to fall naturally into the same number of categories as the width or height
of the image itself.) If dp is set to 1 then the resolutions will be the same; if set to a
larger number (e.g., 2),then the accumulator resolution will be smaller by that factor
(in this case, half). The value of dp cannot be less than 1. The parameter min dist is
the minimum distance that must exist between two circles in order for the algorithm to
consider them distinct circles. For the (currently required) case of the method being set
to CV HOUGH GRADIENT, the next two arguments, param1 and param2, are the edge
(Canny) threshold and the accumulator threshold, respectively. You may recall that the
Canny edge detector actually takes two dierent thresholds itself. When cv Canny() is
called internally, the rst (higher) threshold is set to the value of param1 passed into
cv HoughCircles(), and the second (lower) threshold is set to exactly half that value.
The parameter param2 is the one used to threshold the accumulator and is exactly
analogous to the threshold argument of cv HoughLines().[7]
The nal two parameters are the minimum and maximum radius of circles that can be
found. This means that these are the radii of circles for which the accumulator has a
representation. The Example shows an example program using cv HoughCircles().
Example. Using cv HoughCircles to return a sequence of circles found in a gray-scale
image
]include < cv:h >
]include < highgui:h >
]include < math:h >
int main(int argc, char argv)
IplImage* image = cvLoadImage(argv[1],
CV LOAD IMAGEGRAYSCALE
);
CvMemStorage* storage = cvCreateMemStorage(0);
cvSmooth(image, image, CV GAUSSIAN, 5, 5 );
Chapter 4. Hough Transforms 27
CvSeq* results = cv HoughCircles(
image,
storage,
CV HOUGH GRADIENT,
2,
image-> width=10
);
for(inti = 0; i < results􀀀 > total; i + +)

oat* p = (
oat*) cv GetSeqElem( results, i );
CvPoint pt = cvPoint( cvRound( p[0] ), cvRound( p[1] ) );
cvCircle(
image,
pt,
cvRound( p[2] ),
CV RGB (0xff; 0xff; 0xff)
);
cv NamedWindow( cv HoughCircles, 1 );
cv ShowImage( cv HoughCircles, image);
cvWaitKey(0);
It is worth re
ecting momentarily on the fact that, no matter what tricks we employ,
there is no getting around the requirement that circles be described by three degrees
of freedom (x, y, and r), in contrast to only two degrees of freedom (and) for lines.
The result will invariably be that any circle-nding algorithm requires more memory
and computation time than the line-nding algorithms we looked at previously. With
this in mind, it's a good idea to bound the radius parameter as tightly as circumstances
allow in order to keep these costs under control. The Hough transform was extended
to arbitrary shapes by Ballard in 1981 basically by considering objects as collections of
gradient edges.[6] [7]
Chapter 5
Human Detection
Human detection is the process of nding humans within image or videos rst, a classier
(namely a cascade of boosted classiers working with haar-like features) is trained with
a few hundred sample views of a particular object (i.e., a humans), called positive
examples, that are scaled to the same size (say, 20x20), and negative examples - arbitrary
body of the same size.[8] After a classier is trained, it can be applied to a region of
interest (of the same size as used during the training) in an input humans image. The
classier outputs a "1" if the region is likely to show the object (i.e., a humans), and
"0" otherwise. To search for the object in the whole image one can move the search
window across the image and check every location using the classier. The classier is
designed so that it can be easily "re-sized" in order to be able to nd the objects of
interest at dierent sizes, which is more ecient than re-sizing the image itself. So, to
nd an object of an unknown size in the humans, the scan procedure should be done
several times at dierent scales. Humans detection training takes a lot of process and
when we take some image and a kernel to detect the edges it looks like this:
Figure 5.1: Edge detection
Output image (right) has high intensity at pixels where the convolution kernel pixel
pattern matches perfectly with the input image. Haar features are similar to these
convolution kernels which are used to detect the presence of that feature in the given
image. Each feature results in a single value which is calculated by subtracting the sum
of pixels under white rectangle from the sum of pixels under black rectangle.[8]
28
Chapter 5. Full Body Detection 29
Figure 5.2: Haar features
5.1 The Viola Jones Algorithm
Viola Jones algorithm uses a 24x24 window as the base window size to start evaluating
these features in any given image. If we consider all possible parameters of the haar
features like position, scale and type we end up calculating about 160,000+ features in
this window.
Since it is clear that huge number of these rectangular haar features have to be evaluated
each time Viola Jones have come up with a neat technique to reduce the computation
rather than summing up all pixel values under the black and white rectangles every
time.
They have introduced the concept of integral image to nd the sum of all pixels under
a rectangle with just 4 corner values of the integral image.
5.1.1 Integral Images
In an integral image the value at pixel (x; y) is the sum of pixels above and to the left
of (x; y).
Integral image allows for the calculation of sum of all pixels inside any given rectangle
using only four values at the corners of the rectangle. As stated previously there can
be approximately 160,000 + feature values within a detector at 24x24 base resolution
which need to be calculated. But it is to be understood that only few set of features
will be useful among all these features to identify an image. Those useful few features
are selected by an algorithm called Adaboost.[8]
5.1.2 Adaboost
Adaboost is a machine learning algorithm which helps in nding only the best features
among all these 160,000+ features. After these features are found a weighted combi-
nation of all these features in used in evaluating and deciding any given window has
humans or not. Each of the selected features are considered okay to be included if they
Chapter 5. Full Body Detection 30
Figure 5.3: Integral Image
Figure 5.4: Summation of Integrals
can at least perform better than random guessing (detects more than half the cases).
These features are also called as weak classiers. Adaboost constructs a strong classier
as a linear combination of these weak classiers.
F(x) = 1f1(x) + 2f2(x) + 3f3(x) + :::
 AdaBoost starts with a uniform distribution of "weights" over training examples.
 Select the classier with the lowest weighted error (i.e. a "weak" classier)
 Increase the weights on the training examples that were misclassied.
hstrong(x) = f
1 1h1(x) + ::: + nhn(x)  1
2 (1 + ::: + n)
0 otherwise
Adaboost nds the single rectangular feature and threshold that best separates the
positive (humans) and negative (non body) training examples, in terms of weighted
error.
 Given example images (x1; y1); :::(xn; yn) where yi = 0; 1 for negative and positive
examples respectively.
Chapter 5. Full Body Detection 31
 Initialize weights w1;i = 1
2m; 1
2l for yi = 0; 1 respectively, where m and l are the
number of negatives and positives respectively.
 For t = 1; :::; T :
1. Normalize the weights,
wt;i  
Pwt;i n
j=1 wt;i
so that wt is a probability distribution.
2. For each feature,j, train a classier hj which is restricted to using a single
feature. The error is evaluated with respect to wt; 2j=
P
i wijhj(xi) 􀀀 yij.
3. Choose the classier, ht, with the lowest error 2t.
4. Update the weights:
wt+1;i = wt;i1􀀀2i
t
where 2i= 0 if example xi is classied correctly, 2i= 1 otherwise, t = 2t
1􀀀2t
 The nal strong classier is : h(x) = f
1
PT
t=1 tht(x)  1
2
PT
t=1 t
0 otherwise
where t = log 1
t
The basic principle of the Viola-Jones detection algorithm is to scan the detector many
times through the same image each time with a new size. Even if an image should
contain one or more bodies it is obvious that an excessive large amount of the evaluated
sub-windows would still be negatives (non-humans).So the algorithm should concentrate
on discarding non-humans quickly and spend more time on probable human regions.
Hence a single strong classier formed out of linear combination of all best features is
not a good to evaluate on each window because of computation cost.
Therefore a cascade classier is used which is composed of stages each containing a
strong classier. So all the features are grouped into several stages where each stage
has certain number of features. The job of each stage is used to determine whether a
given sub window is denitely not a human or may be a human. A given sub window is
immediately discarded as not a human if it fails in any of the stage.
5.1.3 Cascade Training
To design a cascade we must choose:
 Number of stages in cascade (strong classiers).
Chapter 5. Full Body Detection 32
 Number of features of each strong classier.
 Threshold of each strong classier (the 1
2
PT
i=1  in denition) strong classier
denition: h(x) = f
1
PT
i=1 ihi(x)  1
2
PT
i=1 i
0 otherwise
where i = log( 1
i
); i = 2i
1􀀀2i
We can raise the question Can we nd optimum combination? Since nding optimum
combination is extremely dicult. Viola and Jones suggested a heuristic algorithm for
the cascade training.
 Manual Tweaking
{ select fi (Maximum Acceptable False Positive rate / stage)
{ select di (Minimum Acceptable True Positive rate / stage)
{ select Ftarger (Target Overall False Positive rate)
 Until Ftarger is met:
{ Add new stage
{ Until fi , di rates are met for this stage
Keep adding features and train new strong classier with AdaBoost.[8]
Chapter 6
Hue-Saturation-Value (HSV)
Object detection and segmentation is the most important and challenging fundamental
task of computer vision. It is a critical part in many applications such as image search,
image auto-annotation and scene understanding. However it is still an open problem
due to the complexity of object classes and images. The easiest way to detect and
segment an object from an image is the color based methods. The colors in the object
and the background should have a signicant color dierence in order to segment objects
successfully using color based methods.
In this part, we are going to convert a video into a binary image based on the red
color or green colors of trac light. (Red color area of the video is assigned to '1' and
other area is assigned to '0' in the binary image). OpenCV usually captures images and
videos in 8-bit, unsigned integer, BGR format. In other words, captured images can be
considered as 3 matrices, BLUE,RED and GREEN with integer values ranges from 0
to 255.[9] Usually, one can think that BGR color space is more suitable for color based
segmentation. But HSV color space is the most suitable color space for color based
image segmentation. So, in our project, we have converted the color space of original
image of the video from BGR to HSV image.
HSV color space consists of 3 matrices, 'hue', 'saturation' and 'value'. In OpenCV, value
range for 'hue', 'saturation' and 'value' are respectively 0-179, 0-255 and 0-255. 'Hue'
represents the color, 'saturation' represents the amount to which that respective color
is mixed with white and 'value' represents the amount to which that respective color is
mixed with black.[9]
33
Chapter 6. Hue-Saturation-Value (HSV) 34
6.1 HSV for trac light detection
In our application, we have considered that the red object has 'hue', 'saturation' and
'value' in between 170-180, 160-255, 60-255 respectively. Here the 'hue' is unique for
that specic color distribution of that object. But 'saturation' and 'value' may be vary
according to the lighting condition of that environment.
Hue values of basic colors
1. Orange 0-22
2. Yellow 22- 38
3. Green 38-75
4. Blue 75-130
5. Violet 130-160
6. Red 160-179
These are approximate values. We have to nd the exact range of 'hue' values according
to the color of the object. We found that the range of 170-179 is perfect for the range of
hue values of our object or light. The 'saturation' and 'value' is depend on the lighting
condition of the environment as well as the surface of the object.[9]
cv InRangeS(const CvArr* src,
CvScalar lower,
CvScalar upper,
CvArr* dst)
Checks that each array element of 'src' lies between 'lower' and 'upper'. If so, array
element in the relevant location of 'dst' is assigned '255' , otherwise '0'.
Argument description:
 const CvArr* src - source array which is the image
 CvScalar lower - inclusive lower bound (In the above application, it is cvScalar(170,160,60)
because my lower bound for 'hue','saturation' and 'value' is 170,160 and 60 respec-
tively).
 CvScalar upper - exclusive upper bound (In the above application, it is cvS-
calar(179,255,255) because my upper bound for 'hue','saturation' and 'value' is
179,255 and 255 respectively)
 CvArr* dst - destination array which is the binary image (must have 8-bit unsigned
integer or 8-bit signed integer type)
Chapter 6. Hue-Saturation-Value (HSV) 35
Therefore, by using HSV, we can determine whether the trac light is on or o so that
the car stops when ever a red color signal from the trac light is received or sensed by
the camera. Output images of a webcam is little bit noisy. So, we smooth each frame
of the video and each binary thresholded images with a Gaussian 3x3 kernel.
Chapter 7
Arduino Programing and Serial
Comunication
7.1 Arduino Programing
The Arduino microcontroller is an easy to use yet powerful single board computer that
has gained considerable traction in the hobby and professional market. The Arduino is
open-source, which means hardware is reasonably priced and development software is
free.
The Arduino project was started in Italy to develop low cost hardware for interaction
design. An overview is on the Wikipedia entry for Arduino.[10]
The Arduino hardware comes in several 
avors. In the United States, Sparkfun is a good
source for Arduino hardware. This chapter covers the Arduino Uno board, a good choice
for our project. With the Arduino board, we can write programs and create interface
circuits to read switches and other sensors, and to control motors and lights with very
little eort.
The Arduino Uno SMD is a version of the Arduino Uno, but uses a surface mount
version of the Atmega328P instead of the through-hole version. This version was made
in response to a shortage in supply of the through-hole Atmega328P.[10] The board is
based on the ATmega328 (datasheet). It has 14 digital input/output pins (of which 6
can be used as PWM outputs), 6 analog inputs, a 16 MHz crystal oscillator, a USB
connection, a power jack, an ICSP header, and a reset button. It contains everything
needed to support the microcontroller; simply connect it to a computer with a USB
cable or power it with a AC-to-DC adapter or battery to get started.
36
Chapter 7. Arduino Programing and Serial Comunication 37
Figure 7.1: The Arduino Board
The Uno diers from all preceding boards is that it does not use the FTDI USB-to-
serial driver chip. Instead, it features the Atmega8U2 programmed as a USB-to-serial
converter.
"Uno" means one in Italian and is named to mark the upcoming release of Arduino 1.0.
The Uno and version 1.0 will be the reference versions of Arduino, moving forward. The
Uno is the latest in a series of USB Arduino boards, and the reference model for the
Arduino platform.[10]
Operating Voltage 5V
Input Voltage (recommended) 7-12V
Input Voltage (limits) 6-20V
Digital I/O Pins 14 (of which 6 provide PWM output)
Analog Input Pins 6
DC Current per I/O Pin 40 mA
DC Current for 3.3V Pin 50 mA
Flash Memory 32 KB (ATmega328) of which 0.5 KB used by bootloader
SRAM 2 KB (ATmega328)
EEPROM 1 KB (ATmega328)
Clock Speed 16 MHz
Table 7.1: Arduino Specications
7.1.1 Power
The Arduino Uno can be powered via the USB connection or with an external power
supply. The power source is selected automatically. External (non-USB) power can come
either from an AC-to-DC adapter (wall-wart) or battery. The adapter can be connected
by plugging a 2.1mm center-positive plug into the board's power jack. Leads from a
battery can be inserted in the Gnd and Vin pin headers of the POWER connector.
Chapter 7. Arduino Programing and Serial Comunication 38
The board can operate on an external supply of 6 to 20 volts. If supplied with less
than 7V, however, the 5V pin may supply less than ve volts and the board may be
unstable. If using more than 12V, the voltage regulator may overheat and damage the
board. The recommended range is 7 to 12 volts. The power pins are as follows:VIN. The
input voltage to the Arduino board when it's using an external power source (as opposed
to 5 volts from the USB connection or other regulated power source). You can supply
voltage through this pin, or, if supplying voltage via the power jack, access it through
this pin. 5V. The regulated power supply used to power the microcontroller and other
components on the board. This can come either from VIN via an on-board regulator, or
be supplied by USB or another regulated 5V supply. 3V3. A 3.3 volt supply generated
by the on-board regulator. Maximum current draw is 50 mA.GND. Ground pins.[10]
7.1.2 Memory
The ATmega328 has 32 KB (with 0.5 KB used for the bootloader). It also has 2 KB of
SRAM and 1 KB of EEPROM.
7.1.3 Input and Output
Each of the 14 digital pins on the Uno can be used as an input or output, using pin-
Mode(), digitalWrite(), and digitalRead() functions. They operate at 5 volts. Each pin
can provide or receive a maximum of 40 mA and has an internal pull-up resistor (discon-
nected by default) of 20-50 kOhms. In addition, some pins have specialized functions:
Serial: 0 (RX) and 1 (TX). Used to receive (RX) and transmit (TX) TTL serial data.
These pins are connected to the corresponding pins of the ATmega8U2 USB-to-TTL
Serial chip.External Interrupts: 2 and 3. These pins can be congured to trigger an
interrupt on a low value, a rising or falling edge, or a change in value. See the attachIn-
terrupt() function for details. PWM: 3, 5, 6, 9, 10, and 11. Provide 8-bit PWM output
with the analogWrite() function.
SPI: 10 (SS), 11 (MOSI), 12 (MISO), 13 (SCK). These pins support SPI communication
using the SPI library.LED: 13. There is a built-in LED connected to digital pin 13.
When the pin is HIGH value, the LED is on, when the pin is LOW, it's o.
The Uno has 6 analog inputs, labeled A0 through A5, each of which provide 10 bits of
resolution (i.e. 1024 dierent values). By default they measure from ground to 5 volts,
though is it possible to change the upper end of their range using the AREF pin and
the analogReference() function. Additionally, some pins have specialized functionality:
Chapter 7. Arduino Programing and Serial Comunication 39
I2C: A4 (SDA) and A5 (SCL). Support I2C (TWI) communication using the Wire
library.
There are a couple of other pins on the board: AREF. Reference voltage (0 to 5V only)
for the analog inputs. Used with analogReference().
Reset. Bring this line LOW to reset the microcontroller. Typically used to add a reset
button to shields which block the one on the board.[10]
7.1.4 Communication
The Arduino Uno has a number of facilities for communicating with a computer, another
Arduino, or other microcontrollers. The ATmega328 provides UART TTL (5V) serial
communication, which is available on digital pins 0 (RX) and 1 (TX). An ATmega8U2
on the board channels this serial communication over USB and appears as a virtual com
port to software on the computer. The '8U2 rmware uses the standard USB COM
drivers, and no external driver is needed. However, on Windows, a .inf le is required.
The Arduino software includes a serial monitor which allows simple textual data to be
sent to and from the Arduino board. The RX and TX LEDs on the board will 
ash
when data is being transmitted via the USB-to-serial chip and USB connection to the
computer (but not for serial communication on pins 0 and 1).[10]
A SoftwareSerial library allows for serial communication on any of the Uno's digital pins.
The ATmega328 also supports I2C (TWI) and SPI communication. The Arduino soft-
ware includes a Wire library to simplify use of the I2C bus.
7.1.5 Programming
The Arduino Uno can be programmed with the Arduino software. Select "Arduino
Uno from the Tools > Board menu (according to the microcontroller on your board).
The ATmega328 on the Arduino Uno comes preburned with a bootloader that allows
you to upload new code to it without the use of an external hardware programmer. It
communicates using the original STK500 protocol. we can also bypass the bootloader
and program the microcontroller through the ICSP (In-Circuit Serial Programming)
header. The ATmega8U2 rmware source code is available . The ATmega8U2 is loaded
with a DFU bootloader. The Uno SMD has a pulldown resistor tying the HWB pin
to ground, so all that's needed to enter DFU mode is to brie
y short enough to short
pins 5 and 6 of the 8U2 icsp connector. This will connect the 8U2 reset pin to ground.
we can then use Atmel's FLIP software (Windows) or the DFU programmer (Mac OS
Chapter 7. Arduino Programing and Serial Comunication 40
X and Linux) to load a new rmware. Or we can use the ISP header with an external
programmer (overwriting the DFU bootloader).
7.1.6 Servo control in arduino
Servo motors have three wires: power, ground, and signal. The power wire is typically
red, and should be connected to the 5V pin on the Arduino board. The ground wire
is typically black or brown and should be connected to a ground pin on the Arduino
board. The signal pin is typically yellow, orange or white and should be connected to
pin 9 on the Arduino board.
Figure 7.2: Servo control scheme in arduino
7.1.7 Arduino Serial Communication
Arduinos have built in support for serial communication on pins 0 and 1, but what if we
need more serial ports? The Software Serial Library has been developed to allow serial
communication to take place on the other digital pins of your Arduino, using software
to replicate the functionality of the hardwired RX and TX lines. This can be extremely
helpful when the need arises to communicate with two serial enabled devices, or to talk
with just one device while leaving the main serial port open for debugging purpose.[10]
In the example below, digital pins 10 and 11 on us Arduino are used as virtual RX and
TX serial lines. The virtual RX pin is set up to listen for anything coming in on via
the main serial line, and to then echo that data out the virtual TX line. Conversely,
anything received on the virtual RX is sent out over the hardware TX.
7.1.8 Automatic Software Reset
Rather than requiring a physical press of the reset button before an upload, the Arduino
Uno is designed in a way that allows it to be reset by software running on a connected
computer. One of the hardware 
ow control lines (DTR) of the ATmega8U2 is connected
Chapter 7. Arduino Programing and Serial Comunication 41
to the reset line of the ATmega328 via a 100 nanofarad capacitor. When this line is
asserted (taken low), the reset line drops long enough to reset the chip. The Arduino
software uses this capability to allow us to upload code by simply pressing the upload
button in the Arduino environment. This means that the bootloader can have a shorter
timeout, as the lowering of DTR can be well-coordinated with the start of the upload.
This setup has other implications. When the Uno is connected to either a computer
running Mac OS X or Linux, it resets each time a connection is made to it from software
(via USB). For the following half-second or so, the bootloader is running on the Uno.
While it is programmed to ignore malformed data (i.e. anything besides an upload of
new code), it will intercept the rst few bytes of data sent to the board after a connection
is opened. If a sketch running on the board receives one-time conguration or other data
when it rst starts, make sure that the software with which it communicates waits a
second after opening the connection and before sending this data.
The Uno contains a trace that can be cut to disable the auto-reset. The pads on either
side of the trace can be soldered together to re-enable it. It's labeled "RESET-EN". we
may also be able to disable the auto-reset by connecting a 110 ohm resistor from 5V to
the reset line.
7.1.9 USB Overcurrent Protection
The Arduino Uno has a resettable polyfuse that protects our computer's USB ports from
shorts and overcurrent. Although most computers provide their own internal protection,
the fuse provides an extra layer of protection. If more than 500 mA is applied to the
USB port, the fuse will automatically break the connection until the short or overload
is removed.[10]
7.1.10 Physical Characteristics
The maximum length and width of the Uno PCB are 2.7 and 2.1 inches respectively,
with the USB connector and power jack extending beyond the former dimension. Four
screw holes allow the board to be attached to a surface or case.
7.2 Serial Comunication
Serial communication is often used either to control or to receive data from an embedded
microprocessor. Serial communication is a form of I/O in which the bits of a byte begin
Chapter 7. Arduino Programing and Serial Comunication 42
transferred appear one after the other in a timed sequence on a single wire. Serial
communication has become the standard for inter-computer communication. Many PCs
and compatible computers are equipped with two serial ports and one parallel port.
Although these two types of ports are used for communicating with external devices,
they work in dierent ways.
A parallel port sends and receives data eight bits at a time over 8 separate wires. This
allows data to be transferred very quickly; however, the cable required is more bulky
because of the number of individual wires it must contain. Parallel ports are typically
used to connect a PC to a printer and are rarely used for much else. A serial port sends
and receives data one bit at a time over one wire. While it takes eight times as long to
transfer each byte of data this way, only a few wires are required. In fact, two-way (full
duplex) communications is possible with only three separate wires - one to send, one to
receive, and a common signal ground wire.
7.2.1 CSerial class member functions
CSerial::CSerial() - Basic c'tor that takes no arguments.
CSerial::Open(int nPort = 2, int nBaud = 9600 ) - This member function is used to
open the serial port. It takes two integer arguments. The rst argument contains the
port number where the valid entries are 1 through 4. The second argument is the baud
rate. Valid values for this argument are 1200, 2400, 4800, 9600, 19200, 38400 and 76800.
This function returns TRUE if successful. Otherwise, it returns a value of FALSE.
CSerial::Close() - While the d'tor will automatically close the serial port for you, this
function has been added just in case there is a reason that you need to explicit close the
port.
CSerial::SendData(const char *, int) - This function writes data from a buer to the
serial port. The rst argument it takes is a const char* to a buer that contains the
data being sent. The second argument is the number of bytes being sent. This function
will return the actual number of bytes that are successfully transmitted.
CSerial::ReadDataWaiting(void) - This function simply returns the number of bytes
that waiting in the communication port's buer. It basically allows you to "peek" at
the buer without actually retrieving the data.[11]
Chapter 8
Hardware Work
The hardwares we are using are the computer which process the whole image processing
,serial communication and data storing ,arduino micro controller which gather the sensor
values and control the servo motors, servo motors which are the actuators to ride the
car in forward and reverse direction and some glass sheet to work on the frame of the
robot car.
8.1 Servo motor(SM-SR303R)
8.1.1 Servo working Mechanism
As the name suggests, a servomotor is a servomechanism. More specically, it is a
closed-loop servomechanism that uses position feedback to control its motion and nal
position. The input to its control is some signal, either analogue or digital, representing
the position commanded for the output shaft. The motor is paired with some type of
encoder to provide position and speed feedback. In the simplest case, only the position is
measured. The measured position of the output is compared to the command position,
the external input to the controller. If the output position diers from that required,
an error signal is generated which then causes the motor to rotate in either direction, as
needed to bring the output shaft to the appropriate position. As the positions approach,
the error signal reduces to zero and the motor stops.
The very simplest servomotors use position-only sensing via a potentiometer and bang-
bang control of their motor; the motor always rotates at full speed (or is stopped). This
type of servomotor is not widely used in industrial motion control, but they form the
basis of the simple and cheap servos used for radio-controlled models.
43
Chapter 8. Hardware Work 44
More sophisticated servomotors measure both the position and also the speed of the
output shaft. They may also control the speed of their motor, rather than always
running at full speed. Both of these enhancements, usually in combination with a PID
control algorithm, allow the servomotor to be brought to its commanded position more
quickly and more precisely, with less overshooting. Circuit Servo motors have three wires:
power, ground, and signal. The power wire is typically red, and should be connected
to the 5V pin on the Arduino board. The ground wire is typically black or brown and
should be connected to a ground pin on the Arduino board. The signal pin is typically
yellow, orange or white and should be connected to a digital pin on the Arduino board.
Note that servos draw considerable power, so if we need to drive more than one or two,
we will probably need to power them from a separate supply (i.e. not the +5V pin
on your Arduino). Be sure to connect the grounds of the Arduino and external power
supply together.
SM-SR303R is a simple, high quality continuous full-rotation servo motor. A standard
3-pin power and control cable is attached and all hardware shown is included.
8.1.2 Features
The SM-SR303R servo motor have the following features:
1. Continuous 360o rotation.
2. Rest point adjustment.
3. Operating voltage: 4.8-6.0VDC.
4. Top operating speed: 60-70RPM (4.8-6.0VDC respectively).
5. Torque: 3.3-4.8 kg-cm (4.8-6.0VDC respectively).
6. 4 plastic gears + 1 metal gear.
7. Double ball bearing.
8.1.3 Dimensions
The dimension of the SM-SR303R servo motor is:
1. 42 x 39.5 x 22.5mm.
2. Wire length: 30cm.
3. Weight: 44g.
Chapter 8. Hardware Work 45
8.1.4 Servo programming
The most common and important command for our arduino programing is the write()
command which writes a value to the servo, controlling the shaft accordingly. On a
standard servo, this will set the angle of the shaft (in degrees), moving the shaft to that
orientation. On a continuous rotation servo, this will set the speed of the servo (with 0
being full-speed in one direction, 180 being full speed in the other, and a value near 90
being no movement).
8.2 Computer
The computer is used for controlling the arduino by processing the images from the
camera. In order to process the images and to send controlling signal to the arduino the
following soft-wares are mandatory.
8.2.1 Software Required
1. Arduino IDE 1.0 for Windows.
2. OpenCV 2.3.1(2.1 ) SuperPack For Windows.
3. Microsoft Visual C++ 2010 Express SP1.
4. Serial C++ Library for Win32 (by Thierry Schneider).
8.2.2 Installation and Integration
Download and install the OpenCV-2.3.1(2.1)-win-superpack.exe if you don't wish to deal
with generating the support les yourself. Everything you need from OpenCV to build
this project has already been generated in this download.
The OpenCV installation documentation explains how to make Visual C++ aware of the
OpenCV support les (include, bin, etc). This is not a one-click job. Careful attention
must be given to how Visual C++ must be congured to recognize OpenCV les.
The computer will accept the input signal from the camera and proximity sensor through
the arduino serial and analogue inputs respectively and it will send the control signal to
the micro controller. But we didnt nd the proximity sensor in our lab so that we are
unable to control the car by this sensor.
Chapter 8. Hardware Work 46
8.2.3 Glass shit and other supporting materials
We use 60*40 cm glass for making the frames and some bolt and nut to attach the
frames and servo strongly.
Figure 8.1: The robot car with glass frame
Chapter 9
Result and Conclusion
9.1 Result
The project's results were very impressive and amazing. The computer vision code is
successfully able to get the road lanes,humans,zebra lines,cars and trac lights in near
real time, and the implementation on the actual car in real road was equally impressive.
The servo motors are successfully adjusted for changes in the lane position and human
body detection so that the robot was able to move correctly. Ultimately, in real world
conditions with nonadjustable lighting conditions, the robot was mostly able to follow
the line and detect the whole objects clearly.
There were certain challenges in implementing our design. The brunt of the problems
came from the diculty in producing a fast yet accurate vision algorithm. Our group ran
through many dierent algorithms until choosing an eective algorithm from a number
of multiple vision algorithms. Also, the complexity of the code forced us to run the
web-camera at a reduced frame rate. This also meant that the resulting accuracy of
the robot would decrease. Finally, with the reduced frame-rate, we had to drive the car
motors at slower speeds in order to eectively capture the object in each frame.
We are unable nd the stepper motor in our campus so we decided to run the car with
full rotation servo motor. The servo has some good result in carrying the computer and
other materials.
47
Chapter 9. Result and Conclusion 48
9.2 Conclusion
In many ways self-driving cars are a logical extension of existing driver aids such as
lane-keeping systems (which follow road markings and sound a warning and correct
the steering if a vehicle starts to drift out of its lane), adaptive cruise control (which
maintains a constant distance from the vehicle in front, rather than a constant speed),
auto-parking systems (which can reverse a car into a parking space), emergency braking
(which slams on the brakes if an obstacle, another vehicle or a pedestrian is detected
in front of the car). Computerized control of a car's steering, acceleration and braking
is already possible under some circumstances, in other words. For a car to drive itself,
these systems must all be tied together using software, and supplemented with a set of
sensors so that the software can tell what is going on around the vehicle.
Finally when we see the car accidents that came from drivers fault, the robot car appli-
cation is essential to save human's death and loss of property. Autonomous (robot)cars
make a lot of sense to the military. the robot can be run more eciently, and fallible
human drivers can be supported by machines on days-long journeys across deserts and
on tedious concrete roads.
Chapter 9. Result and Conclusion 49
9.3 Recommendation
As we described earlier our project is based on Driver-less car technology and it is
not advanced enough to develop stable image processing in real time specially when
controlling the lane and template matching so we recommend for feature work, it needs
some additional image processing steps. In order to improve the speed and carrying
power of the robot the robot servo has to be changed by DC or stepper motors. The
wheels are too tin and they have to be changed by other big wheels.
Finally we would like to recommend the department to give lectures on image processing
and robotics. We didn't saw any project that have been worked using this topics. It
is better for the students because they are the most new and essential part of today's
technology.
Appendix A
Servo controller program
] include <Servo.h>
Servo servoLeft; ////servo object
Servo servoRight;
int ledleft=11;
int ledright=13;
int ledstop=9;
void setup() f
Serial.begin(9600); // set serial speed for serial communication
servoLeft.attach(7);
servoRight.attach(6);
pinMode(ledleft, OUTPUT);
pinMode(ledright, OUTPUT);
pinMode(ledstop, OUTPUT);
g
void loop()f
while (Serial.available() == 0); // do nothing if nothing sent
int val = Serial.read() - '0'; // deduct ascii value of '0' to nd numeric value of sent
number
if (val == 5) //test for command 5 then start the servo to move
f
delay(1000);
servoLeft.write(0);
servoRight.write(180);
digitalWrite(ledstop, LOW);
g
else if (val == 1) // test for command 1 then turn the servo to left
50
Appendix A. Servo controller program 51
f
servoLeft.write(180); // tell servo to go left
servoRight.write(180);
digitalWrite(ledleft, HIGH);
digitalWrite(ledleft, LOW);
g
else if (val == 2) // test for command 2 then turn the servo to right
f
servoRight.write(0); // tell servo to go right
servoLeft.write(0);
digitalWrite(ledright, HIGH);
delay(100);
digitalWrite(ledright, LOW);
g
else if (val == 0) // test for command 0 then turn the servo to go straight
f
servoRight.write(180); // tell servo to go straight
servoLeft.write(0);
g
else if(val == 6) // test for command 6 then stop the servos
f
servoRight.write(90); // tell servo to stop
servoLeft.write(90);
digitalWrite(ledstop, HIGH);
g
Serial.
ush(); // clear serial port
g
Bibliography
[1] . URL http://mrg.robots.ox.ac.uk/robotcar/howitworks.html.
[2] . URL http://www.businessweek.com/articles/2013-03-28/
googles-self-driving-robot-cars-are-ruining-my-commute.
[3] . URL https://en.wikipedia.org/wiki/Autonomous_car.
[4] . URL http://docs.opencv.org/doc/tutorials/imgproc/histograms/
template_matching/template_matching.html.
[5] . URL http://docs.opencv.org/doc/tutorials/imgproc/imgtrans/canny_
detector/canny_detector.html.
[6] . URL http://docs.opencv.org/doc/tutorials/imgproc/imgtrans/hough_
lines/hough_lines.html.
[7] Gary Bradski and Adrian Kaehler. Learning opencv. September 2008.
[8] . URL http://docs.opencv.org/doc/tutorials/objdetect/cascade_
classifier/cascade_classifier.html.
[9] . URL http://docs.opencv.org/doc/tutorials/imgproc/histograms/
histogram_comparison/histogram_comparison.html.
[10] . URL http://arduino.cc/en/Reference/HomePage.
[11] . URL http://www.codeguru.com/cpp/i-n/network/serialcommunications/
article.php/c2503/CSerial--A-C-Class-for-Serial-Communications.htm.
52
