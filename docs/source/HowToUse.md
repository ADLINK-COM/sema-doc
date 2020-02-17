### How to use SEMA Utility


1. After installed Windows SEMA 4.0 (please refer to here to gude you how to install). please open **Command Prompt** and go to this path:**C:\Windows\System32\cmd.exe** to execute SEMA utility.
<img src="source/HowToUseSEMA.assets/image-20200212153937452.png" alt="image-20200212153937452" style="zoom:80%;" />



2. please use **semautil.exe -h** to make you understand how more easily to use.
   <img src="source/HowToUseSEMA.assets/image-20200212154404990.png" alt="image-20200212154404990" style="zoom:80%;" />



   #### Here is some examples:

   * BIOS version:  Enter the command: **semautil.exe /i get_bd_info 4** on Command Prompt Window
     <img src="source/HowToUseSEMA.assets/image-20200212155019743.png" alt="image-20200212155019743" style="zoom:80%;" />

   * Boot counter: Enter the command: **semautil.exe /d get_value 2**
     <img src="source/HowToUseSEMA.assets/image-20200212155230867.png" style="zoom:80%;" />




   * Watchdog capability :  Enter the command: **semautil.exe /w get_cap** on Command Prompt Window
     <img src="source/HowToUseSEMA.assets/image-20200212155747252.png" style="zoom:80%;" />
