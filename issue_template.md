<!--
    Before you create this issue,
    Have you checked if your problem 
    have been reported here? 
    https://together.jolla.com/questions/ 
    
    Or already been answered here?
    https://github.com/bitrvmpd/sailfish-santoni/issues?q=is%3Aissue+is%3Aclosed
     
    If there's isn't anything there that solves your issue, 
    continue filling this form.
-->


<!-- Name of the LOS zip -->
LineageOS build:
  > 

<!-- Name of the SailfishOS zip-->
SailfishOS build:
  > 


#### Expected behavior



#### Actual behavior



#### Steps to reproduce




---
<!-- Attachments logs, images, etc-->

<!--
    Getting the logs:
    =================
    Go to settings -> Developers Options
    And create a password, hit save.
    
    Then, got to Settings -> USB -> Default USB Mode
    And select "Always Ask".

    Connect your phone in developer mode.

    How to access?
    ==============
    Telnet:
    telnet [Your USB IP] 2323 
    
    SSH:
    ssh nemo@[Your phone's Wifi IP]
    Enter the password you've created before.
    
    Terminal App:
    Open the app in your device.

    
    After you got a shell, run these commands:
    ==========================================
    1. devel-su
    Enter the password you've created before.
    2. /usr/libexec/droid-hybris/system/bin/logcat > /home/nemo/logcat.log
    Hit ctrl+c to exit.
    3. dmesg > /home/nemo/dmesg.log
    4. journalctl > /home/nemo/journalctl.log

    Then connect your phone in MTP Mode copy those logs and upload them here.
-->

<!-- 
    If for some reason MTP is not working for you
    move them to /data/media/0 
    In a terminal run:
    1. devel-su
    Enter the password you've created before.
    2. mv /home/nemo/logcat.log /data/media/0
    3. mv /home/nemo/dmesg.log /data/media/0
    4. mv /home/nemo/journalctl.log /data/media/0
     
    Then you can access in your recovery or in Android.
-->
