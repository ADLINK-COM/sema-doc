
### GPIO Access

Provides a set of functions to control GPIO pins.



#### List of SEMA EAPI

1. Only supports the specific exnternal GPIO controller : **PCA9535 I/O expander on COM/SMARC Module**
2. For Linux users, PCA9535 kernel driver is ready on your Linux. Please use GPIO sysfs Interface to access pins. We don't provide any SEMA GPIO EAPI function on Linux environment.


<br />
<br />


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
