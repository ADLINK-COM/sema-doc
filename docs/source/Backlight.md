
### Backlight Control

Support backlight brightness and backlight enable





#### List of SEMA EAPI

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
