
### Backlight Control

Support backlight brightness and backlight enable





#### List of sys Interface



* To get the current Backlight Enable State

  ```
  cat /sys/class/backlight/adl-bmc-bklight/bl_power
  ```

* To Set the current Backlight Enable State to either ON / OFF

  ```
  echo  > /sys/class/backlight/adl-bmc-bklight/bl_power
  ```

  For Example, 

  To enable the backlight: **$ echo 1 > /sys/class/backlight/adl-bmc-bklight/bl_power**

  To Disable the backlight: **$ echo 0 > /sys/class/backlight/adl-bmc-bklight/bl_power**

 

* To get the current Backlight Brightness level

  ```
  cat /sys/class/backlight/adl-bmc-bklight/actual_brightness
  ```

* To Set the current Backlight brightness level

  ```
  echo > /sys/class/backlight/adl-bmc-bklight/brightness
  ```

  For Example, to set the brightness level of 78: **$ echo 78 > /sys/class/backlight/adl-bmc-bklight/brightness**





<br />



#### List of SEMA EAPI (Support Windows & Linux)

```
uint32_t EApiVgaGetBacklightEnable(uint32_t PanelId, uint32_t *pEnable)
```

**Description**

Returns current Backlight status for specified Flat Panel

* Parameters:
  * uint32_t PanelId:

    Select Backlight IDs as the first parameter

    | ID                  | Description                  |
    | ------------------- | ---------------------------- |
    | EAPI_ID_BACKLIGHT_1 | Backlight Local Flat Panel 1 |

  * uint32_t \*pEnable:

    Indicate the status for on/off

    | ID                     | Description                                       |
    | ---------------------- | ------------------------------------------------- |
    | EAPI_BACKLIGHT_SET_ON  | Requests/Signifies that the backlight is enabled  |
    | EAPI_BACKLIGHT_SET_OFF | Requests/Signifies that the backlight is disabled |




<br />
<br />


```
uint32_t EApiVgaSetBacklightEnable(uint32_t PanelId,  uint32_t Enable)
```

**Description**

Set the enable status for specified Flat Panel

* Parameters:

  * uint32_t PanelId:

    ​		Select ID or code name as the first parameter

    | ID                  | Description                  |
    | ------------------- | ---------------------------- |
    | EAPI_ID_BACKLIGHT_1 | Backlight Local Flat Panel 1 |

  *  uint32_t Enable:

     ​		Select ID for Backlight Enable Values

     | ID                     | Description                                       |
     | ---------------------- | ------------------------------------------------- |
     | EAPI_BACKLIGHT_SET_ON  | Requests/Signifies that the backlight is enabled  |
     | EAPI_BACKLIGHT_SET_OFF | Requests/Signifies that the backlight is disabled |




<br />
<br />


```
uint32_t EApiVgaGetBacklightBrightness(uint32_t PanelId, uint32_t *pBright)
```

**Description**

Get the current the value of brightness

* Parameters:

  * uint32_t PanelId:

    ​     	Select ID or code name as the first parameter

    | ID                  | Description                  |
    | ------------------- | ---------------------------- |
    | EAPI_ID_BACKLIGHT_1 | Backlight Local Flat Panel 1 |

  * uint32_t *pBright:

    ​         Pointer to a buffer that receives the current backlight brightness level.  



<br />
<br />

```
uint32_t EApiVgaSetBacklightBrightness(uint32_t PanelId, uint32_t Bright)
```

**Description**

Set the current the value of brightness

* Parameters:

  * uint32_t PanelId:

    ​		Select ID or code name as the first parameter

    | ID                  | Description                  |
    | ------------------- | ---------------------------- |
    | EAPI_ID_BACKLIGHT_1 | Backlight Local Flat Panel 1 |

  * uint32_t Bright:

    ​	     Configure backlight Brightness level and maximum level goes to 255
