
### Smart Fan Control

Supports to control the smart fan. For each fan, four temperature thresholds can be configured with corresponding fan power levels which are applied when the threshold is exceeded.

Also provide two different operations to control PWM speed:

* Operation of SMART FAN Mode:  

  please use **EApiSmartFanSetMode** function with `SEMA_FAN_MODE_AUTO` parameter and provides 4 levels of temerpature & 4 levels of PWM are configured to get the below ladder chart:

  For example:

  |             | Level 1  | Level 2  | Level 3  | level 4  |
| ----------- | -------- | -------- | -------- | -------- |
  | Temperature | 30℃ (t1) | 40℃ (t2) | 50℃ (t3) | 80℃ (t4) |
  | PWM         | 40 (p1)  | 50 (p2)  | 60 (p3)  | 100 (p4) |
  
   

  ​                                      	![image-20200215141241146](SmartFan.assets/image-20200215141241146.png)
  
* Operation of SOFT FAN Mode:

  Please use BMC capability command to check Bit 34 & Bit 39 to see whic design of SOFT FAN are using on your platform.

  | Bit 34 | Bit 39 | FAN Mode               | Type                                                         |
  | ------ | ------ | ---------------------- | ------------------------------------------------------------ |
  | 0      | 1      | SEMA_FAN_MODE_SOFT_FAN | 4 level of temperature & PWM as the below linear **chart 1** |
  | 1      | 0      | SEMA_FAN_MODE_AUTO     | 2 level of temperature & PWM as the below linear **chart 2** |
  | 0      | 0      | Not support            | Not support                                                  |
  | 1      | 1      | Not support            | Not support                                                  |

  1. Linear chart 1 with 4 level of temperature & PWM configuration:
  
    For example,
  
    |             | Level 1  | Level 2  | Level 3  | level 4  |
| ----------- | -------- | -------- | -------- | -------- |
| Temperature | 30℃ (t1) | 40℃ (t2) | 50℃ (t3) | 80℃ (t4) |
 PWM         | 40 (p1)  | 50 (p2)  | 60 (p3)  | 100 (p4) |
      
      ![image-20200120180638356](SmartFan.assets/image-20200120180638356.png)

  2. Linear chart 2 with 2 level of temperature & PWM configuration:
    
    For exmple:  **(The Rule is  t1 = t2; t3 = t4; p3 = p4)**
  
    |             | Level 1      | Level 2      | Level 3      | level 4     |
| ----------- | ------------ | ------------ | ------------ | ------------ |
    | Temperature | **30℃ (t1)** | **30℃ (t2)** | **75℃ (t3)** | **75℃ (t4)** |
    | PWM         | 0 (p1)       | 30 (p2)      | **100 (p3)** | **100 (p4)** |
  
    ![image-20200215144606569](SmartFan.assets/image-20200215144606569.png)


<br />
#### List of SEMA EAPI


```
uint32_t uint32_t EApiSmartFanSetTempSetpoints(uint32_t FanID, uint32_t Level1, uint32_t Level2, uint32_t Level3, uint32_t Level4)
```

**Description**

Set temperature levels ( variable type is signed integer / Degree Celsius)

* Parameters:

  * uint32_t FanID:

    Select FAN ID as the parameter

    | ID                        | Description   |
    | ------------------------- | ------------- |
    | SEMA_EAPI_ID_FAN_CPU      | CPU Fan       |
    | SEMA_EAPI_ID_FAN_SYSTEM_1 | System Fan #1 |
    | SEMA_EAPI_ID_FAN_SYSTEM_2 | System Fan #2 |
    | SEMA_EAPI_ID_FAN_SYSTEM_3 | System Fan #3 |

  * uint32_t Level1:

    ​		 Configure the first level of temperature (t1)

  * uint32_t Level2:

    ​		 Configure the second level of temperature (t2)

  * uint32_t Level3:

    ​		 Configure the third level of temperature (t3)

  * uint32_t Level4:

    ​		 Configure the fourth level of temperature (t4)

<br /> 

```
uint32_t uint32_t EApiSmartFanGetTempSetpoints(uint32_t FanId, uint32_t* pLevel1, uint32_t* pLevel2, uint32_t* pLevel3, uint32_t* pLevel4)
```

