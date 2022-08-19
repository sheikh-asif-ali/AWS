# AWS
Pushing Sensor data to cloud
1. Introduction:
2. Requirements:
3. Steps involved in this Tutorial:
    3.1 Creating thing, certificate and attaching a policy to the certificate
    3.2 Installing Required SDKs, and Libraries. such as “AWS IoT Python SDK” & Paho-MQTT library
        3.2.1 Installing “AWS IoT Python SDK”
        3.2.2 Installing Paho-MQTT library
    3.3 Programming Part – Creating scripts for Publishing, Subscribing to a particular thing.
        3.3.1 ei_aws_publish.py
        3.3.2 ei_aws-subscribe.py
        3.3.3 Modifications required:
    3.4 Execution of Scripts & Demonstration of Data logging
    3.5 Creating DynamoDB Rule & DynamoDB Table.
        3.5.1 Creating DynamoDB Rule
        3.5.2  Creating Amazon DynamoDB
    3.6 Execution of Scripts & Demonstration of pushing data into the DynamoDB
    
1. Introduction:

In this example, we will see How to get raspberry pi to interact with Amazon web Services & push data into the DynamoDB.

2. Requirements:

i.  Working Raspberry Pi Setup
ii. An active account on Amazon web services.

* Introduction to AWS IoT Core:

Internet of Things (IoT) is being integrated with almost every device nowadays.
There is a number of hardware and software IoT platforms are available in the market for building IoT based application.
Likewise, we can interface sensors to the hardware development kits like ESP32, ESP8266, Raspberry Pi, Particleboards( Aargon, Boron, Xenon) and post data to the clouds like Thingspeak, Ubidots, AWS_IoT_Core, Microsoft Azure.

Amazon is not only in e-commerce but also focusing on IoT and providing cloud-based service named as AWS IoT.
Here, AWS IOT stands for Amazon Web Service Internet of Things. This service allows us to connect our devices to the internet for processing, operating and exchanging data securely.
Along with AWS IoT, the Amazon Web Services also provides tons of other features like virtual machine deployment, web-hosting, etc.

* What Is AWS IoT?

AWS_IoT provides secure, bi-directional communication between internet-connected devices such as sensors, actuators, embedded microcontrollers, or smart appliances and the AWS Cloud.
This makes it possible for you to collect telemetry data from multiple devices, and store and analyze the data.
You can also create applications that enable your users to control these devices from their phones or tablets.

* What is Thing/ Device (in the Internet of Things)?

A thing, in the context of the Internet of things (IoT), is an entity or physical object that has a unique identifier, an embedded system and the ability to transfer data over a network.

* What is AWS IoT Certificate?

A device must have a certificate to authenticate with AWS_IoT. X.509 certificates are used to authenticate the device,This certificate represents that the particular thing belongs to your  AWS Account. This certificate will help AWS to authenticate while your device trying to communicate with it.

There are two main methods for encoding certificate data.

    DER = Binary encoding for certificate data
    PEM = The base64 encoding of the DER-encoded certificate, with a header and footer lines added.

DER

DER: (Distinguished Encoding Rules) is a subset of BER encoding providing for exactly one way to encode an ASN.1 value. DER is intended for situations when a unique encoding is needed, such as in cryptography, and ensures that a data structure that needs to be digitally signed produces a unique serialized representation.
PEM

PEM: (Privacy-enhanced Electronic Mail) Simply a US-ASCII by base64 encoded DER certificate, certificate request, or PKCS#7, enclosed between typical PEM delimiters. ie “—–BEGIN CERTIFICATE—–” and “—–END CERTIFICATE—–“. PEM is an abbreviation for Privacy Enhanced Mail (RFC 1421 – RFC 1424), an early standard for securing electronic mail (IRTF, IETF). PEM never has been widely adopted as Internet Mail Standard but has become a staple standard in x509 pki (also called pkix)

* What is the policy?

AWS_IoTpolicies are used to authorize your device to perform AWS_IoT operations, such as subscribing or publishing to MQTT topics. Your device presents its certificate when sending messages to AWS IoT. To allow your device to perform AWS IoT operations, you must create an AWS IoT policy and attach it to your device certificate.

Hopefully, you have understood the basic concepts of AWS IoT Core, let’s move to the next step.

3. Steps involved in this:
        
    i)   Creating thing, certificate and attaching a policy to the certificate
    ii)  Installing Required SDKs, and Libraries. such as “AWS IoT Python SDK” & Paho-MQTT library
    iii) Programming Part – Creating scripts for Publishing, Subscribing to a particular thing.
    iv)  Execution of Scripts & Demonstration of Data logging
    v)   Creating DynamoDB Rule & DynamoDB Table.
    vi)  Execution of Scripts & Demonstration of pushing data into the DynamoDB

i) Creating thing, certificate and attaching a policy to the certificate

        Check the following tutorial for step by step Explanation: How to create a thing in AWS IoT Core, its Certificates & policies

        Setting up the AWS environment for these devices is pretty simple.
        Check the following: Amazon AWS and login to the AWS Management Console & search for IoT core in the Amazon Services, find services search bar will help you in this regard.
        After getting into the IoT Core section, tap on the tab called “Manage” from the AWS IoT menu which is on the left side, tap on the register thing button if you haven’t added any devices till now.
        If you have previously added things just tap on the button named “Create” which is on the top right corner beside the iot-notifications Icon.
        
