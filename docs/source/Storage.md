
### Storage Access

Support to access 1K-Bytes EEPROM on BMC device.





#### List of Sys Interface 

* To get the storage capabilities

  ```
  cat /sys/bus/platform/devices/adl-bmc-nvmem/capabilities/nvmemcap
  ```

* To read the storage area,

  ```
  hexdump /sys/bus/nvmem/devices/<nvmem index>/nvmem
  ```

  For example: **hexdump /sys/bus/nvmem/devices/nvmem544/nvmem**

* To write the storage area

  ```
  hexer /sys/bus/nvmem/devices/<nvmem index>/nvmem
  ```

  For example:**$ hexer /sys/bus/nvmem/devices/nvmem544/nvmem**

  **Note**: Hexer will open a nvmem file in editor mode. To edit the data press **r (replace**) and enter new data then press escape and **:wq** to save. Then read the same file using hexdump to check saved changes.



<br />



#### List of SEMA EAPI (Support Windows & Linux)

```
uint32_t EApiStorageCap(uint32_t Id, uint32_t* pStorageSize, uint32_t* pBlockLength)
```

**Description**

Get the capabilities of the selected storage area

* Parameters:

  * uint32_t Id:

    Select ID as the parameter

    | ID                  | Description                                            |
    | ------------------- | ------------------------------------------------------ |
    | EAPI_ID_STORAGE_STD | Standard Storage Area >=32 bytes for read/write access |

  * uint32_t* pStorageSize:

    Pointer to a buffer that receives storage area size. This parameter can be NULL if the data is not required

  * uint32_t* pBlockLength:

    Pointer to a buffer that receives the storage areas alignment/Block size. This parameter can be NULL if the data is not required. The value must be used to calculate write block alignment and size.



 <br />


```
uint32_t EApiStorageAreaRead(
        uint32_t Id,
        uint32_t nOffset,
        void* pBuffer,
        uint32_t nBufLen,
        uint32_t nByteCnt
)
```

**Description**

Read data to the selected user data area

* Parameters:

  * uint32_t Id:

    Select ID as the parameter

    | ID                  | Description                                            |
    | ------------------- | ------------------------------------------------------ |
    | EAPI_ID_STORAGE_STD | Standard Storage Area >=32 bytes for read/write access |

  * uint32_t nOffset:

     Storage area start address offset in bytes

  * void* pBuffer:

    Pointer to a buffer that receives the read data.

  * uint32_t nBufLen:

    Size, in bytes, of the buffer pointed to by the pBuffer parameter

  * uint32_t nByteCnt:

    Size, in bytes, of the information read to the buffer pointed to by the pBuffer parameter




 <br />

```
uint32_t EApiStorageAreaWrite(
        uint32_t Id,
        uint32_t nOffset,
        void* pBuffer,
        uint32_t  nByteCnt
)		
```

**Description**

Write data to the selected user data area

* Parameters:

  * uint32_t Id:

    Select ID as the parameter

    | ID                  | Description                                            |
    | ------------------- | ------------------------------------------------------ |
    | EAPI_ID_STORAGE_STD | Standard Storage Area >=32 bytes for read/write access |

  * uint32_t nOffset:

    Storage area start address offset in bytes. This value must be a multiple of *pBlockLength

  * void* pBuffer:

    Pointer to a buffer containing the data to be stored

  * uint32_t  nByteCnt:

    Size, in bytes, of the information pointed to by the pBuffer parameter
