# Projects
- [Dashcam power consumption measurement, estimates and alternative battery power sources](dashcam-battery.md)

# Notes by topic

# Notes from learning sessions

## 2025-11-08 with a friend at the Social Teahouse Makerspace

We measured the power consumption of a car dashcam (the 70mai A800SE 2025-10 purchase) by wiring it to a device which we configured to output 12.4V of power to simulate a 12V car battery. [The results are here.](https://docs.google.com/spreadsheets/d/1df-L6RSLH9bB3h5AUZsGnoTc4iXx0CGFSiUskLTtzaE/edit?gid=0#gid=0) . Interestingly, we were able to use dashcam hardwire kit to simulate turning parking mode on and off successfully by touching and removing the VCC signal wire to the 12V source while holding the ACC power wire to the source all the time, with the GND wire held to the source's other terminal. The cam used about 6.15W of power in full operation, about 3.7W in parking mode with all features on, about 1.8W with collision detection on but without timelapse capture of 1 photo per second, and only about 0.25W with both features off. It's not clear if there's any benefit at all to having parking mode with all features off.

My car's 12V battery was confirmed by the Dacia dealership to be the 50Ah variant, which means it's most likely the [Exide Excell](https://www.ebay.co.uk/itm/396003527759), to be confirmed by opening the hood, removing the frunk and checking, or using the car manual. Assuming a lower threshold of 20Ah (40% SoC at 100% 12V battery SoH), that means I can leave the dashcam plugged in for about 1440 hours before this threshold is reached, or 8.5 weeks. With only collision detection on, it'll last about 8 days. With all parking mode features on, it'll last about 4 days.

Questions for research:

- Exact dimensions of 12V battery, so we can determine if we can buy a replacement with a higher capacity (and at what cost - the original is around £65, although the dealership sold it to me for almost £100 during a mandatory warranty service).

## 2025-11-02 with a friend

### Common Li-Ion battery cells

18650 is a standard size battery with a nominal voltage of 3.7V (chemistry-dependent) - https://en.wikipedia.org/wiki/18650_battery

### Connecting battery cells in series and in parallel

### Measuring battery capacity

#### Wh vs Ah

Watt-hours are useful when we have an associated device where we know the consumption in watts.

Amper-hours are useful when we know the voltage at which the battery will operate (like 12V for the small accumulator car battery), because then we can talk about charging and discharging the battery in (A)mpere current terms directly.

You can convert between the two of them if you know the battery voltage. (I guess the nominal voltage will give you nominal Ah and Wh values, whereas the real average voltage during different operations will give the real capacities for those operations.)

### Internal resistance (ESR) and battery degradation

BMS = Battery Management Systems

### What does a BMS do

- Balance cell charging

A BMS detects individual cell voltage (using an ADC component). In theory, if all cells were exactly the same, then applying current across them would result in them charging at the exact same rate. But differences in manufacture means some cells have a little bit more capacity than others. That means they effectively charge to a lesser % SoC state for the same amount of time than the other cells. The BMS can balance charging so it's almost exactly the same across all cells, by turning on a little bit of extra resistance for each cell.

- Battery condition monitoring - a primary monitoring and control chip monitors the battery alongisde a secondary, cheaper control chip.
- Charge/discharge control - a BMS can detect dangerous conditions and choose to shut off all charging, all discharging, or both.

Questions for research:

- Does it also balance cell discharging? If so, how?

### Typical BMS components

#### Transistors CHG and DSG

2 transistors are used as essentially electrically-controllable on/off gates. When current flows through, the resistance either becomes infinitesmally low, letting all current through, or infinitesmally large, blocking all current from flowing. The charge transistor is used to stop all charging, whereas the discharge transistor controls all discharging. The BMS can choose to shut either or both of them off at any time.

#### ADCs

A Battery Management System (BMS) detects voltage by using high-precision analog-to-digital converters (ADCs) to measure the potential difference across each individual cell. An ADC samples the current voltage very often, resulting in an sampled curve that is a close-to-reality picture of the voltage level over time.