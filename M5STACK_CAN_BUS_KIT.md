# m5stack Canbus Kit

This option uses the [m5stack Canbus Kit](https://shop.m5stack.com/products/atom-canbus-kit-ca-is3050g) to interact with the Zehnder ComfoAir Q ventilation unit.

  ![M5STACK CAN][m5stack_can]

## Components

- m5stack Canbus Kit
- 5V power supply 
  - standdard usb power adapter
  - [step-down converter](https://www.aliexpress.com/item/1005002797242220.html) \
    [usb-c connector](https://www.aliexpress.com/item/1005005068786615.html) (2pin type-c male)
- Any ethernet cable (RJ45 connector)
- A USB-C cable to connect the m5stack Atom Lite to your computer

### Hardware

1. Strip one side of the ethernet cable
2. Connect the orange, white-orange, white-green wires to the `m5stack can` connector (see diagram + pictures below).
3. Connect the blue and white-green to the step-down converter
4. Connect the usb-c connector to the m5stack atom controller
5. Connect the other side of the cable to the RJ45 port of the ventilation unit (located at the top, behind the sliding cover).


### Connection diagram

```

|----------------+ 
|                | 
|   [ComfoAir]   | 
|                |                                           m5stack can
|                |      +++++++++++++++++++++            +-----------------+
|           RJ45 o------|   (orange)  CAN-H o------------o CAN-H           |
|----------------+      | (w/orange)  CAN-L o------------o CAN-L   usb-c   O-----+
                        |  (w/green)    GND o-------+----o GND             |     |
                        |     (blue)   +12V o---+   |    +-----------------+     |
                        +++++++++++++++++++++   |   |                            |
                                                |   |    +-----------+           |
                                                |   +----o           o----+      |
                                                |        |  Mini560  |    +------+
                                                +--------o           o----+ 
                                                         +-----------+
```

Here some pictures of the current setup connected to the Zehnder ComfoAir Q

![m5stack with step-down converter][m5stack_mini560]
![m5stack test installation][m5stack_installed]

[m5stack_can]: ./docs/m5stack_can_kit.png
[m5stack_mini560]: ./docs/m5stack_mini560.png
[m5stack_installed]: ./docs/m5stack_installed.png
