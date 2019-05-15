# Vscode Arduino Example

> This is an example file with default selections.

## Install

Open VS Code and press F1 or Ctrl + Shift + P to open command palette, select Install Extension and type `vscode-arduino`.

Or launch VS Code Quick Open (Ctrl + P), paste the following command, and press enter.

```vscode
ext install vscode-arduino
```

You can also install directly from the Marketplace within Visual Studio Code, searching for Arduino.

You should also install C/C++ from the Marketplace.

## Setup

Create a new folder and open it in VS Code.

Press Ctrl + Shift + P to open command palette and enter the command `Arduino: Initialize` and press enter to create the sample `app.ino` file.

This will create folders/files like this:

```bash
.
├── .vscode
│   ├── arduino.json
│   └── ipch
│       └── <misc things not mess with>
└── app.ino
```

Now that's add some basic code to `app.ino`.

```arduino
void setup()
{
    pinMode(LED_BUILTIN, OUTPUT);
    Serial.begin(9600);
}

void loop()
{
    digitalWrite(LED_BUILTIN, HIGH);
    Serial.println("ON");
    delay(1000);
    digitalWrite(LED_BUILTIN, LOW);
    Serial.println("OFF");
    delay(1000);
}
```

Wow there, that's a lot of red sqiggles! Our C/C++ IntelliSense (code checker) extension is telling us that there are problems with our code. This is because the extension doesn't know where to find our Arduino libraries.

### Creating JSON settings

Make a new file named `c_cpp_properties.json` in your `.vscode` folder and paste this into it:

```json
{
    "configurations": [
        {
            "name": "Win32",
            "includePath": [
                "C:\\Program Files (x86)\\Arduino\\tools\\**",
                "C:\\Program Files (x86)\\Arduino\\hardware\\arduino\\avr\\**",
                "C:\\Program Files (x86)\\Arduino\\hardware\\tools\\**",
                "C:\\Program Files (x86)\\Arduino\\hardware\\tools\\avr\\avr\\include\\**",
                "C:\\Users\\timmi\\Documents\\Arduino\\libraries\\**"
            ],
            "forcedInclude": [
                "C:\\Program Files (x86)\\Arduino\\hardware\\arduino\\avr\\cores\\arduino\\Arduino.h"
            ],
            "defines": [
                "UBRRH"
            ],
            "intelliSenseMode": "msvc-x64",
            "cStandard": "c11",
            "cppStandard": "c++17"
        }
    ],
    "version": 4
}
```

Let's check out our `app.ino` file. Excellent! No more red squiggles. 

Finally, Make a new file named `settings.json` in your `.vscode` folder and paste this into it:

```json
{
    "arduino.path": "C:/Program Files (x86)/Arduino",
    "arduino.commandPath": "arduino_debug.exe",
    "arduino.logLevel": "info",
    "arduino.enableUSBDetection": true,
    "arduino.disableTestingOpen": false,
    "arduino.skipHeaderProvider": false,
    "arduino.additionalUrls": [
        "https://dl.espressif.com/dl/package_esp32_index.json"
    ],//Along with any other additional paboard packages you may need
    "arduino.defaultBaudRate": 9600
}
```

### Configuring Arduino JSON

Plug your arduino into your computer. Look on the blue tool bar at the bottom of VS Code. You should see some clickable button named `<Select Programmer>`, `<Select Board Type>`, `<Select Serial Port>`. Click on each and select `AVRISP mkII`, `Arduino/Genuino Uno`, and whatever COM port your port is plugged into respectively. *If you feel like peering under the hood just a little: open `.vscode/arduino.json` and mess around the Programmer, Board Type, and COM port settings*.

Open your `arduino.json` file and add the key output and set it to a folder `build` in your projects root. For example, my project is named `Arduino_projects` and my `arduino.json` file looks like this:

```json
{
    "sketch": "app.ino",
    "programmer": "AVRISP mkII",
    "board": "arduino:avr:uno",
    "port": "COM20",
    "output": "../Arduino_projects/build/"
}
```

### Git ignore

**This only applies if you plan on tracking your repo.**

Make to ignore that ipch folder and your build folder. Make a new file called `.gitignore` in the root of your project and add this:

```gitignore
ipch
build
```

## Usage

### General

Use Ctrl + Alt + R to verify your code and Ctrl + Alt + U to upload it.

Use the plug icon next to the COM port to open the serial monitor. To write to the serial monitor use the command `Arduino: Send Text to Serial Port` in the command palette.

### Other Commands

To enter the command palette type Ctrl + Shift + P

| Command                           | Description
| ---                               | ---
| `Arduino: Board Manager`            | Manage packages for boards. You can add 3rd party Arduino board by configuring Additional Board Manager URLs in the board manager.
| `Arduino: Change Baud Rate`         | Change the baud rate of the selected serial port.
| `Arduino: Change Board Type`        | Change board type or platform.
| `Arduino: Close Serial Monitor`     | Stop the serial monitor and release the serial port.
| `Arduino: Examples`                 | Show list of examples.
| `Arduino: Initialize`               | Scaffold a VS Code project with an Arduino sketch.
| `Arduino: Library Manager`          | Explore and manage libraries.
| `Arduino: Open Serial Monitor`      | Open the serial monitor in the integrated output window.
| `Arduino: Select Serial Port`       | Change the current serial port.
| `Arduino: Send Text to Serial Port` | Send a line of text via the current serial port.
| `Arduino: Upload`                   | Build sketch and upload to Arduino board.
| `Arduino: Upload Using Programmer`  | Upload using an external programmer.
| `Arduino: Verify`                   | Build sketch.

## Contributing

PRs accepted.

## License

MIT © Richard McRichface
