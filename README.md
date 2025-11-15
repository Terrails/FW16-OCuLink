# OCuLink 8i Expansion Board for the Framework 16

## The schematic
![rev1.1](./imgs/schematic.svg)

The schematic in itself is pretty simple. You only need to connect the TX and RX PCIe lanes to the correct pins of the OCuLink connector. And then add components such as the EEPROM that the Embedded Controller (EC) on the laptop reads to configure GPIO pins and bifurcation.

A pdf version of the schematic is available [here](./imgs/schematic.pdf).

### EEPROM
As for the EEPROM, I have decided to use the same one that Framework is using in their [Dual SSD reference design](https://github.com/FrameworkComputer/ExpansionBay/tree/main/Dual%20SSD%20Reference%20Design). The `BR24G32FVT-3GE2`. The chip is marked as not recommended for new design according to Mouser, but it still seems to be in stock, although it can easily be swapped with another if required.

The EEPROM's address pins are all connected to the ground as that is the address the EC expects and by default the write protection (WP) is disabled by being connected to GND to allow writing data to it.

### Fans
For the fans I had to go with an alternative FPC header, as the one Framework uses on their boards was not available anywhere. The connector I use is slightly smaller, but still makes the connection nevertheless and the fans do spin up. I have specifically went with the [`AFC05-S04FIA-00`](https://www.lcsc.com/product-detail/C561383.html) that is available on LCSC to use with JLCPCB's assembly.

## Firmware
The firmware file is generated using [Framework's Expansion Bay tool](https://github.com/FrameworkComputer/ExpansionBayConfigurationGenerator). More info on the specific file I have been using in my testing and how I flashed it *SOON*.

## The PCB layout
![rev1.1](./imgs/pcb.png)

For the layout I have went with a 4-layer board and did manage to successfully stay within JLCPCB's fabrication limits. For the production runs I have used the `JLC04161H-3313` stackup and matched the differential pairs to it. I did also manage to stay within the minimum 0.3mm via hole size to keep costs somewhat down.
