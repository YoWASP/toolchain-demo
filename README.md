# Demonstration of the [YoWASP toolchain](https://yowasp.org/) and [its VS Code extension](https://marketplace.visualstudio.com/items?itemName=yowasp.toolchain)

## Getting started

You can run this demonstration either with or without hardware. The design is built for the [Radiona ULX3S](https://radiona.org/ulx3s/) board, and bitstream upload only works on [WebUSB-enabled browsers](https://caniuse.com/webusb) (and not on the desktop VS Code at the moment). If these requirements are not met, the board programming will fail, but every step before that will still complete.

1. Open this repository in Visual Studio Code. If you have a GitHub account, you can open it [directly via vscode.dev](https://vscode.dev/github/YoWASP/toolchain-demo); otherwise, use any
2. Install the [YoWASP VS Code extension](https://marketplace.visualstudio.com/items?itemName=yowasp.toolchain) (there will be a prompt to do so in the lower right corner; click "Install").
3. **(Only when using hardware)** Plug your FPGA evaluation board into a USB port.
4. Press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (or open menu "View" → "Command Palette...") and navigate to "YoWASP Toolchain: Build..." by typing the first letters of each word. Press <kbd>Enter</kbd>.
5. A terminal will open at the bottom of the window and show the progress of the build process. It may take a few minutes to complete for the first time, and at times there may be no progress indication. This is normal; running the toolchain for the first time requires downloading about 100 MB of code and data, which will be cached afterwards in the browser.
6. **(Only when using hardware)** A prompt to use a USB device will appear in the lower right corner; click "Connect Device", pick the line starting with "ULX3S FPGA" in the panel that opens, and click "Connect" in that panel.
7. **(Only when using hardware)** The terminal will now show the progress of the bitstream loading process. This should only take a few seconds, and when complete, the board will start blinking a LED at 1 Hz.
8. That's it! Now that your environment is verified to work, you can fork this repository and play with the demo design.

## Customizing the demo

This demonstration is made for the Radiona ULX3S board, but it could be used with any Lattice iCE40, ECP5, MachXO2, MachXO3, or Nexus FPGAs; see also the [openFPGALoader board compatibility list](https://trabucayre.github.io/openFPGALoader/compatibility/board.html). The build process is configured in the `.vscode/settings.json` file, and will need to be adjusted for your particular FPGA and board.
