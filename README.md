


<h1 align = "center"> 🌟T-HMI🌟</h1>

<p align="center">
  <a href="https://www.youtube.com/@Fusion_Automate"><img src="https://img.shields.io/badge/YouTube-FusionAutomate-%23FF0000?style=for-the-badge&logo=youtube" alt="YouTube"></a>
  <a href="https://www.instagram.com/fusion_automate"><img src="https://img.shields.io/badge/Instagram-fusion__automate-%23E4405F?style=for-the-badge&logo=instagram" alt="Instagram"></a>
  <a href="https://x.com/fusion_automate"><img src="https://img.shields.io/badge/X-fusion__automate-000000?style=for-the-badge&logo=x" alt="X (Twitter)"></a>
  <a href="https://t.me/fusionautomate"><img src="https://img.shields.io/badge/Telegram-%40fusionautomate-%2326A5E4?style=for-the-badge&logo=telegram" alt="Telegram"></a>
  <a href="https://wa.me/919974477759"><img src="https://img.shields.io/badge/WhatsApp-%2B91_99744_77759-%2325D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhatsApp"></a>
  <a href="mailto:eng.innovativ@gmail.com"><img src="https://img.shields.io/badge/Email-eng.innovativ%40gmail.com-c71610?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"></a>
  <a href="https://fusionautomate.in/"><img src="https://img.shields.io/badge/Website-fusionautomate.in-blueviolet?style=for-the-badge" alt="Website"></a>
</p>


## Pinout

![image](./image/T-HMI.jpg)



## Quick Start

The board uses USB as the JTAG upload port. When printing serial port information on USB, CDC_ON_BOOT configuration needs to be turned on. 
If the port cannot be found when uploading the program or the USB has been used for other functions, the port does not appear. 
Please enter the upload mode manually. 
-  Press and hold the BOOT button when the power is off, the button is located behind the RST button.
-  When the USB is connected, first press and hold the BOOT button, then click reset and then release the BOOT button

### Arduino

* [Record Video](https://youtu.be/4tYiujotmKI)

1. In Arduino Preferences, on the Settings tab, enter the `https://espressif.github.io/arduino-esp32/package_esp32_index.json` URL in the `Additional boards manager URLs` input box. 
2. Click OK and the software will install. 
3. Search for ESP32 in Tools → Board Manager and install ESP32-Arduino SDK (V 2.0.5 or above and below V3.0)
![](image/Arduino_board.png)
4. Copy everything from this repository lib folder to [Arduino library folder](https://docs.arduino.cc/software/ide-v1/tutorials/installing-libraries#manual-installation) (e.g. `C:\Users\YourName\Documents\Arduino\libraries`)
5. Select the correct settings in the Tools menu as shown below.

| Setting                  | Value                            |
| :----------------------- | :------------------------------- |
| Board                    | ESP32 S3 Dev Module              |
| USB CDC On Boot          | Enabled                          |
| CPU Frequency            | 240MHz (WiFi)                    |
| Core Debug Level         | None                             |
| USB DFU On Boot          | Enabled                          |
| Events Run On            | Core 1                           |
| Flash Mode               | QIO 80MHz                        |
| Flash Size               | 16MB (128Mb)                     |
| JTAG Adapter             | Integrated USB JTAG              |
| Arduino Runs On          | Core 1                           |
| USB Firmware MSC On Boot | Disabled                         |
| Partition Scheme         | Huge APP (3MB No OTA/1MB SPIFFS) |
| PSRAM                    | OPI PSRAM                        |
| USB Mode                 | Hardware CDC and JTAG            |

##### Writing as a beginner: 

- When opening the Arduino IDE, you will be prompted that there are new libraries that can be updated. Please do not click update. There is no guarantee that it can be compiled, run, etc. after the update. Make sure that the board is running normally before deciding whether to update. You have to Know that problems may occur after updating due to library differences, or the default configuration (such as TFT_eSPI) will be overwritten.
- If it runs abnormally after the update, please follow Article 4 of the Arduino Quick Start to delete the directory in libraries, and drag the folder in lib into the libraries directory again.

### PlatformIO

1. PlatformIO plug-in installation: click on the extension on the left column → search platformIO → install the first plug-in
2. Click Platforms → Embedded → search Espressif 32 in the input box → select the corresponding firmware installation

## Tips

1. The board uses USB as the JTAG upload port. When printing serial port information on USB_CDC_ON_BOOT configuration needs to be turned on.
If the port cannot be found when uploading the program or the USB has been used for other functions, the port does not appear.
Please enter the upload mode manually.
   1. Connect the board via the USB cable
   2. Press and hold the BOOT button , While still pressing the BOOT button, press RST
   3. Release the RST
   4. Release the BOOT button
   5. Upload sketch
2. If the above is invalid, burn the [firmware](./firmware/README.MD)  to check whether the hardware is normal
3. Powering up the T-HMI board via the 5V DC connector does not work
   - Looking at the [schematic](./schematic/Schematic.pdf), we know that if you use an external 5V power supply, you need to bring a magnet close to the ReedSwitch and set the PowerOn Pin (GPIO14) to HIGH as soon as the chip starts.
   ```c
    pinMode(14, OUTPUT);
    digitalWrite(14, HIGH);
    ```
4. It can start normally when using USB power supply, but it cannot start when connected to the battery alone?
   - When using the battery alone, IO10 needs to be set to HIGH to work properly.
    ```c
    pinMode(10, OUTPUT);
    digitalWrite(10, HIGH);
    ```
5. How to turn the machine on and off with a switch and how many ways are there? See [here](https://github.com/Xinyuan-LilyGO/T-HMI/tree/master/examples/power_on)
---

<div align="center">

✨ **Enjoying these lessons? Support our work!** ✨

<a href="https://buymeacoffee.com/pylin" target="_blank">
  <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me a Coffee" height="40">
</a>

<a href="https://www.youtube.com/channel/UCKKhdFV0q8CV5vWUDfiDfTw" target="_blank">
  <img src="assets/youtube-subscribe.png" alt="Subscribe on YouTube" height="40">
</a>

</div>
