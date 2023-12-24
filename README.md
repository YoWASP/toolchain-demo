Install the [YoWASP VS Code extension](https://marketplace.visualstudio.com/items?itemName=yowasp.toolchain), then run the "YoWASP Toolchain: Build..." command for those unfamiliar with visual studio code pressing `Ctrl + Shift + P` and then typing `YoWASP` until you see an option is how you do that. There is also a "YoWASP Toolchain: Connect to USB Device..." command which can but useful to see whether your USB device is detected without rebuilding things.


# This is the first time i am using Yosys for this board (in a while)
The repository is currently configured for the [ulx3s](https://radiona.org/ulx3s/) board. Modify `.vscode/settings.json` to suit your model. Here are some useful resources:

- [List of supported openFPGALoader boards](https://trabucayre.github.io/openFPGALoader/compatibility/board.html)
- [The YoWASP website has a "How do I use the tools" section which can give you an idea what packages you might want to look into](https://yowasp.org/)
- Make files of Yosys projects for your target. These obviously are different for your target but can give you good idea what flags you might need to use
- For a board from a different family of FPGA, you probably need to change these lines:
  - `"@yowasp/nextpnr-ecp5",` needs to be changes to reflect your FPGA type.
  - `["yosys", "top.v", "-o", "top.json", "-p", "synth_ecp5"],` needs to reflect your FPGA type.
  - `["nextpnr-ecp5", "--85k", "--package", "CABGA381", "--json", "top.json", "--lpf", "top.lpf", "--textcfg", "top.config"],` needs to be changed to reflect your board type and use the right compiler for your FPGA. `top.lpf` tells nextpnr how your program accesses certain hardware and differs per board. A `.asc` file can could also work.
  - `["ecppack", "--compress", "top.config", "top.bit"],` needs to reflect your FPGAs type. Different FPGA types have differen packers.
  - `["openFPGALoader", "-b", "ulx3s", "-m", "top.bit"]` needs to reflect your board type. The `--verify` option can be useful when debugging

# Make the project yours
The repo contains a demo which makes lights blink on the targeted board. You could modify it to make mutliple LEDs of your board blink or turn an LED on and off quickly to make the LED dimmer. Convince yourself that you actually control what happens on your board. This can be empowering.