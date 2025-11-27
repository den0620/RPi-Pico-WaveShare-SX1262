# RPi-Pico-WaveShare-SX1262
RPi Pico Replica + SX1262

So I have managed to somewhat start RPi Pico replica (type-c) with bare SX1262 radio module

I couldn't connect to any nodes so I guess there's none nearby but SX1262 didn't fail and even stated something to meshtastic firmware

This all was connected with just a breadboard and several cables so only worked when pushed within a specific angle

Here is what I've discovered:

Special pico-sized sx1262 and `/firmware/variants/rp2040/rpipico/variant.h` say:

```
?? EXT_NOTIFY_OUT 22
?? BUTTON_PIN 17

LoRa's "BAT_AD": BATTERY_PIN 26 (bare SX1262) have none!

LoRa's "CLK": LORA_SCK 10
LoRa'S "MISO": LORA_MISO 12
LoRa's "MOSI": LORA_MOSI 11
LoRa's "CS": LORA_CS 3

LoRa's ??? LORA_DIO0 RADIOLIB_NC ???
LoRa's "RESET": LORA_RESET 15
LoRa's "DIO1": LORA_DIO1 20
LoRa's "BUSY": LORA_DIO2 2
LoRa's ??? LORA_DIO3 RADIOLIB_NC ??
```

Also connect Pico's `3V3` to LoRa's `3V3`

And a pair of Pico's `GND` to LoRa's `GND`

## Debug

```
SX126x init result -2
```

Bad wiring or/and no contact

```
SX126x init result -707
```

Bad contact (or/and bad wiring?)

```
SX1262 init success
```

Everything's good

# Update

I've connected LoRa to antenna and it worked ok. After I've made a DIY one from two empty cans it works good
