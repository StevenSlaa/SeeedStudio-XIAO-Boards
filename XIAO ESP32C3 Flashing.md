# Flashing the XIAO ESP32C3 board

This tutorial is writtin because I have encoutered issues with uploading to the board. Out of the box I had to hold down the boot button before plugging the board in to actually be able to upload code to the board. After this I also had to press the enable button to actually execute the code. 

## 1. Connecting the XIAO ESP32C3 to the computer

Before connecting it to the computer. Please **hold down the boot button and plugin the cable** to the computer. Everything should be working as expected.

> If you get an error message that the device is not recognized, you probably didn't hold down the boot  button correctly before plugging it in to the computer.

## 2. Downloading and opening the [ESPRFTestTool](https://www.espressif.com/sites/default/files/tools/ESP_RF_Test_EN.zip)

From this link it will download a `.zip` file. Extract this file and navigate to the following directory: `\ESP_RF_Test_EN\EspRFTestTool_v2.8_Manual`. In here you will find an executable that is called:
`EspRFTestTool_v2.8_Manual`.
![Flash Tool Directory](https://user-images.githubusercontent.com/47790980/208499719-70f1229e-f99a-4dd0-b8a1-dc704d253bd5.png)

When you have located the executable, you can open it.

## 3. Flashing the board

When the executable is open, you can configure the tool with the following settings:

- Chiptype: **ESP32C3**
- COM: **[*Your COM-port*]**
- BaudRate: **115200**

After this, you can click on the `open` button. Beneath these options, configure the settings as follows:

- **Change RAM to Flash**
- Click on the `Select Bin` button and select the following file: **\ESP_RF_Test_EN\EspRFTestTool_v2.8_Manual\Bin\RF_TEST_BIN\ESP32-C3_RFTest_108_2b9b157_20211014.bin**.

When everything is configured correctly, you should be seeing something like this:
![Flash settings overview](https://user-images.githubusercontent.com/47790980/208499722-c81c60d9-ebd8-495d-9db2-21863746d1e1.png)

After this your ready to click the `Load Bin` button and start flashing your board. After this is complete your ready to go to the next step and see something like this:

![Flash Success](https://user-images.githubusercontent.com/47790980/208499724-1cf30a42-263d-45e5-87b4-2dd47639998d.png)

Now you can close the port by clicking on the `close` button in the top right corner.

## 4. Uploading code to the board.

Maybe you've noticed that up until this point it has pretty much been following [the guide from the manufacturer](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/#q3-i-want-to-reflash-the-bootloader-with-factory-firmware). Unplug your XIAO ESP32C3 and plug it back in (without holding down the boot button). You will notice that the board is not recognized by the computer. To fix this, unplug your board, (for the last time :wink:) hold down the boot button and plug it back in. Now the message disappears. To make this permanently, open up the Arduino IDE (in my case version 2.0.3) and [install the board](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/#getting-started). 

> In my case ESP32 board collection (in the board manager) is at version 2.0.5

Do the following things:

- Create a blank sketch.
- Select the correct board and port (`XIAO_ESP32C3`) with the following properties (I believe these are all default):
  USB CDC On Boot: **Enabled**
  CPU Frequency: **160 MHz (WiFi)**
  Core Debug Level: **None**
  Erase all Flash Before Sketch Upload: **Disabled**
  Flash Frequency: **80MHz**
  Flash Mode: **QIO**
  Flash Size: **4MB (32Mb)**
  Partition Scheme: **Default 4MB with spiffs (1.2MB APP/1.5MB SPIFFS)**
  Upload Speed: **921600**
- Click on the upload button. This should work just fine because you've held the boot button down on startup.

However now unplug your board and (without holding down the boot button) plug it back in. Now the error of that the device is not recognized should not appear. In fact you should now be able to reupload the blank sketch and thus fixing the issue.

### Notes

- These steps has been tested with a USB-C to USB-C cable to a computer with a length of 0.25 Meters (~10'')
- External antenna does not have to be connected.

## FAQ

### I am still having the same issues after following the steps

If you still encouter the same issues after following the steps. You can try redoing step 3, but this time do not hold the boot button pressed when plugging the board in. If this is done, redo step 3, but with holding down the boot button and then continue with step 4. (At first I had this issue aswell, but doing this fixed the issue for me).

### My board is not recognized by my computer

When this is occuring at the steps mentioned, this is correct behaviour. If not, then try holding down the boot button while plugging it in. If this doesn't work, you can try a different/ shorter cable. If this doesn't work you could encouter some driver issues. Try using a different computer verify if this is the issue.



If you have anyother issues, please create an issue so we can fix this together.


