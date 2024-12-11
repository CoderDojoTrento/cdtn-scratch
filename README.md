
# CoderDojo Trento Scratch

A collection of extensions we use in our labs.

Forked from [OSEP Scratch](https://estea8968.github.io/osep_web_serial/app/)

Most code is intact from the original, we only disabled things we don't use or couldn't compile. 


## CDTN KIDSUINO EXTENSION 

Extension to run Keyestudio Kidsbits Kidsuino, in particular the set of sensors from [Keyestudio Kidsbits Smart Engineering Kit](https://www.keyestudio.com/products/kidsbits-smart-engineering-kit-for-arduino-compatible-with-lego-series-scratch-programming)

We are making this because original Keyestudio software only runs in win/mac with a driver, our extension should work also in Linux **without** driver installation.

**MAKE SURE TO INSTALL LATEST FIRMWARE**

NOTE: This software is *IN PROGRESS*, expect some bug.

WORKING THINGS:  

- connection: ok
- firmware screen: when served locally with file:// I see weird characters, apart from that seems working   
- digital read / write: some locking problems may arise, don't use concurrent code. TODO Kidsuino may have non-standard ports, check we cover them all
- analog read / write:  some locking problems may arise, don't use concurrent code. TODO Kidsuino may have non-standard ports, check we cover them all
- servo commands: seems to work, we limited it to kidsuino channels 12 and 13. 
- orange continuous 360° servo:  works but commanding it through angles doesn't make much sense, maybe we should provide a proper command
- grey 270° servo: TODO check angles 
- button:  works but gives 0 on pressed and 1 when open, better to invert 
- potentiometer: works
- touch sensor: works
- ultrasonic sensor: doesn't work
- IR sensor: to check
- steam sensor: works
- light: works
- buzzer: works
- integrated display: doesn't work
- joystick: doesn't work
- 
- translation: to improve
- power: tried to connect via USB to laptop without batteries and put together buzzer + light + grey servo + orange servo without heavy loads, didn't fry anything (so far..)


### Notes to myself to at least compile & build  

### Compile:

npm version:  8.19.4
node version: v16.20.2

```bash
npm install
```

```bash
npm run copy
```

### Dirty things I did to make it compile:

```bash
rm -rf node_modules/openai/
rm -rf node_modules/scratch3_llmstudio/
rm -rf node_modules/scratch-vm/src/extensions/scratch3_llmstudio
```

`source/scratch-vm/extension-support/extension-manager.js`: disabled openai and llmstudio for build problems

### deploy (sort of)

NOTE: for some reason osep scratch puts stuff in `app` instead of `dist/`

To put built website in `app/`

```bash```
npm run deploy
```

To view the website and have Arduino working, you don't event need a server!  Just point the server to 

file:///PATH/TO/YOUR/cdtn-scratch/build 


### Develop

I still didn't understand how to properly run & develop

In case you really want to use a proper web server,  remember you need HTTP*S*


For now: 

```bash
npm run copy && npm run build
```


WEB SERIAL ARDUINO:

source/scratch-vm/src/extensions/scratch3_webserialArduino/index.js

CDTN Kidsuino

source/scratch-vm/src/extensions/cdtn-kidsuino/index.js



## ORIGINAL OSEP STUFF   --------------------------------------------------

## Introduction
OSEP (Open-Source Extension Platform) Scratch is an open-source project running Scratch 3.0 GUI with official and experimental extensions. You can try out this project by going to [https://estea8968.github.io/osep_web_serial/app/](https://estea8968.github.io/osep_web_serial/app/).

This project intends to comply with the 2019 Curriculum Guidelines of 12-Year Basic Education in Taiwan and to promote the teaching and learning of computer technology in high school and elementary school. In order to empower students to use innovative technologies to explore and solve problems in daily life, several extensions about open data, the Internet of Things (IoT), artificial intelligence, and others are included. Below is a list of extensions and their information.

#### JSON / IFTTT / LASS / ThingSpeak
Developer: Gasolin

Github: https://github.com/gasolin/scratch3-internet

#### Speech to Text / URL & Text File / Google Sheets / Web Serial Arduino / Web Serial ESP-8266 / Web Serial ESP 32 / Web Serial PicoBoard / MQTT / Line / Open AI
Developer: estea chen

Github: https://github.com/estea8968/osep_web_serial

#### Chart.js / TAIEX / Google Maps / Data Processing / Google Sheets 
Developer: TYiC

Github: https://github.com/estea8968/osep_web_serial 

#### ML2Scratch / Posenet2Scratch / TM2Scratch / TMPose2Scratch / Google Maps 
Developer: champierre

Github: https://github.com/champierre

#### QR Code
Developer: Sugiura Lab

Github: https://github.com/sugiura-lab

#### Microbit More
Developer: Yengawa Lab

Github: https://github.com/microbit-more/mbit-more-v2

## Installation
This project requires you to have Git and Node.js installed. If you want to edit/play yourself, please follow these steps:

1. `git clone https://github.com/estea8968/osep_web_serial.git`
2. `cd osep_web_serial`
3. `npm install`
4. `npm run copy` (for Mac and Linux operating systems)
   `npm run copy:win` (for Windows operating system)

## Running
`npm start` (for Mac and Linux operating systems)

`npm run start:win` (for Windows operating system)

Then go to [http://localhost:8601/](http://localhost:8601/).

## Conclusions
OSEP Scratch is a collective effort of open-source developers and educators. We welcome your comments and suggestions.  
