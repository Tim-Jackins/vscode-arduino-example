# Vscode Arduino Example

> What a cool IDE!

The most important part to be noted is the `includePath` variable in the [./.vscode/c_cpp_properties.json](./.vscode/c_cpp_properties.json) file. In order to allow Microsofts C/C++ extension not throw bogus errors you need the following paths included:

```json
"includePath": [
    "C:\\Program Files (x86)\\Arduino\\tools\\**",
    "C:\\Program Files (x86)\\Arduino\\hardware\\arduino\\avr\\**",
    "C:\\Program Files (x86)\\Arduino\\hardware\\tools\\**",
    "C:\\Program Files (x86)\\Arduino\\hardware\\tools\\avr\\avr\\include\\**",
    "C:\\Users\\timmi\\Documents\\Arduino\\libraries\\**"
],
```

This needs more paths or ignores to be good. To verify use `Ctrl + Alt + R` to upload use `Ctrl + Alt + U`. Here are some other useful commands:

* Arduino: Board Manager: Manage packages for boards. You can add 3rd party Arduino board by configuring Additional Board Manager URLs in the board manager.
* Arduino: Change Baud Rate: Change the baud rate of the selected serial port.
* Arduino: Change Board Type: Change board type or platform.
* Arduino: Close Serial Monitor: Stop the serial monitor and release the serial port.
* Arduino: Examples: Show list of examples.
* Arduino: Initialize: Scaffold a VS Code project with an Arduino sketch.
* Arduino: Library Manager: Explore and manage libraries.
* Arduino: Open Serial Monitor: Open the serial monitor in the integrated output window.
* Arduino: Select Serial Port: Change the current serial port.
* Arduino: Send Text to Serial Port: Send a line of text via the current serial port.
* Arduino: Upload: Build sketch and upload to Arduino board.
* Arduino: Upload Using Programmer: Upload using an external programmer.
* Arduino: Verify: Build sketch.

More info can be found [here](https://marketplace.visualstudio.com/items?itemName=vsciot-vscode.vscode-arduino).
