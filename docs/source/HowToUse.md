### How to use SEMA Utility


1. After installed Windows SEMA 4.0 (please refer to here to gude you how to install). please open **Command Prompt** and go to this path:**C:\Windows\System32\cmd.exe** to execute SEMA utility.


![image-20200212153937452](HowToUse.assets/image-20200212153937452.png)

2. please use **semautil.exe -h** to make you understand how more easily to use.

![image-20200212154404990](HowToUse.assets/image-20200212154404990.png)

   #### Here is some examples:

   * BIOS version:  Enter the command: **semautil.exe /i get_bd_info 4** on Command Prompt Window
     ![image-20200212155019743](HowToUse.assets/image-20200212155019743-1581946908287.png)

   * Boot counter: Enter the command: **semautil.exe /d get_value 2**
     ![image-20200212155230867](HowToUse.assets/image-20200212155230867.png)


   * Watchdog capability :  Enter the command: **semautil.exe /w get_cap** on Command Prompt Window
     ![image-20200212155747252](HowToUse.assets/image-20200212155747252.png)
