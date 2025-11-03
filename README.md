# soarerConverter
<img src="https://github.com/bipknit/soarerConverter/blob/main/src/model_fbs_con.png?raw=true" alt="Model FBS Converter" width="400"/>

A tutorial for how to converting certain IBM keyboard protocol to standard USB
I made a lot of these converters in the past year so I decided to make a tutorial.

Big thanks to https://www.reddit.com/user/SharktasticA/ for helping me creating my first converter in 2024.

A summarized version can be found here: https://sharktastica.co.uk/buyers/converting

And another with the classic firmware here (build log): https://github.com/aholland909/Soarers-Convertor-Build
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

The pinouts for all possible protocols can be found at: https://github.com/bipknit/soarerConverter/blob/main/pinout/

Just to clarify, we are going to use this one:

<img src="https://github.com/bipknit/soarerConverter/blob/main/pinout/kbd_connector_ibmterm.png" alt="IBM Terminal protocol" width="400"/>


# Step 2: Getting the microcontroller
Personally I recommend getting the Arduino Pro Micro clone or the USB-C variant from china cause thats the cheapest solution, you can find a lot of offers on sites like Aliexpress, Temu etc.

<img src="https://github.com/bipknit/soarerConverter/blob/main/src/promicrousbc.png" alt="Arduino Pro USB-C" width="400"/>

You can also get these Teensy® USB Development Boards but during this tutorial we are going to use the Arduino Pro Micro

<img src="https://github.com/bipknit/soarerConverter/blob/main/src/teensy20plusplus.png" alt="Teensy++ 2.0" width="400"/>


# Step 2: Getting the RJ45 female connector
You can either purchase an RJ45 female head and handle the cable management yourself, or, for easier soldering, I recommend using an RJ45 breakout board. The breakout board simplifies wiring but requires slightly more space.

Keywords to find the RJ45 F head: Shield RJ45 8P8C Jack Connector, Shielded RJ45 8P8C Jack Connector

Keywords to find the RJ45 breakout board: RJ45 Adapter Board to XH2.54 Modular Ethernet Connector Breakout board.

# Step 3: Get them cables
Get some Pre-cut hookup wire or Dupont jumper wires depending on your solution.

First chapter end.

---

# Wiring & Setup Guide

This guide walks you through wiring a **Soarer's Converter** (or compatible firmware such as **Vial-QMK IBMPC_USB**) using a **Pro Micro** and an **RJ45 keyboard connection**.

Firmware can be found here (Vial QMK): https://github.com/qmk/qmk_toolbox/releases

## Step 1: Verify Keyboard-Side Pinout

Your keyboard-side pinout appears to be **correct**.  
If you’re unsure, you can check the **female pinout diagrams** available on my website.  
Your wiring should match those diagrams.


## Step 2: Check Pro Micro Wiring (Clock & Data Lines)

One common mistake is **reversing the Clock and Data pins** on the Pro Micro.

Please double-check your wiring — it looks like your **Clock (CLK)** and **Data (DAT)** lines may be swapped.

Make sure:
- **Clock (CLK)** from the keyboard goes to the correct **Pro Micro pin**
- **Data (DAT)** from the keyboard goes to the correct **Pro Micro pin**


## Step 3: Pull-Up Resistors

According to the **Soarer's Converter documentation:**

> In nearly all cases, these resistors are not needed.  
> But, if the keyboard has a very long cable (3m+), I recommend adding two pull-up resistors of 1 kΩ — one between Clock and +5 V, the other between Data and +5 V.

That said, if you already have 1 kΩ resistors on hand, you can safely add them — doing so won’t cause any issues and may improve signal reliability.

**Recommended:**  
- Add **1 kΩ resistor** between **Clock ↔ +5 V**  
- Add **1 kΩ resistor** between **Data ↔ +5 V**


## Step 4: Firmware Options

If you’re building a **literal Soarer's Converter**, use the **official Soarer's Converter firmware** — there’s only one, so just go with the latest version.

However, for a more modern and flexible alternative, consider the **Vial-QMK port of the IBMPC_USB converter**.  
This firmware supports a GUI (Vial) that allows **real-time editing and saving** of layout changes directly to the converter.

**Advantages of Vial-QMK:**
- GUI-based configuration
- No need to reflash for layout changes
- Compatible pinouts (no wiring changes needed)


## Step 5: Choosing the Right Firmware Binary

If you’re using a **Pro Micro (ATmega32U4)**, flash the following firmware file:




