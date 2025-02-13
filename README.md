# Digital-Stethescope

<br>
<details>
  <summary>Table of Contents</summary>
    <ol>
        <li>
            <a href="#introduction">Introduction</a>
            <ul>
                <li><a href="#technologies-used">Technologies Used</a></li>
            </ul>
        </li>
        <li>
          <a href="#Objectives">Getting Started</a>
        </li>
        <li>
            <a href="#literature-survey">Literature Survey</a>
            <ul>
                <li><a href="#ESP32">MicroController</a></li>
                <li><a href="#Deep-Learning-Model">Detection Model</a></li>
            </ul>
        </li>
        <li>
              <a href="#ml-model">ML Model</a>
        </li>  
        <li>
          <a href="#Deep Learning">Deep learning</a>
        </li>
        <li>
            <a href="#references">References</a> 
        </li>
        <li>
            <a href="#project-mentors">Project Mentors</a></li>
        </li>
        <li>
            <a href="#project-members">Project Members</a></li>
        </li>   
    </ol>
</details>

<hr>

## Introduction

Digital Stethoscope aims at producing an electronics based amplifying stethoscope, which can store/ transmit the sound waveform captured to another device. Some of the advantages and motivation to switch from mechanically to electronically based amplifying are :
- Better amplification, and a more flexible range of amplification
- Noise reduction capabilities 
- Ability to store and transmit sound captures in order to analyse them on a later date 

### Technologies Used
We have used the following technologies and software for our project

<ul>
    <li>
        <a href="https://www.python.org/" target ="_blank"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Python-logo-notext.svg/1869px-Python-logo-notext.svg.png" alt="python "
        width = "50"
        height = "50"></a>
    </li>
    <li>
        <a href="https://www.tensorflow.org/" target ="_blank"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/2d/Tensorflow_logo.svg/1200px-Tensorflow_logo.svg.png" alt="TensorFlow "
        width = "50"
        height ="50"></a>
    </li>
    <li>
        <a href="https://www.analog.com/en/design-center/design-tools-and-calculators/ltspice-simulator.html" target ="_blank"><img src="https://github.com/gagan20003/Digital-Stethoscope/blob/main/resources/ltspice%20logo.jpeg" alt="LTSpice"
        width = "50"
        height = "50"></a>
    </li>
    <li>
        <a href="https://exploreembedded.com/wiki/Basics_of_AVR_%27C%27" target ="_blank"><img src="https://t4.ftcdn.net/jpg/05/57/67/21/360_F_557672188_zkvWqyC0SoWFRKsdyO6PaZzWmKYs484Q.jpg" alt="AVR C"
        width = "50"
        height = "50"></a>
    </li>
    <li>
        <a href="https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/index.html" target ="_blank"><img src="https://github.com/gagan20003/Digital-Stethoscope/blob/main/resources/esp%20logo.jpeg" alt="ESP32"
        width = "50"
        height = "50"></a>
    </li>
</ul>

## Objectives 
The main goals we have set out for this project are 
- Make a microphone - amplification module that can detect frequencies from 50Hz to 20kHz 
- Transmit the sound clip to an associated laptop wirelessly 
- Be able to detect the disease by using an associated Deep Learning model <hr>

<!--- Microcontroller description starts --->

<h2>ESP32</h2>
<img src="https://cdn.shopify.com/s/files/1/0609/6011/2892/files/doc-esp32-pinout-reference-wroom-devkit.png?width=1384" alt="ESP32 Pinout"
  width="700"
  height="500"
  align="middle"
>
<p>The microcontroller that we are using in our project is the ESP32.
The ESP32 is a high-performance microcontroller board that is widely used in Internet of Things (IoT) applications.
Espressif Systems manufactures it, and it is the successor to the ESP8266. The ESP32 is built around a dual-core 
Tensilica LX6 processor that operates at up to 240 MHz, providing plenty of processing power for IoT applications.
</p>

