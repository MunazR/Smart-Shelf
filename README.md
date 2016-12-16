# Smart Shelf

This IoT smart shelf can be used to get the quantity of the items placed it. It uses load sensors to measure the total weight on the shelf and the unit weight of each item to calculate the total number of products on the shelf.


## Parts Used
* 4 x [Load Sensor](https://www.sparkfun.com/products/10245)
  * Alternatively use a bathroom scale
* 1 x [OpenScale Microcontroller](https://www.sparkfun.com/products/13261)
* 1 x Raspberry Pi 3


### Load Sensors

Four load sensors are used to measure the weight on the shelf. These are the same load sensors you would find in your bathroom scale. It may be better and cheaper to purchase a bathroom scale instead and take it apart as you can use it as a platform for your shelf as well.

### OpenScale Microcontroller

The OpenScale microcontroller is used to read the input from the load sensors and transmit it to the Raspberry Pi using a serial USB connection.

### Raspberry Pi
The Raspberry Pi uses Node-RED to translate the weight readings from the OpenScale microcontroller, calculate the product quantities and display it to the user.


## Steps to Build

1. Attach your load sensors to a flat platform, or take apart any unused electronics in your bathroom scale such as the LCD display and circuitry other than the four load sensors.

2. Wire your load sensors to the combinator following the schematic below. The load sensors connect to the load sensor combinator on the OpenScale microcontroller which will take the four inputs and provide a single output.
  
  ![Final Design Schematic](/images/Final Design Schematic.png)

  * If you're having trouble getting the combinator to work, like myself, you can try to create a [wheatstone bridge](https://en.wikipedia.org/wiki/Wheatstone_bridge) configuration. Refer to [this schematic](https://cdn.sparkfun.com/datasheets/Sensors/ForceFlex/openScale_v04.pdf) on the OpenScale. Look at the wiring for the combiner in the bottom right and replicate it in your wiring for the load sensors. Connect the four-wire output from the load sensors to the four-wire load cell input on the OpenScale.

3. Connect your Raspberry Pi to your OpenScale using a USB cable.

## Calibration
After building the shelf, you'll need to calibrate it. Follow the instructions [here](https://learn.sparkfun.com/tutorials/openscale-applications-and-hookup-guide?_ga=1.181554343.1825949873.1479936802#calibration-suggestions) to calibrate your scale. You'll need to tare it, set the calibration factor and turn off any data you will not need. The OpenScale comes with a built-in temperature sensor that you may also use.

Once calibration is complete you can will get readings from the OpenScale over the USB serial connection.

## Raspberry Pi - Node-RED
Node-RED is a simple wiring tool for Internet of Things applications. A sample Node-RED flow has been included in this repository. You will need to change it to support your product type and serial port identifier.

## Final Product

![Shelf](/images/Shelf.JPG)

## Additional Resources
* [Getting started with load cells](https://learn.sparkfun.com/tutorials/getting-started-with-load-cells?_ga=1.112962820.1825949873.1479936802)
* [OpenScale Applications and Hookup Guide](https://learn.sparkfun.com/tutorials/openscale-applications-and-hookup-guide?_ga=1.179366308.1825949873.1479936802)
* [Load Cell Amplifier HX711 Breakout Hookup Guide](https://learn.sparkfun.com/tutorials/load-cell-amplifier-hx711-breakout-hookup-guide?_ga=1.179366308.1825949873.1479936802)
* [Node-RED](https://nodered.org/)
