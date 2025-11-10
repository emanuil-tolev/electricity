# Mounting the 70mai A800SE front and rear dashcam system in a Dacia Spring 45 (2021)

## Project context

### Using the car's 12V battery as a hardwire power source

#### How long will this camera last in parking mode using the car's 12V battery?

We measured the power consumption of a car dashcam (the 70mai A800SE 2025-10 purchase) by wiring it to a device which we configured to output 12.4V of power to simulate a 12V car battery.

[The measurement results are here.](https://docs.google.com/spreadsheets/d/1df-L6RSLH9bB3h5AUZsGnoTc4iXx0CGFSiUskLTtzaE/edit?gid=0#gid=0) . Interestingly, we were able to use dashcam hardwire kit to simulate turning parking mode on and off successfully by touching and removing the VCC signal wire to the 12V source while holding the ACC power wire to the source all the time, with the GND wire held to the source's other terminal. The cam used about 6.15W of power in full operation, about 3.7W in parking mode with all features on, about 1.8W with collision detection on but without timelapse capture of 1 photo per second, and only about 0.25W with both features off. It's not clear if there's any benefit at all to having parking mode with all features off.

My car's 12V battery was confirmed by the Dacia dealership to be the 50Ah variant, which means it's most likely the [Exide Excell](https://www.ebay.co.uk/itm/396003527759), to be confirmed by opening the hood, removing the frunk and checking, or using the car manual. Assuming a lower threshold of 20Ah (40% SoC at 100% 12V battery SoH), that means I can leave the dashcam plugged in for about 1440 hours before this threshold is reached, or 8.5 weeks. With only collision detection on, it'll last about 8 days. With all parking mode features on, it'll last about 4 days.

##### Other considerations

- Will this damage the car 12V battery or cause it to degrade faster in any way? Needs online research.
- Is the camera able to cut out its power consumption when a certain 12V battery % is reached?
- Is it possible to see the 12V battery approximate % SoC?
  - inside the car?
  - remotely via an app?

### Using a power bank

You can't and aren't supposed to use phone Li-ion power banks to run a dashcam because of two reasons:
1. Voltage drops when 12V is being provided can make the camera restart, stop or corrupt data on its SD card unexpectedly
2. Li-ion consumer power banks aren't safe for use in the summer in a hot car. LFP (LiFePo4) is recommended instead.

#### 70mai's own power bank - €230

#### Using a custom-built power bank

The goal of this project is to establish the feasability and approximate cost of building a custom power bank out of LFP cells, and if feasible, to actually build one. This will also be an exercise in learning about electricity.

It might be better to buy a 12V car battery with a larger capacity instead. Feasibility depends on cost.

# Building a custom dashcam power bank out of LFP cells