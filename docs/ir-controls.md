# Infrared controls

The Minthouz Fano P12L is controlled by an eight-button NEC-IR remote. This
integration sends codes through an existing Home Assistant `infrared.*` emitter
entity; it does not connect to hardware directly. The codes were captured
with `ir-keytable` and a USB receiver (`address=0x00`, one-byte commands).
Other remotes with different codes will not work unchanged.

![Minthouz Fano P12L remote](images/remote.png)

| Entity | Controls |
|--------|----------|
| Fan | Power and three speeds (33%, 66%, 100%) |
| LED light | Three brightness levels using a cycling button |
| Timer buttons | Two-, four- and six-hour presets |

The remote offers no feedback: entity state is assumed, and a physical remote
can make it drift. The fan avoids depending on its assumed state by using a
hardware quirk: Timer 2H always turns the fan on at speed 1, while the power
button toggles. Timer 2H → Power → Power forces the fan on at speed 1; Timer
2H → Power forces it off. These sequences briefly cycle power and clear the
timer's indicator LED.

Timer buttons themselves turn the fan on at speed 1 when it was off. The LED
button cycles off → low → medium → high → off, so the light entity calculates
how many presses are needed from its last assumed state.

## Emitter hardware

The example [`esphome/ir-blaster.yaml`](../esphome/ir-blaster.yaml) configures
an ESP32 with an IR LED and ESPHome's experimental `infrared`/`ir_rf_proxy`
platform. Connect an IR LED through a suitable driver, and adjust `board` and
`ir_led_pin` to match your hardware. Copy
[`esphome/secrets.yaml.example`](../esphome/secrets.yaml.example) to a local
`secrets.yaml`, supply Wi-Fi credentials and a fresh API key, then flash the
device with `esphome run ir-blaster.yaml` from the `esphome/` directory.
