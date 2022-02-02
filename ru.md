# Neopixel: Часть 1

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
Привет! Сегодня мы узнаем, как подключать к MakeCode расширения, открывающие доступ к новым блокам кода, и используем их, чтобы управлять светодиодной подсветкой!  
    
## Step 1 @showDialog
### Что такое расширение?
Мы знаем, как включать и выключать светодиод, подключенный к выводу Micro:bit. Но более сложные устройства требуют постоянного обмена информацией с Micro:bit с помощью закодированных электрических сигналов.  
  
Чтобы написать программу для управления таким устройством с использованием только одних лишь стандартных блоков, потребовалось бы слишком много времени. Здесь нам на помощь приходят расширения.
  
Расширения — это части программы для выполнения конкретных задач. С помощью библиотек можно выполнять сложные действия всего парой блоков кода, потому что кто-то другой уже написал всё остальное за вас.

## Step 2 @showDialog
### Расширение Neopixel
Расширение Neopixel добавляет в MakeCode блоки для управления "умной" светодиодной подсветкой. С этим расширением мы можем задавать цвет каждому светодиоду отдельно, используя только один сигнальный провод.
  
Перед тем, как начать, соедини светодиодную ленту и Micro:bit так, как показано на схеме.
![](https://raw.githubusercontent.com/CraftAndCode/neopixel-extension/master/strip.png)

## Step 3 @showHint
### Настраиваем Micro:bit на работу с лентой
Блок ``||variables.установить значение||`` говорит устройству, что к нему подключена светодиодная лента.
  
Добавь этот блок в программу. Для подготовки ленты к работе, укажи в полях номер контакта, к которому подключена лента и количество светодиодов в ней.

```blocks
strip = neopixel.create(DigitalPin.P0, 10, NeoPixelMode.RGB)

```
## Step 3.5 @showDialog
### Да будет свет!
Давай познакомимся с некоторыми блоками управления лентой:
  
``||neopixel.show color||`` - зажигает все светодиоды выбранным цветом
```block
let strip: neopixel.Strip = null
strip.showColor(neopixel.colors(NeoPixelColors.Red))
```
  
``||neopixel.show rainbow||`` - отображает радугу или её часть
```block
let strip: neopixel.Strip = null
strip.showRainbow(1, 360)
```
  


## Step 4 @showHint
### Да будет свет!
Давай добавим новые блоки в программу и посмотрим на них в действии!

Проверь, как меняется цвет ленты при добавлении каждого из блоков. Помни, что эти команды будут работать только если в начале программы лента была инициализирована блоком ``||variables.установить значение||``.
```hint
Зажечь все светодиоды одним цветом
```
```block
let strip: neopixel.Strip = null
strip.showColor(neopixel.colors(NeoPixelColors.Red))
```
```hint
  
Показать радугу
```
```block
let strip: neopixel.Strip = null
strip.showRainbow(1, 360)
```
## Step 5 @showHint
### Пример 1: Смена цвета
В этом примере показывается, как управлять цветом подсветки с помощью блока ``||neopixel.show color||``.
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
### Пример 2: Включить - выключить
Этот пример показывает, как выключить подсветку с помощью блока ``||neopixel.show color||``.
```blocks
input.onButtonPressed(Button.A, function () {
    strip.showColor(neopixel.colors(NeoPixelColors.White))
})
input.onButtonPressed(Button.B, function () {
    strip.showColor(neopixel.colors(NeoPixelColors.Black))
})
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 10, NeoPixelMode.RGB)

```
## Step 7 @showHint
### Теперь твой черёд!
Напиши программу, которая будет показывать разные цвета в зависимости от наклона Micro:bit. Управлять Micro:bit с помощью наклона мы научились [этом уроке](https://makecode.microbit.org/#tutorial:github:craftandcode/sensors-accelerometer/ru).
## Step 8
### Ответы: Теперь твой черёд!
Один из вариантов программы:
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
Все задания выполнены! В следующем уроке мы познакомимся с остальными блоками управления подсветкой и сможем зажигать светодиоды по отдельности.
