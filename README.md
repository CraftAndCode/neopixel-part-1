# Neopixel: Part 1

```package
core
radio
microphone
neopixel=github:microsoft/pxt-neopixel
```

```template
basic.forever(function () {
})
```

```blocks
basic.forever(function () {
strip = neopixel.create(DigitalPin.P0, 10, NeoPixelMode.RGB)
})
```

## Step 0 @showDialog
Hello! Today we're going to learn how to import extensions into MakeCode and use the Neopixel extension to connect to an LED strip and change its colors.  
    
## Step 1 @showDialog
### What are extensions?
We've already learned to drive an LED connected to one of the Micro:bit pins. But more complex devices require constant communication with the Micro:bit using encoded electrical signals.
  
It would take too long to write a program to control such a device using only the code blocks provided. This is where extensions come to our rescue.
  
Extensions are parts of a program that perform specific tasks. Using them, you can do complex things with just a couple of blocks of code, because someone else has already written the rest for you.

## Step 2 @showDialog
### Neopixel extension

The Neopixel extension adds new blocks to MakeCode to control "smart" LED lighting. With this extension, we can assign colors to each LED separately using only one signal wire.
  
Before you start, connect the LED strip and the Micro:bit as shown in the diagram.
![](https://raw.githubusercontent.com/CraftAndCode/neopixel-extension/master/strip.png)

## Step 3 @showHint
### Configuring Micro:bit to work with the LED strip.
A ``||variables.set||`` block tells the device that an LED strip is connected to it.
  
Add this block to the program. To prepare the strip to work, enter the number of the pin to which the strip is connected and the amount of LEDs in it.
```blocks
strip = neopixel.create(DigitalPin.P0, 10, NeoPixelMode.RGB)

```
## Step 3.5 @showDialog
### Let there be light!
Let's take a look at some blocks to control the strip.
  
``||neopixel.show color||`` - lights up all the LEDs in the selected color
```block
let strip: neopixel.Strip = null
strip.showColor(neopixel.colors(NeoPixelColors.Red))
```
  
``||neopixel.show rainbow||`` - displays a rainbow or part of a rainbow
```block
let strip: neopixel.Strip = null
strip.showRainbow(1, 360)
```
    

## Step 4 @showHint
### Let there be light!
Let's add the new blocks to the program and see them in action!

See how the strip color changes when you add each of the blocks. Remember that these commands will only work if the strip was initialized with a ``||variables.set||`` block at the beginning of the program. 
```hint
Light up all the LEDs in the selected color 
```
```block
let strip: neopixel.Strip = null
strip.showColor(neopixel.colors(NeoPixelColors.Red))
```
```hint
  
Display a rainbow or part of a rainbow
```
```block
let strip: neopixel.Strip = null
strip.showRainbow(1, 360)
```
  
## Step 5 @showHint
### Example 1: Color change
This example shows how to control the lighting color using the ``||neopixel.show color||`` block.
```blocks
let strip = neopixel.create(DigitalPin.P0, 10, NeoPixelMode.RGB)
basic.forever(function () {
    strip.showColor(neopixel.colors(NeoPixelColors.Red))
    basic.pause(500)
    strip.showColor(neopixel.colors(NeoPixelColors.Green))
    basic.pause(500)
})
```

## Step 6 @showHint
### Example 2: Switch on - switch off
This example shows how to turn off the backlight using the ``||neopixel.show color||`` block. Because black represents no light, choosing black as a color turns all the lighting off.
```blocks
input.onButtonPressed(Button.A, function () {
    strip.showColor(neopixel.colors(NeoPixelColors.White))
})
input.onButtonPressed(Button.B, function () {
    strip.showColor(neopixel.colors(NeoPixelColors.Black))})
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 10, NeoPixelMode.RGB)

```
## Step 7 @showDialog
### Now it's your turn!
Write a program that will display different colors depending on the angle of the Micro:bit. We've already learned how to control the Micro:bit by tilting it in [this tutorial](https://makecode.microbit.org/#tutorial:github:craftandcode/sensors-accelerometer/ru).
## Step 8
### Answers: Now it's your turn!
One program option:
```blocks
input.onGesture(Gesture.TiltLeft, function () {
    strip.showColor(neopixel.colors(NeoPixelColors.Blue))
})
input.onGesture(Gesture.TiltRight, function () {
    strip.showColor(neopixel.colors(NeoPixelColors.Yellow))
})
input.onGesture(Gesture.LogoDown, function () {
    strip.showColor(neopixel.colors(NeoPixelColors.Green))
})
input.onGesture(Gesture.LogoUp, function () {
    strip.showColor(neopixel.colors(NeoPixelColors.Red))
})
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 10, NeoPixelMode.RGB)

```
## Step 9
All the tasks are complete! In the next lesson, we will get to know the rest of the backlight control units and will be able to light up the LEDs individually.
