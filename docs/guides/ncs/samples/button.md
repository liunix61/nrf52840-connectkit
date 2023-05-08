# Button

## Overview

A simple button sample demonstrates the use of GPIO input with interrupts. The sample prints a message to the console each time a button is pressed.

## Requirements

Before you start, check that you have the required hardware and software:

- 1x [nRF52840 Connect Kit](https://makerdiary.com/products/nrf52840-connectkit)
- 1x USB-C Cable
- A computer running macOS, Linux, or Windows 7 or newer

## Building the sample

Before you start building, remember to [set up the environment](../setup.md) first.

Use the following steps to build the [Button] sample on the command line.

1. Open a terminal window.

2. Go to `my-workspace/ncs-playground` directory created in the [Setting up the environment](../setup.md#get-the-code) section.

    ``` bash linenums="1"
    cd my-workspace/ncs-playground
    ```

3. Build the sample using the `west` command, specifying the board (following the `-b` option) as `connectkit_nrf52840`:

    ``` bash linenums="1"
    west build -p always -b connectkit_nrf52840 samples/button
    ```

    !!! Tip
        The `-p always` option forces a pristine build, and is recommended for new users. Users may also use the `-p auto` option, which will use heuristics to determine if a pristine build is required, such as when building another sample.

4. After running the `west build` command, the build files can be found in `build/zephyr`. 

## Flashing the firmware

The sample is designed to work with the UF2 Bootloader, so that you can easily flash the sample [using the UF2 Bootloader](../../../programming/uf2boot.md). The firmware can be found in `build/zephyr` with the name `zephyr.uf2`.

To flash the firmware, complete the following steps:

1. Push and hold the __USER__ button and plug your board into the USB port of your computer. Release the __USER__ button after your board is connected. The RGB LED turns green.

2. It will mount as a Mass Storage Device called __UF2BOOT__.

3. Drag and drop `zephyr.uf2` onto the __UF2BOOT__ volume. The RGB LED blinks red fast during flashing.

4. Reset the board and the sample will start running.

## Testing

After flashing the firmware to your board, complete the following steps to test it:

1. Connect nRF52840 Connect Kit to your computer using the USB-C Cable.
2. Open up a serial terminal, specifying the correct serial port that your computer uses to communicate with the board:

    === "macOS/Linux"

        Open up a terminal and run:

        ``` bash linenums="1"
        screen <serial-port-name> 115200
        ```

    === "Windows"

        1. Start [PuTTY].
        2. Configure the correct serial port and click __Open__:

            ![](../../../assets/images/putty-settings.png)

3. Observe the output of the terminal and press the __USER__ button. You should see the output, similar to what is shown in the following:

    ``` { .bash .no-copy linenums="1" }
    Set up button at GPIO_1 pin 0
    Set up LED at GPIO_1 pin 15
    Press the button
    Button pressed at 281102
    Button pressed at 310379
    Button pressed at 341776
    ...
    ```

[Button]: https://github.com/makerdiary/ncs-playground/tree/main/samples/button
[PuTTY]: https://apps.microsoft.com/store/detail/putty/XPFNZKSKLBP7RJ
