[![FAP Build](https://github.com/0xchocolate/flipperzero-esp-esp/actions/workflows/build.yml/badge.svg)](https://github.com/0xchocolate/flipperzero-esp-esp/actions/workflows/build.yml)

# Esp Esp companion app for Flipper Zero

Requires a connected dev board running Esp FW. [See install instructions from UberGuidoZ here.](https://github.com/UberGuidoZ/Flipper/tree/main/Esp_DevBoard#esp-install-information)

## Get the app
1. Make sure you're logged in with a github account (otherwise the downloads in step 2 won't work)
2. Navigate to the [FAP Build](https://github.com/0xchocolate/flipperzero-esp-esp/actions/workflows/build.yml)
   GitHub action workflow, and select the most recent run, scroll down to artifacts.
3. The FAP is built for the `dev` and `release` channels of both official and unleashed
   firmware. Download the artifact corresponding to your firmware version.
4. (Optional step to avoid confusion) Go to "Apps/GPIO" on the Flipper SD Card, delete any existing Esp app, on some firmwares there will be a `ESP32CAM_Esp.fap` or similar.
5. Extract `esp32_esp_flasher.fap` from the ZIP file downloaded in step 3 to your Flipper Zero SD card, preferably under Apps/GPIO along with the rest of the GPIO apps. (If you're using qFlipper to transfer files you need to extract the content of the ZIP file to your computer before you drag it to qFlipper, as qFlipper does not support direct dragging from a ZIP file (at least on Windows)).

From a local clone of this repo, you can also build the app yourself using ufbt.

## In-app ESP32 flasher (WIP)
Guide by [@francis2054](https://github.com/francis2054)

The app now contains a work-in-progress of an ESP32 flasher (close to the bottom of the esp menu). Use at your own risk. This hardcodes addresses for non-S3 ESP32 chips.

To use this method:
1. Make sure you follow the instructions for how to get the Esp app on your Flipper Zero, they can be found on the top of this page. Latest release needs to be downloaded and installed.
2. Go to [Justcallmekoko's firmware page](https://github.com/justcallmekoko/ESP32Esp/wiki/update-firmware#using-spacehuhn-web-updater) and download all files necessary for the board you are flashing, most boards will want all 4 files but for the Esp Devboard you want to download these 3 files: `0x1000` (Bootloader), `0x8000` (partitions), `0x10000` (Firmware). The `Boot App` is not needed for the Esp Devboard with this method. The Firmware one will redirect you to the releases page where you'll need to pick the one relevant to the board you're flashing, if you are using the official Wi-Fi Devboard you want to pick the one ending in `_flipper_sd_serial.bin`. 
3. Place all files downloaded in step 2 in a new folder on your desktop, the name does not matter. Rename the `_flipper_sd_serial.bin` file you downloaded in step 2 to `Firmware.bin`.
4. Now for transferring the files to the Flipper Zero, drag all the files from the folder on your desktop to the "Esp" folder inside "apps_data" folder on the Flipper Zero SD card. Preferred method to transfer these files is plugging the SD card into your computer with an adapter, but qFlipper works as well. Insert the Flipper Zero SD Card back into the Flipper before proceeding to the next step.
5. Plug your Wi-Fi Devboard into the Flipper.
6. Press and keep holding the boot button while you press the reset button once, release the boot button after 2 seconds.
7. Open the Esp app on your Flipper Zero, it should be named "esp32_esp_flasher" and be located under Apps->GPIO from the main menu if you followed the instructions for how to install the app further up on this page. (You might get an API mismatch error if the Flipper firmware you are running doesn't match the files you've downloaded, you can try "Continue" anyway, otherwise the app needs to be rebuilt or you might need to update the firmware on your Flipper).
8. Press the up arrow on the Flipper three times to get to "Reflash ESP32 (WIP)" and open it.
9. For "Bootloader" scroll down in the list and select `esp32_esp.ino.bootloader.bin`, for "Paritition table" select `esp32_esp.ino.partitions.bin` and for "Firmware" select `Firmware.bin`.
10. Scroll down and click "[>] FLASH" and wait for it to complete. (If you get errors here, press back button once and repeat step 6 then try "[>] FLASH" again).
11. Once it says "Done flashing" on the screen, restart the Flipper and you are done :)

## For future updates, just repeat from step 2 and only download the new "Firmware" bin

This process will improve with future updates! :)

## Support

For app feedback, bugs, and feature requests, please [create an issue here](https://github.com/0xchocolate/flipperzero-firmware-with-esp-esp-companion/issues).

You can find me (0xchocolate) on discord as @cococode#6011.

If you'd like to donate to the app development effort:  
**ETH**: `0xf32A1F0CD6122C97d8953183E53cB889cc087C9b`  
**BTC**: `bc1qtw7s25cwdkuaups22yna8sttfxn0usm2f35wc3`

Find more info about Esp and support its developer (justcallmekoko aka WillStunForFood) here: https://github.com/justcallmekoko/ESP32Esp

If you found the app preinstalled in a firmware release, consider supporting the maintainers!