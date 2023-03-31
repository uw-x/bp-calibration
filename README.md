# A low-power wearable acoustic device for accurate invasive arterial pressure monitoring

## Abstract
Millions of catheters for invasive arterial pressure monitoring are placed annually in intensive care units, emergency rooms, and operating rooms to guide medical treatment decision-making. Accurate assessment of arterial blood pressure requires an IV pole-attached pressure transducer placed at the same height as a reference point on the patient’s body, typically, the heart. Every time a patient moves, or the bed is adjusted, a nurse or physician must adjust the height of the pressure transducer. There are no alarms to indicate a discrepancy between the patient and transducer height, leading to inaccurate blood pressure measurements.

We present a low-power wireless wearable tracking device that uses inaudible acoustic signals emitted from a speaker array to automatically compute height changes and correct the mean arterial blood pressure. Performance of this device was tested in 26 patients with arterial lines in place by moving the height of the bed over a 45 cm height range.

## Setup
1. Download nRF SDK
-  Go to https://www.nordicsemi.com/Software-and-Tools/Software/nRF5-SDK/Download#infotabs
-  Download the latest SDK
-  Unzip the .zip to a high level directory (e.g. C:\ on Windows, or home directory on linux/mac)
2. Install toolchains
-  Install gcc-arm-none-eabi using 'brew install gcc-arm-none-eabi'. If using a Linux environment, please refer to this link for help with installation: https://askubuntu.com/questions/1243252/how-to-install-arm-none-eabi-gdb-on-ubuntu-20-04-lts-focal-fossa. Full details for installing toolchains for the Nordic family of chipsets can be found here: https://www.nordicsemi.com/Products/Development-tools/Segger-Embedded-Studio/Download?lang=en#infotabs.
-  Update GNU_INSTALL_ROOT (path of your gcc) inside Makefile.posix (located at SDK/components/toolchain/gcc/) of the unzipped SDK. If you installed using brew, the path should be `/usr/local/Cellar/gcc-arm-none-eabi/20180627/bin/`
-  Install nordic command line tools from here: https://www.nordicsemi.com/Software-and-tools/Development-Tools/nRF-Command-Line-Tools/Download. Unzip, and move the nrfjprog directory to /usr/local/. Finally, add this to your PATH inside `.bash_profile` with this change: `export PATH=/usr/local/bin:/usr/local/sbin:/usr/local/nrfjprog:$PATH`
-  Validate that this worked by opening a new terminal and typing `nrfjprog --version` as a sanity check
3. Clone the repo
-  Clone anywhere, and overwrite this repo's `SDK/modules/nrfx/drivers/src/nrfx_pdm.c` file over the stock version of the file provided by the nRF SDK.
- Once overwritten, copy over the entire SDK directory into this repository
4. Build and flash
-  Run `make flash` in terminal to build and flash

If you have any trouble installing, feel free to reach out, more details for setting up on a mac can be found here: https://aaroneiche.com/2016/06/01/programming-an-nrf52-on-a-mac/

## Code organization
The root directory of this repository contains software for the wearable acoustic device. The receiver software lives in the `udon/` directory. Programming the receiver is identical to the wearable device and can be done via `make flash`.

## License
This project is under the GNU General Public License v3.0. See the COPYING file for the full license text.
