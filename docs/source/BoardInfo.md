
### Board Information

Provides an interface to control or get the board's information, including:

* Static board information (ex: module name, BIOS version, or manufacturer name)
* Dynmical board information (ex: voltage, current, boot count or temperature)
* Failure forensics (ex: restart event)



#### List of SEMA EAPI

```
uint32_t EApiBoardGetValue(uint32_t Id, uint8_t* pData, uint32_t nSize)
```

**Description**

   Information about the hardware platform.

* Parameters:

  * uint32_t Id:

    Select ID for the first parameter:

    | ID                                         | Description                                      | Units                       |
    | :----------------------------------------- | :----------------------------------------------- | --------------------------- |
    | EAPI_ID_GET_EAPI_SPEC_VERSION              | EAPI Specification Version used to implement API |                             |
    | EAPI_ID_BOARD_BOOT_COUNTER_VAL             | Boot Counter                                     |                             |
    | EAPI_ID_BOARD_RUNNING_TIME_METER_VAL       | Running Time Meter                               | minutes                     |
    | EAPI_ID_BOARD_LIB_VERSION_VAL              | Vendor Specific Library                          |                             |
    | EAPI_ID_HWMON_CPU_TEMP                     | CPU Temperature                                  |                             |
    | EAPI_ID_HWMON_SYSTEM_TEMP                  | System Temperature                               |                             |
    | EAPI_ID_HWMON_VOLTAGE_VCORE                | CPU Core Voltage                                 | millivolts                  |
    | EAPI_ID_HWMON_VOLTAGE_2V5                  | 2.5V Voltage                                     | millivolts                  |
    | EAPI_ID_HWMON_VOLTAGE_3V3                  | 3.3V Voltage                                     | millivolts                  |
    | EAPI_ID_HWMON_VOLTAGE_VBAT                 | Battery Voltage                                  | millivolts                  |
    | EAPI_ID_HWMON_VOLTAGE_5V                   | 5V Voltage                                       | millivolts                  |
    | EAPI_ID_HWMON_VOLTAGE_5VSB                 | 5V Standby Voltage                               | millivolts                  |
    | EAPI_ID_HWMON_VOLTAGE_12V                  | 12V Voltage                                      | millivolts                  |
    | EAPI_ID_HWMON_FAN_CPU                      | CPU Fan speed                                    | RPM                         |
    | EAPI_ID_HWMON_FAN_SYSTEM                   | System Fan speed                                 | RPM                         |
    | SEMA_EAPI_ID_BOARD_POWER_UP_TIME           | Get the operating time after power up            | seconds                     |
    | SEMA_EAPI_ID_BOARD_RESTART_EVENT           | Get the restart event                            | See **Note 1**              |
    | SEMA_EAPI_ID_BOARD_CAPABILITIES            | Get the capabilities of this board or system     | See **Note 2**              |
    | SEMA_EAPI_ID_BOARD_CAPABILITIES_EX         | Get extended BMC capabilities                    | See **Note 3**              |
    | SEMA_EAPI_ID_BOARD_SYSTEM_MIN_TEMP         | Board Min Temperature                            | 0.1 Kelvins                 |
    | SEMA_EAPI_ID_BOARD_SYSTEM_MAX_TEMP         | Board Max Temperature                            | 0.1 Kelvins                 |
    | SEMA_EAPI_ID_BOARD_SYSTEM_STARTUP_TEMP     | Board Startup Temperature                        | 0.1 Kelvins                 |
    | SEMA_EAPI_ID_BOARD_CPU_MIN_TEMP            | CPU Min Temperature                              | 0.1 Kelvins                 |
    | SEMA_EAPI_ID_BOARD_CPU_MAX_TEMP            | CPU Max Temperature                              | 0.1 Kelvins                 |
    | SEMA_EAPI_ID_BOARD_CPU_STARTUP_TEMP        | CPU Startup Temperature                          | 0.1 Kelvins                 |
    | SEMA_EAPI_ID_BOARD_MAIN_CURRENT            | Get main power current                           | unit: mA, resolution=1/10mA |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_GFX_VCORE       | GFX voltage                                      | millivolts                  |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_1V05            | 1.05 V voltage                                   | millivolts                  |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_1V5             | 1.5 V voltage                                    | millivolts                  |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_VIN             | Vin Voltage                                      | millivolts                  |
    | SEMA_EAPI_ID_HWMON_FAN_SYSTEM_2            | 2nd System Fan                                   | RPM                         |
    | SEMA_EAPI_ID_HWMON_FAN_SYSTEM_3            | 3rd System Fan                                   | RPM                         |
    | SEMA_EAPI_ID_BOARD_2ND_SYSTEM_TEMP         | 2nd board Temperature                            | 0.1 Kelvins                 |
    | SEMA_EAPI_ID_BOARD_2ND_SYSTEM_MIN_TEMP     | 2nd board Min Temperature                        | 0.1 Kelvins                 |
    | SEMA_EAPI_ID_BOARD_2ND_SYSTEM_MAX_TEMP     | 2nd board Max Temperature                        | 0.1 Kelvins                 |
    | SEMA_EAPI_ID_BOARD_2ND_SYSTEM_STARTUP_TEMP | 2nd board Startup Temperature                    | 0.1 Kelvins                 |
    | SEMA_EAPI_ID_BOARD_POWER_CYCLE             | Power cycle counter                              |                             |
    | SEMA_EAPI_ID_BOARD_BMC_FLAG                | status of the BMC                                | See **Note 4**              |
    | SEMA_EAPI_ID_BOARD_BMC_STATUS              | status of the BMC                                |                             |
    | SEMA_EAPI_ID_BOARD_IO_CURRENT              | IO current                                       |                             |




    **Note 1**: The following table describes the definition of Restart Event:


    | Code | Code Name   | Description                                                  |
    | ---- | ----------- | ------------------------------------------------------------ |
    | 0x00 | UNKNOWN     | Unknown reason of restart (shown only on first BMC power-up) |
    | 0x20 | SW_RESET    | A reset by software caused the restart of the system         |
    | 0x30 | HW_RESET    | A reset by hardware caused the restart of the system (e.g. reset button) |
    | 0x40 | WATCHDOG    | The Watchdog has restarted the system                        |
    | 0x50 | BIOS_FAULT  | Standard BIOS is corrupted -> boot from Fail-Safe BIOS       |
    | 0x60 | POWER_DOWN  | The system was shut down (e.g. power button, ACPI shutdown)  |
    | 0x70 | POWER_LOSS  | The system is restarted after a power loss (e.g. external power supply instable or switched off while the system was running) |
    | 0x80 | POWER_CYCLE | The system is restarted after a power cycle (e.g. internal power supply has failed) |
    | 0x90 | VIN_DROP    | The system is restarted after a voltage drop of the main input voltage |
    | 0xA0 | PWR_FAIL    | The system is restarted after a PWRFAIL detection of an internal power supply circuit |
    | 0xB0 | CRIT_TEMP   | The system was shut down by ACPI Watchdog (CPU reached critical temperature) |
    | 0xC0 | WAKE_UP     | The system has received a wake event and resumes operation from a sleep state |

    <br />

    **Note 2**: The following table describes the definition of BMC Capability Bits. it shows that which functions can be supported on your platform:

    -  When Bit value goes to **1**, it indicates **enabled**

    -  When Bit value goes to **0**, it indicates **disabled**

    | Bit    | Description                                          |
    | ------ | ---------------------------------------------------- |
    | Bit 0  | Uptime & power cycles counter supported              |
    | Bit 1  | System restart event supported                       |
    | Bit 2  | 1k USER flash memory available supported             |
    | Bit 3  | Watchdog supported                                   |
    | Bit 4  | Temperature sensors installed/available              |
    | Bit 5  | Voltage sensors installed/available                  |
    | Bit 6  | Storage of failure reason available (exception code) |
    | Bit 7  | Bootloader timeout Configuration                     |
    | Bit 8  | Display control available                            |
    | Bit 9  | Power up watchdog available                          |
    | Bit 10 | the current sensors installed/available ??????       |
    | Bit 11 | Boot counter supported                               |
    | Bit 12 | Input-Voltage0                                       |
    | Bit 13 | Input-Voltage1                                       |
    | Bit 14 | Rsense for Input-Voltage: 0=8 mR, 1=4 mR )           |
    | Bit 15 | Fail-Safe-BIOS supported                             |
    | Bit 16 | Ext. I2C bus #1 available                            |
    | Bit 17 | Ext. I2C bus #2 available                            |
    | Bit 18 | CPU FAN available                                    |
    | Bit 19 | System Fan available                                 |
    | Bit 20 | AT/ATX mode supported                                |
    | Bit 21 | Thermal SCI supported                                |
    | Bit 22 | Power up to last state                               |
    | Bit 23 | Backlight restore                                    |
    | Bit 24 | DTS register                                         |
    | Bit 25 | DTS register offset                                  |
    | Bit 26 | Smart fan #3 available                               |
    | Bit 27 | Smart fan #4 available                               |
    | Bit 28 | TIVA GPIOs support (12 GPIOs)                        |
    | Bit 29 | Ext. I2C bus #3 available                            |
    | Bit 30 | Ext. I2C bus #4 available                            |
    | Bit 31 | BMC is from TIVA type                                |

    <br />

    **Note 3**: The following table describes the definition of the extended BMC Capability Bits:

    | Bit    | Description                                          |
    | ------ | ---------------------------------------------------- |
    | Bit 32 | Board2 Temperature supported                         |
    | Bit 33 | PEC protocol supported                               |
    | Bit 34 | reserved                                          |
    | Bit 35 | Error log supported                                  |
    | Bit 36 | 1-Wire supported                                     |
    | Bit 37 | Wake-by-BMC supported                                |
    | Bit 38 | GPIO ADC supported                                   |
    | Bit 39 | SoftFan supported                                    |
    | Bit 40 | Parameter memory supported                           |
    | Bit 41 | Extended I2C registers for status and data supported |

    <br />

    **Note 4**: The following table describes the definition of the BMC Flag/Status:

    | Bit       | Description                                                  |
    | --------- | ------------------------------------------------------------ |
    | Bit 7     | BIOS Select<br />    - Single BIOS = 0<br />    - Fail-Safe-BIOS = 1 |
    | Bit 6     | ATX Mode<br />    - AT Mode = 0<br />    - ATX mode = 1      |
    | Bit 5     | reserved                                                   |
    | Bit 0 - 4 | Exception Code <br />**Note**: Code definition will be different for each hardware. please refer to [ADLINK offifical Website](https://www.adlinktech.com/) to seach for the Hardware User Manual or use **EApiGetExceptionDescription** |

  * uint8_t* pData:

    Pointer to a buffer that receives the value's data. This  parameter can be NULL if the data is not required.

  * uint32_t nSize:

    Pointer to a variable that specifies the size, in bytes, of the buffer pointed to by the pBuffer parameter. When the function returns, this variable contains the size of the data copied to pBuffer including the terminating null character.



<br />
<br />

```
uint32_t EApiBoardGetStringA(uint32_t Id, uint8_t* pData, uint32_t nSize)
```

**Description**

   Information about the hardware platform.

* Parameters:

  * uint32_t Id:

    Select ID number or Code name as the first parameter

    | ID                                         | Description                         | Format |
    | ------------------------------------------ | ----------------------------------- | ------ |
    | EAPI_ID_BOARD_MANUFACTURER_STR             | Board manufacturer name             | String |
    | EAPI_ID_BOARD_NAME_STR                     | Board name                          | String |
    | EAPI_ID_BOARD_SERIAL_STR                   | Serial number                       | String |
    | EAPI_ID_BOARD_BIOS_REVISION_STR            | Board BIOS revision                 | String |
    | EAPI_ID_BOARD_PLATFORM_TYPE_STR            | Platform ID                         | String |
    | EAPI_ID_BOARD_HW_REVISION_STR              | HW revision string                  | String |
    | SEMA_EAPI_ID_BOARD_BOOT_VERSION_STR        | Boot version string                 | String |
    | SEMA_EAPI_ID_BOARD_APPLICATION_VERSION_STR | Firmware application version string | String |
    | SEMA_EAPI_ID_BOARD_CHIPSET_ID_STR          | Chipset ID string                   | String |
    | SEMA_EAPI_ID_BOARD_RESTART_EVENT_STR       | Restart Event string                | String |
    | SEMA_EAPI_ID_BOARD_DEVICE_ID_STR           | Device ID string                    | String |
    | SEMA_EAPI_ID_BOARD_REPAIR_DATE_STR         | Last Repair Date                    | String |
    | SEMA_EAPI_ID_BOARD_MANUFACTURE_DATE_STR    | Manufacture date                    | String |
    | SEMA_EAPI_ID_BOARD_MAC_STRING              | MAC address on module               | String |
    | SEMA_EAPI_ID_BOARD_2ND_HW_REVISION_STR     | 2nd HW revision string              | String |
    | SEMA_EAPI_ID_BOARD_2ND_SERIAL_STR          | 2nd HW serial string                | String |

  * uint8_t* pData:

    Pointer to a buffer that receives the value's data. This  parameter can be NULL if the data is not required.

  * uint32_t nSize:

    Pointer to a variable that specifies the size, in bytes, of the buffer pointed to by the pBuffer parameter. When the function returns, this variable contains the size of the data copied to pBuffer including the terminating null character


<br />
<br />


```
uint32_t EApiBoardGetVoltageMonitor(uint8_t channel, uint32_t *pValue, char *pBuffer)
```

**Description**

   There will be different definition of Voltage on every channel for each hardware platform. please refer to [ADLINK official website](https://www.adlinktech.com/) to search for the Hardware User Manual.

* Parameters:

  * uint8_t channel:

    Select Channel number or Channel name as the first parameter

    | ID                               | Description             | Format  | Units      |
    | -------------------------------- | ----------------------- | ------- | ---------- |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN0  | voltage from channel 0  | &string | millivolts |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN1  | voltage from channel 1  | &string | millivolts |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN2  | voltage from channel 2  | &string | millivolts |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN3  | voltage from channel 3  | &string | millivolts |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN4  | voltage from channel 4  | &string | millivolts |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN5  | voltage from channel 5  | &string | millivolts |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN6  | voltage from channel 6  | &string | millivolts |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN7  | voltage from channel 7  | &string | millivolts |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN8  | voltage from channel 8  | &string | millivolts |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN9  | voltage from channel 9  | &string | millivolts |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN10 | voltage from channel 10 | &string | millivolts |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN11 | voltage from channel 11 | &string | millivolts |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN12 | voltage from channel 12 | &string | millivolts |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN13 | voltage from channel 13 | &string | millivolts |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN14 | voltage from channel 14 | &string | millivolts |
    | SEMA_EAPI_ID_HWMON_VOLTAGE_AIN15 | voltage from channel 15 | &string | millivolts |

  * uint32_t *pValue:

    Pointer to a buffer that receives the value's data

  * char *pBuffer:

    Pointer to a buffer that receives the description string


<br />
<br />

```
uint32_t EApiBoardGetErrorLog(
        uint32_t  position,
        uint32_t *ErrorNumber,
        uint8_t  *Flags,
        uint8_t  *RestartEvent,
        uint32_t *PwrCycles,
        uint32_t *Bootcount,
        uint32_t *Time,
        uint16_t *Status,
        signed char *CPUtemp,
        signed char *Boardtemp
)
```

**Description**

Get Error number history in the BMC. Failures in the Power Sequence are shown on the BMC status LED at the time where the issue occurs. The Error Log buffer stores those Power Sequence issues in an Error Log buffer. Beside of the displayed Error Code, the Error Log also stores information about the actual state and counters for better tracking of the issues. The latest entry in the Error Log Buffer is always found on position 0. The previous entry is found on position 1 and so on.

* Parameters:

  * uint32_t  position:

    The pointer point to the log to be read

  * uint32_t *ErrorNumber:

    Error Number. To get the detailed description, please use **EApiGetErrorNumberDescription**

  * uint8_t  *Flags:

     Exception Code, selected BIOS and Power Mode ( see **EApiBoardGetValue** function and
     `SEMA_EAPI_ID_BOARD_BMC_FLAG` parameter to mention about the definition of Exception Flag). To get the detailed description from exception code, please use **EApiGetExceptionDescription**

     **Note**: Exception Code will be different for each hardware. please refer to [ADLINK official website](https://www.adlinktech.com/) to search for the Hardware User Manual to check your codes.

  * uint8_t  *RestartEvent:

    System Restart Event (see **EApiBoardGetValue** function and `SEMA_EAPI_ID_BOARD_RESTART_EVENT` parameter to mention about the definition of Restart Event)

  * uint32_t *PwrCycles:

    Power Cycles Counter

  * uint32_t *Bootcount:
    Boot Counter

  * uint32_t *Time:

    Ontime Counter (seconds)

  * uint16_t *Status:

    Status information from BMC status command

  * signed char *CPUtemp:

    Current CPU temperature (if available)

  * signed char *Boardtemp:

    Current Board temperature (if available)





<br />
<br />


```
uint32_t EApiBoardGetCurErrorLog(
        uint32_t *ErrorNumber,
        uint8_t  *Flags,
        uint8_t  *RestartEvent,
        uint32_t *PwrCycles,
        uint32_t *Bootcount,
        uint32_t *Time,
        uint16_t *Status,
        signed char *CPUtemp,
        signed char *Boardtemp
)
```

**Description**

Get Error number history in the BMC. Failures in the Power Sequence are shown on the BMC status LED at the time where the issue occurs. The Error Log buffer stores those Power Sequence issues in an Error Log buffer. Beside of the displayed Error Code, the Error Log also stores information about the actual state and counters for better tracking of the issues. After retrieving the Error Log, the position will be automatically moved to next position (previous record).

* Parameters:

  * uint32_t *ErrorNumber:

    Error Number. To get the detailed description, please use **EApiGetErrorNumberDescription**

  * uint8_t  *Flags:

    Exception Code, selected BIOS and Power Mode ( see **EApiBoardGetValue** function and 		`SEMA_EAPI_ID_BOARD_BMC_FLAG` parameter) To get the detailed description from exception 		code, please use `SemaEApiBoardGetExceptionDescription`

    **Note**: Exception Code will be different for the platforms. please refer to [ADLINK official website](https://www.adlinktech.com/) to search for the Hardware User Manual to check your codes.

  * uint8_t  *RestartEvent:

    System Restart Event (see **EApiBoardGetValue** function and `SEMA_EAPI_ID_BOARD_RESTART_EVENT` parameter to mention about the definition of Restart Event)

  * uint32_t *PwrCycles:

    Power Cycles Counter

  * uint32_t *Bootcount:

    Boot Counter

  * uint32_t *Time:

    Ontime Counter (seconds)

  * uint16_t *Status:

    Status information from BMC status command

  * signed char *CPUtemp:

    Current CPU temperature (if available)

  * signed char *Boardtemp:

    Current Board temperature (if available)



<br />
<br />

```
uint32_t EApiGetErrorNumberDescription(uint32_t ErrorNum, uint8_t* pBuffer)
```

**Description**

Get text information of the Error number in the error log (get from **EApiBoardGetErrorLog**).

* Parameters:

  * uint32_t ErrorNum:

    The Error number (Exception Code) ( Please refer to [ADLINK offifical Website](https://www.adlinktech.com/) to seach for Hardware User Manual)

  * uint8_t* pBuffer:

    The description of error number.



<br />
<br />

```
uint32_t EApiGetExceptionDescription(uint32_t ErrorCode, uint8_t* pBuffer)
```

**Description**

Get text information of the Exception Code

* Parameters:

  * uint32_t ErrorNum:

    The Error number (Exception Code)  ( Please refer to [ADLINK offifical Website](https://www.adlinktech.com/) to seach for Hardware User Manual)

  * uint8_t* pBuffer:

    The description of error number