The ESP32 microcontroller board has the following key features:
<ol>
<li>
    <em>Wi-Fi and Bluetooth connectivity:</em> The ESP32 includes Wi-Fi and Bluetooth connectivity, making it simple to connect to the internet and other devices.
</li>
<li>
    <em> Low power consumption:</em> The ESP32 is energy-efficient, with multiple power modes that allow it to operate on very little power.
</li>
<li>
    <em> Large Memory:</em> The ESP32 comes up with up to 520 KB of SRAM and 4MB of flash memory, which is enough to run complex applications.
</li>
<li>
    <em>GPIO pins:</em> The ESP32 has a large number of GPIO pins, which makes it easy to interface with other devices and sensors.
</li>
<li>
    <em>Development tools:</em> There are many development tools available for it including Arduino IDE, ESP-IDF, and MicroPython.
</li>
</ol>
<p>
Overall, the ESP32 is a powerful and versatile microcontroller board that is well-suited for a wide range of IoT applications. Its built-in Wi-Fi and Bluetooth capabilities, low power consumption, and large memory make it a popular choice among developers.

In this project, the esp32 is used to transmit the data collected from the microphone to the ML model over the in-built Wi-Fi.
</p> <hr>


<!--- Microcontroller description ends --->

## ML Model

CNN 

A Convolutional neural network (CNN) is a neural network that has one or more convolutional layers and are used mainly for image processing, classification, segmentation and also for other auto correlated data.
A convolution is essentially sliding a filter over the input. One helpful way to think about convolutions is this quote from Dr Prasad Samarakoon: “A convolution can be thought as “looking at a function’s surroundings to make better/accurate predictions of its outcome.”

