# Connecting MKR1000 WiFi to Azure IoT Hub with DHT22

## Arduino
use the above .ino file as base line to send messages. Create arduino_secrets.h file to store the links to your enviornment. 

The authenitcation against the Azure IoT Hub goes with a self signed certificate. We need to create this via Arduino for every MKR1000 device Open the sketch in the Arduino IDE using the File -> Examples -> ArduinoECCX08 -> Tools -> ECCX08SelfSignedCert. Click the "Upload".

Open the terminal screen and click Y on the first question. After that you need to create an own device. Put there the date etc of today. We use the slot 0 for storing the certificate on the device. Click yes to generate the private key. Save the SHA output. 

## Azure IoT Hub
Create a new IoT device in the IoT Hub, when creating the new devive don't use the SAS authentication, but the self signed certificate authentication. Paste the SHA key from the previous step into the primary and secondary key.

## Run
Run the code on Arduino with the device ID you have created in the secrets file. Check with your serial port if the data is send to the IoT Hub. If yes, check with Azure IoT Explorer if the data is received in the IoT Hub.