**Description**

Get temperature levels

* Parameters:

  * uint32_t FanID:

    Select FAN ID as the parameter

    | ID                        | Description   |
    | ------------------------- | ------------- |
    | SEMA_EAPI_ID_FAN_CPU      | CPU Fan       |
    | SEMA_EAPI_ID_FAN_SYSTEM_1 | System Fan #1 |
    | SEMA_EAPI_ID_FAN_SYSTEM_2 | System Fan #2 |
    | SEMA_EAPI_ID_FAN_SYSTEM_3 | System Fan #3 |

  * uint32_t* Level1:

    ​		 Pointer to a buffer that receives the current temperature level (t1)

  * uint32_t* Level2:

    ​		 Pointer to a buffer that receives the current temperature level (t2)

  * uint32_t* Level3:

    ​		 Pointer to a buffer that receives the current temperature level (t3)

  * uint32_t* Level4:

    ​		 Pointer to a buffer that receives the current temperature level (t4)

<br /> 

```
uint32_t uint32_t EApiSmartFanSetPWMSetpoints(uint32_t FanID, uint32_t Level1, uint32_t Level2, uint32_t Level3, uint32_t Level4)
```

**Description**

Set PWM levels ( Range is **0 ~100** )

* Parameters:

  * uint32_t FanID:

    Select FAN ID as the parameter

    | ID                        | Description   |
    | ------------------------- | ------------- |
    | SEMA_EAPI_ID_FAN_CPU      | CPU Fan       |
    | SEMA_EAPI_ID_FAN_SYSTEM_1 | System Fan #1 |
    | SEMA_EAPI_ID_FAN_SYSTEM_2 | System Fan #2 |
    | SEMA_EAPI_ID_FAN_SYSTEM_3 | System Fan #3 |

  * uint32_t Level1:

    ​		 Configure the first level of PWM (p1)

  * uint32_t Level2:

    ​		 Configure the second level of PWM (p2)

  * uint32_t Level3:

    ​		 Configure the third level of PWM (p3)

  * uint32_t Level4:

    ​		 Configure the fourth level of PWM (p4)


<br />

```
uint32_t uint32_t EApiSmartFanGetTempSetpoints(uint32_t FanId, uint32_t* pLevel1, uint32_t* pLevel2, uint32_t* pLevel3, uint32_t* pLevel4)
```

**Description**

Get PWM levels ( Range is **0 ~100** )

* Parameters:

  * uint32_t FanID:

    Select FAN ID as the parameter

    | ID                        | Description   |
    | ------------------------- | ------------- |
    | SEMA_EAPI_ID_FAN_CPU      | CPU Fan       |
    | SEMA_EAPI_ID_FAN_SYSTEM_1 | System Fan #1 |
    | SEMA_EAPI_ID_FAN_SYSTEM_2 | System Fan #2 |
    | SEMA_EAPI_ID_FAN_SYSTEM_3 | System Fan #3 |

  * uint32_t* Level1:

    ​		 Pointer to a buffer that receives the current PWM level (p1)

  * uint32_t* Level2:

    ​		 Pointer to a buffer that receives the current PWM level (p2)

  * uint32_t* Level3:

    ​		 Pointer to a buffer that receives the current PWM level (p3)

  * uint32_t* Level4:

    ​		 Pointer to a buffer that receives the current PWM level (p4)

<br /> 

```
uint32_t uint32_t EApiSmartFanSetMode(uint32_t FanId, uint8_t pFanMode)
```

**Description**

Set FAN Mode

