# Run HentaiAtHome On Portable External Hard Drive

## Install Required Tools
```sudo apt-get install screen```

```sudo apt-get install vim```

```sudo apt-get install openjdk-8-jdk```

```sudo apt-get install openjdk-8-jre```

## Auto Mount External Hard Drive
1. Use ```df -h``` command to check the disk and free space on the system
![](https://i.imgur.com/wLQf4Ey.jpg)

2. Use ```lsblk``` command to show the hard disk partition status and partition
![](https://i.imgur.com/F6ue8aH.jpg)

3. Use ```sudo fdisk -l``` to view details of the hard drive and volume
![](https://i.imgur.com/CVj4KL2.jpg)

   The **/dev/sda** is the external dard drive
![](https://i.imgur.com/zqXQtRT.jpg)

4. Use ```sudo fdisk /dev/sda``` to edit the external hard drive,
first **d** and then **w** to delete the partition table and disk on the hard disk
![](https://i.imgur.com/NWrnQMM.jpg)

5. Once again, use ```sudo fdisk /dev/sda``` to build disk partition,
   first type **n**, next type **p**, and type **1**, then press enter twice, if it shows ```contains a ext4 signature``` message,
   just type **Y** to countine, finally type **w** to build partition on the hard disk
![](https://i.imgur.com/e6b5rOB.jpg)

6. Use ```sudo mkfs.ext4 /dev/sda1``` to format the partition into **Ext4**
![](https://i.imgur.com/bBm3gv4.jpg)

7. Use ```sudo mkdir /media/hd``` to create a folder,
   then the external hard drive will be mounted here
![](https://i.imgur.com/XbVNLHa.jpg)

8. Use ```sudo chmod 777 /media/hd``` to give it permission
![](https://i.imgur.com/ddsg5WE.jpg)

9. Use ```ls -lh /dev/disk/by-uuid``` can see the UUID of the hard disk and partition
![](https://i.imgur.com/K4SAadO.jpg)

10. Use ```sudo blkid /dev/sda1``` to list UUIDs of external hard drive partitions
![](https://i.imgur.com/gpQpcB5.jpg)

11. Remember the UUID of external hard drive,
then use ```sudo vim /etc/fstab``` to edit **fstab** to let raspberry pi automatically mount the external hard drive after boot
![](https://i.imgur.com/nIbZX2h.jpg)

    you will see this:
![](https://i.imgur.com/NPrOMi6.jpg)
    then press **```i```**, the ```-- INSERT --``` will display at buttom, it means now this file can be edit
![](https://i.imgur.com/37grKIa.jpg)
    type ```UUID=YOURUUID /media/hd ext4 defaults 0      2```
![](https://i.imgur.com/S9WIV9u.jpg)
    then press **```ESC```**, you will see that ```-- INSERT --``` disappear
![](https://i.imgur.com/9cOyIyI.jpg)
    now type **```:wq```**, then press enter
![](https://i.imgur.com/AYTiNcu.jpg)

12. Use ```sudo reboot``` to reboot the device,
and then use ```df -h``` to check if the external hard drive has been mounted
![](https://i.imgur.com/mvvWtYJ.jpg)

13. Now use ```sudo mkdir /media/hd/hath``` to create a folder,
and use ```sudo chmod 777 /media/hd/hath``` to give it permission
![](https://i.imgur.com/cZJCLtC.jpg)

14. Use ```cd /media/hd/hath``` to go to ```hath``` folder,
then use ```sudo wget https://repo.e-hentai.org/hath/HentaiAtHome_1.4.2.zip``` to download the H@H
![](https://i.imgur.com/8JAlGBj.jpg)

15. Use ```sudo unzip HentaiAtHome_1.4.2.zip``` to unzip H@H files
![](https://i.imgur.com/0uxKpOV.jpg)

16. Use ```screen``` to start terminal in background
![](https://i.imgur.com/SuqmsOo.jpg)
    you will see this
![](https://i.imgur.com/ZblOG2U.jpg)
    just press enter to start
![](https://i.imgur.com/4jQ7ky9.jpg)

17. Use ```sudo java -jar HentaiAtHome.jar``` to start H@H
![](https://i.imgur.com/3tH381x.jpg)

18. Enter your Client ID and Client Key
![](https://i.imgur.com/QfSWyRw.jpg)

19. Running
![](https://i.imgur.com/lIkFnnU.jpg)

20. Now press **Ctrl + A** and then press **D** to detach H@H
![](https://i.imgur.com/Aasj0mG.jpg)

21. Finish
![](https://i.imgur.com/DtDIy8s.jpg)