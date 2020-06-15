
### GPIO Access

* Provides a set of functions to control GPIO pins.
* Only supports the specific exnternal GPIO controller : PCA9535 I/O expander on COM/SMARC Module
* For Linux users, please refer to [this](https://adlink-epm.github.io/sema-doc/#/source/HowToInstallSEMA?id=install-native-gpio-driver) and install PCA9535 kernel driver on your target device. Please use GPIO sysfs Interface to access pins. We don't provide any SEMA GPIO EAPI function on Linux environment.



#### List of sys Interface

* To export the GPIO pin: (N should replace with gpio chip base number)

  ```
  echo N > /sys/class/gpio/export
  ```

* To read the direction of a pin

 ```
cat /sys/class/gpio/gpio251/direction
 ```

* To write the direction of a pin

 ```
echo in > /sys/class/gpio/gpio251/direction
 ```

* To read the value of a pin

 ```
cat /sys/class/gpio/gpio251/value
 ```

* To write the value of a pin

 ```
echo 1 > /sys/class/gpio/gpio251/value
 ```



<br />



#### List of SEMA EAPI (Only for Windows)


```
uint32_t EApiGPIOGetDirectionCaps(uint32_t Id, uint32_t* pnCapsIn, uint32_t* pnCapsOut)
```

**Description**

Get the capabilities of the current GPIO implementation from the selected GPIO interface. The ports where both input and output bit masks are 1 are GPIOs.

* Parameters:

  * uint32_t Id:

  * uint32_t* pnCapsIn:

    Pointer to a buffer that receives the bit mask of the supported inputs

  * uint32_t* pnCapsOut:

    Pointer to a buffer that receives the bit mask of the supported inputs




<br />
<br />


```
uint32_t EApiGPIOGetDirection(uint32_t GpioId, uint32_t Bitmask, uint32_t* pDirection)
```

**Description**

Reads the current configuration of the selected GPIO ports

* Parameters:

  * uint32_t Id:

  * uint32_t Bitmask:

    Bit mask

  * uint32_t* pnCapsOut:

    Pointer to a buffer that receives the direction of the selected GPIO ports



<br /> 


```
uint32_t EApiGPIOSetDirection(uint32_t GpioId, uint32_t Bitmask, uint32_t pDirection)
```

**Description**

Sets the configuration for the selected GPIO ports

* Parameters:

  * uint32_t GpioId:

  * uint32_t Bitmask:

    Bit mask. Only the ports with the level **EAPI_GPIO_HIGH**are processed

  * uuint32_t pDirection:

    Sets the direction of the selected GPIO ports. Bits with the value EAPI_GPIO_INPUT are inputs, 		bits with **EAPI_GPIO_OUTPUT** are outputs



<br />
<br />



```
EApiGPIOGetLevel(uint32_t GpioId, uint32_t Bitmask, uint32_t* plevel)
```

**Description**

Read the from GPIO ports

* Parameters:

  * uint32_t GpioId:

  * uint32_t Bitmask:

    Bit mask. Only selected bits are returned. Unselected bits return **EAPI_GPIO_LOW**

  * uint32_t* plevel:

    Pointer to a buffer that receives the GPIO level. Results can be read on a bit level



<br /> 



```
EApiGPIOSetLevel(uint32_t GpioId, uint32_t Bitmask, uint32_t plevel)
```

**Description**

Write to GPIO ports. Depending on the hardware implementation writing multiple GPIO ports with the bit mask option does not guarantee a time synchronous change of the output levels. Any GPO level setting to the pins witch are configured with “Input” will not take effect. This function call will not return this as an error. Please make sure the Bitmask also mask the Input pins.

* Parameters:

  * uint32_t GpioId:

  * uint32_t Bitmask:

    Value for a bit mask. Only selected bits are changed. Unselected bits remain unchanged

  * uint32_t* plevel:

    Input level of the selected GPIO port. Output for single ports is on a bit level
