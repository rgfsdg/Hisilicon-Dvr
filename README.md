# Hisilicon-Dvr
My journey on how Im trying to get access to a dvr

My family recently got a cheap dvr from a chinese vendor use for analog cctvs around the house. eventually the power supply for the dvr failed and i took it out to swap it. I wondered if the firmware on these are updated or even replaceable. After researching online, turns out tons of these xiongmai dvr are vulnerable to botnet attacks and remote access vulnerabilities. this got me worrying of our safety and privacy as we do use the cloud services

Now after some articles about the vulnerabilities i found that these are accessible through telnet and generic passwords. i connected to mine and instantly dropped into a root shell. Thats disturbing considering its a security device!. I wandered around until i found that you can get serial access and dump or write firmware through uboot. After getting uboot accessed i found an article explaining on how to modify the rootfs of a firmware. At that time i did not realize you could dump the firmware and modify it but i unknowingly updated and lost telnet access but in the process got my hands on a update package. now following the article the firmware is accessible if you unzip it and unzip the romfs file one more time. it is just a cramfs file that can be repackaged. after repackaging with uboot tools i managed to flash the firmware but it did not boot at all i tried the process multiple times but i couldnt get it to work. i reflashed the original firmware and gave up.

After a few months i chanced upon the board and decided to try one more time. This time i dug deeper and went into the rabbit holes of chinese forums and blogs and managed get my hands on a very old sdk for my chip and instructions [here](https://blog.csdn.net/lydstory123/article/details/141372548). using the sdk i found a prebuilt uboot and decided to flash it with the help of chatgpt. It did not go well. The board failed to boot and no output came from serial. i originally had an spi dump of the firmware after the update but now im waiting for my programmer to arrive so i can reflash the onboard spi.

This is all i know about the dvr. Please open up an issue if you are able to find any other information

My end goal is to get the camera feed over to my server via lan to zoneminder to convert into an open source setup
