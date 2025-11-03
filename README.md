# soarerConverter
<img src="https://github.com/bipknit/soarerConverter/blob/main/src/model_fbs_con.png?raw=true" alt="Model FBS Converter" width="400"/>

A tutorial for how to converting certain IBM keyboard protocol to standard USB
I made a lot of these converters in the past year so I decided to make a tutorial.

# Why the IBM Model M compared to new keyboards?
## 1. The Model M (introduced in 1985) was built like a tank:
- Steel backplate: gives it substantial weight (often 2+ kg) and zero flex.
- Thick ABS or PBT keycaps: double-shot or dye-sublimated legends that never fade.
- Modular design: easily repairable — you can open it, clean it, and replace parts.
https://github.com/bipknit/soarerConverter/blob/main/src/buckling-spring-working-switch.gif
## 2. Buckling Spring Mechanism

<img src="https://github.com/bipknit/soarerConverter/blob/main/src/buckling-spring-working-switch.gif" alt="buckling spring" width="400"/>


This is the defining feature of the Model M.
How it works:

    Each key has a coil spring that compresses when pressed.

    At a certain point, the spring buckles, snapping sideways.

    That snap actuates a membrane switch underneath and provides a sharp tactile and audible “click.”

Why it feels so good:

    The tactile feedback is precise and consistent.

    The click is mechanically generated — not from a simple click jacket like in Cherry MX Blues.

    The actuation point is highly predictable; your fingers “learn” exactly when a key activates.

Many typists find it more satisfying and accurate than most modern switches.

## 3. The Sound

The Model M’s click isn’t just loud — it’s rich and tonal.
It sounds mechanical in the purest sense, almost like a typewriter, and provides strong aural feedback that reinforces the tactile feel.
*(Though it’s not office-friendly — it’s very loud!)*


# Step 1: Gathering the model number and certain info
Gather info about yout model M from the database by typing the part number on the back of your keyboard.

https://sharktastica.co.uk/keyboard-database

From this website you can gather the protocol that is being used as output by default.
During this tutorial we gonna use the case it uses the IBM terminal 8P5C/RJ45 protocol as default.


# Step 2: Getting the microcontroller
Personally I recommend getting the Arduino Pro Micro clone or the USB-C variant from china cause thats the cheapest solution, you can find a lot of offers on sites like Aliexpress, Temu etc.

<img src="https://github.com/bipknit/soarerConverter/blob/main/src/promicrousbc.png" alt="Arduino Pro USB-C" width="400"/>

You can also get these Teensy® USB Development Boards but during this tutorial we are going to use the Arduino Pro Micro

<img src="https://github.com/bipknit/soarerConverter/blob/main/src/teensy20plusplus.png" alt="Teensy++ 2.0" width="400"/>