![image](https://user-images.githubusercontent.com/97295669/224393238-dd832da9-6724-4cd7-bcbe-412659879d0c.png)


The architecture of the model used here is as follows :
|Layer (type) |               Output Shape|              Param #   |
|---------------|----------------------------|--------------------------|
| conv2d (Conv2D)     |        (None, 39, 861, 16)  |    80     |   
| max_pooling2d (MaxPooling2D ) | (None, 19, 430, 16)   |   0      |   
|dropout (Dropout)      |     (None, 19, 430, 16)   |    0         |                                                                 
| conv2d_1 (Conv2D)    |       (None, 18, 429, 32)  |     2080     |                                                                  
| max_pooling2d_1 (MaxPooling2D)|  (None, 9, 214, 32) |      0        |                                                                                   
| dropout_1 (Dropout)  |       (None, 9, 214, 32)   |    0         |                                                                
| conv2d_2 (Conv2D)    |       (None, 8, 213, 64)   |     8256      |                                                                 
| max_pooling2d_2 (MaxPooling 2D) |  (None, 4, 106, 64)  |     0     |                                                                                                 |dropout_2 (Dropout)   |      (None, 4, 106, 64)   |     0   |      
| conv2d_3 (Conv2D)     |      (None, 3, 105, 128)   |    32896    |                                                                 
| max_pooling2d_3 (MaxPooling 2D) |  (None, 1, 52, 128)  |     0   |                                                                                                    
| dropout_3 (Dropout)    |     (None, 1, 52, 128)   |     0     |                                                                     
|global_average_pooling2d (G lobalAveragePooling2D)|  (None, 128)    |          0       |                                                                                                            
|dense (Dense)      |         (None, 6)         |        774      | 

<h3>Deep Learning</h3>
RNN

<p>Recurrent Neural Network is a generalization of feedforward neural network that has an internal memory. RNN is recurrent in nature as it performs the same function for every input of data while the output of the current input depends on the past one computation. After producing the output, it is copied and sent back into the recurrent network. For making a decision, it considers the current input and the output that it has learned from the previous input.
Unlike feedforward neural networks, RNNs can use their internal state (memory) to process sequences of inputs. This makes them applicable to tasks such as unsegmented, connected handwriting recognition or speech recognition. In other neural networks, all the inputs are independent of each other. But in RNN, all the inputs are related to each other.
</p>
<img width="669" alt="Screenshot 2023-03-10 at 9 38 11 AM" src="https://www.simplilearn.com/ice9/free_resources_article_thumb/Simple_Recurrent_Neural_Network.png">

LSTM
<p>Long Short-Term Memory (LSTM) networks are a modified version of recurrent neural networks, which makes it easier to remember past data in memory. The vanishing gradient problem of RNN is resolved here. LSTM is well-suited to classify, process and predict time series given time lags of unknown duration. It trains the model by using back-propagation. In an LSTM network, three gates are present:
Input gate — discover which value from input should be used to modify the memory. Sigmoid function decides which values to let through 0,1. and tanh function gives weightage to the values which are passed deciding their level of importance ranging from-1 to 1.
Forget gate — discover what details to be discarded from the block. It is decided by the sigmoid function. it looks at the previous state(ht-1) and the content input(Xt) and outputs a number between 0(omit this)and 1(keep this)for each number in the cell state.
Output gate— the input and the memory of the block is used to decide the output. Sigmoid function decides which values to let through 0,1. and tanh function gives weightage to the values which are passed deciding their level of importance ranging from-1 to 1 and multiplied with output of Sigmoid
There were multiple architectures used that are explained in detail in the Heart-Model folder
</p>

<img width="669" src="https://media.geeksforgeeks.org/wp-content/uploads/newContent1.png">

## Model

Tried couple of architecture but one given here is as :
|Layer (type) |               Output Shape|              Param #   |
|---------------|----------------------------|--------------------------|
| LSTM     |        (None, 30, 256)   |    264192    | 
| LSTM     |        (None, 30,128)   |     197120     | 
| LSTM     |        (None, 64)        |    49408      |  
| Dense    | (None,3) | 195 |


## Results
This gave accuracies of : 
- model train data score       :  74 %
- model test data score        :  76 %
- model validation data score  :  79 %
- model unlabeled data score   :  74 %
<img width="669" alt="Screenshot 2023-03-10 at 9 38 11 AM" src="https://user-images.githubusercontent.com/119749228/224388357-968e1a6b-347e-49fd-b49e-97095111a611.png">

<!--- MFCC STARTS HERE --->
<h1>MFCC</h1>
<p>
Speech Recognition is a supervised learning task. In the speech recognition problem input will be the audio signal and we have to predict the text from the audio signal. We can’t take the raw audio signal as input to our model because there will be a lot of noise in the audio signal. It is observed that extracting features from the audio signal and using it as input to the base model will produce much better performance than directly considering raw audio signal as input. MFCC is the widely used technique for extracting the features from the audio signal.
</p>
<h3>The road map of the MFCC technique is given below:</h3>
<img src="https://github.com/gagan20003/Digital-Stethoscope/blob/main/resources/roadmap_for_mfcc.jpeg" alt="roadmap for MFCC"
width = "700"
height = "500"
align = "middle"
>
<h3>A plot of MFCCs </h3>
<img src="https://github.com/gagan20003/Digital-Stethoscope/blob/main/resources/MFCCs.jpg" alt="MFCCs">
<h3>Power Spectrogram </h3>
<img src="https://github.com/gagan20003/Digital-Stethoscope/blob/main/resources/power_spectogram.jpg" alt="MFCCs">
<!--- MFCC ends HERE --->

## Project Mentors

1. [Dharaneedaran K S](https://github.com/DharaneedaranKS)
2. [Hrishikesh Kulkarni](https://github.com/HrishiCoolkarni)

## Project Members

1. [Aditya Rajesh](https://github.com/Adityarajesh001)
2. [Aman Raj](https://github.com/amanrajNitk)
3. [Chandan Padmashali](https://github.com/CHANDAN-2003)
4. [Gagan Mahotiliya](https://github.com/gagan20003)