* Parameters:

  * uint32_t FanID:

    Select FAN ID as the parameter

    | ID                        | Description   |
    | ------------------------- | ------------- |
    | SEMA_EAPI_ID_FAN_CPU      | CPU Fan       |
    | SEMA_EAPI_ID_FAN_SYSTEM_1 | System Fan #1 |
    | SEMA_EAPI_ID_FAN_SYSTEM_2 | System Fan #2 |
    | SEMA_EAPI_ID_FAN_SYSTEM_3 | System Fan #3 |

  * uint32_t pFanMode:

     Select FAN mode as the parameter

    | FAN Mode               | Description                                                  |
    | ---------------------- | ------------------------------------------------------------ |
    | SEMA_FAN_MODE_ON       | Default speed is only refer to PWM level #4                  |
    | SEMA_FAN_MODE_OFF      | Turn Off FAN                                                 |
    | SEMA_FAN_MODE_AUTO     | it will be configured as "stepwise operation between Temperature and PWM" |
    | SEMA_FAN_MODE_SOFT_FAN | it will be configured as "Linear operation between Temperature and PWM" |



<br /> 

```
uint32_t uint32_t EApiSmartFanGetMode(uint32_t FanId, uint8_t* pFanMode)
```

**Description**

Get FAN Mode

* Parameters:

  * uint32_t FanID:

    Select FAN ID as the parameter

    | ID                        | Description   |
    | ------------------------- | ------------- |
    | SEMA_EAPI_ID_FAN_CPU      | CPU Fan       |
    | SEMA_EAPI_ID_FAN_SYSTEM_1 | System Fan #1 |
    | SEMA_EAPI_ID_FAN_SYSTEM_2 | System Fan #2 |
    | SEMA_EAPI_ID_FAN_SYSTEM_3 | System Fan #3 |

  * uint8_t* pFanMode:

     Pointer to a buffer that receives the current FAN mode

    | FAN Mode               | Description                                   |
    | ---------------------- | --------------------------------------------- |
    | SEMA_FAN_MODE_ON       | Default speed is only refer to PWM level #4   |
    | SEMA_FAN_MODE_OFF      | Turn Off FAN                                  |
    | SEMA_FAN_MODE_AUTO     | it will be configured as "stepwise operation" |
    | SEMA_FAN_MODE_SOFT_FAN | it will be configured as "Linear operation"   |




 <br />

```
uint32_t uint32_t EApiSmartFanGetTempSrc(uint32_t FanId, uint8_t* pTempSrc)
```

**Description**

Get the temperature source for the specified FAN ID. SMART FAN will be triggered by the temperature source. Only CPU and system temperature could be set as temperature source of FANs

* Parameters:

  * uint32_t FanID:

    Select FAN ID as the parameter

    | ID                        | Description   |
    | ------------------------- | ------------- |
    | SEMA_EAPI_ID_FAN_CPU      | CPU Fan       |
    | SEMA_EAPI_ID_FAN_SYSTEM_1 | System Fan #1 |
    | SEMA_EAPI_ID_FAN_SYSTEM_2 | System Fan #2 |
    | SEMA_EAPI_ID_FAN_SYSTEM_3 | System Fan #3 |

  * uint8_t* pTempSrc:

    Pointer to a buffer that receives the current tmperature source.

    | Temperature Source ID | Description                    |
    | --------------------- | ------------------------------ |
    | SEMA_FAN_TEMP_CPU     | Temperature source from CPU    |
    | SEMA_FAN_TEMP_SYS     | Temperature source from System |



 <br />

```
uint32_t uint32_t EApiSmartFanSetTempSrc(uint32_t FanId, uint8_t pTempSrc)
```

**Description**

Set the temperature source for the specified FAN ID. SMART FAN will be triggered by the temperature source. Only CPU and system temperature could be set as temperature source of FANs

* Parameters:

  * uint32_t FanID:

    Select FAN ID as the parameter

    | ID                        | Description   |
    | ------------------------- | ------------- |
    | SEMA_EAPI_ID_FAN_CPU      | CPU Fan       |
    | SEMA_EAPI_ID_FAN_SYSTEM_1 | System Fan #1 |
    | SEMA_EAPI_ID_FAN_SYSTEM_2 | System Fan #2 |
    | SEMA_EAPI_ID_FAN_SYSTEM_3 | System Fan #3 |

  * uint8_t pTempSrc:

     Select ID as the paramter

    | Temperature Source ID | Description                    |
    | --------------------- | ------------------------------ |
    | SEMA_FAN_TEMP_CPU     | Temperature source from CPU    |
    | SEMA_FAN_TEMP_SYS     | Temperature source from System |
