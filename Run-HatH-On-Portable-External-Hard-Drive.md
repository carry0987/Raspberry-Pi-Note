# Run HentaiAtHome On Portable External Hard Drive

## Install Required Tools
```sudo apt-get install screen```

```sudo apt-get install vim```

```sudo apt-get install openjdk-8-jdk```

```sudo apt-get install openjdk-8-jre```

## Auto Mount External Hard Drive
1. Use ```df -h``` command to check the disk and free space on the system
![](static/image/hath/img_1.jpg)

2. Use ```lsblk``` command to show the hard disk partition status and partition
![](static/image/hath/img_2.jpg)

3. Use ```sudo fdisk -l``` to view details of the hard drive and volume
![](static/image/hath/img_3.jpg)

   The **/dev/sda** is the external dard drive
![](static/image/hath/img_4.jpg)

4. Use ```sudo fdisk /dev/sda``` to edit the external hard drive,
first **d** and then **w** to delete the partition table and disk on the hard disk
![](static/image/hath/img_5.jpg)

5. Once again, use ```sudo fdisk /dev/sda``` to build disk partition,
   first type **n**, next type **p**, and type **1**, then press enter twice, if it shows ```contains a ext4 signature``` message,
   just type **Y** to countine, finally type **w** to build partition on the hard disk
![](static/image/hath/img_6.jpg)

6. Use ```sudo mkfs.ext4 /dev/sda1``` to format the partition into **Ext4**
![](static/image/hath/img_7.jpg)

7. Use ```sudo mkdir /media/hd``` to create a folder,
   then the external hard drive will be mounted here
![](static/image/hath/img_8.jpg)

8. Use ```sudo chmod 777 /media/hd``` to give it permission
![](static/image/hath/img_9.jpg)

9. Use ```ls -lh /dev/disk/by-uuid``` can see the UUID of the hard disk and partition
![](static/image/hath/img_10.jpg)

10. Use ```sudo blkid /dev/sda1``` to list UUIDs of external hard drive partitions
![](static/image/hath/img_11.jpg)

11. Remember the UUID of external hard drive,
then use ```sudo vim /etc/fstab``` to edit **fstab** to let raspberry pi automatically mount the external hard drive after boot
![](static/image/hath/img_12.jpg)

    you will see this:
![](static/image/hath/img_13.jpg)
    then press **```i```**, the ```-- INSERT --``` will display at buttom, it means now this file can be edit
![](static/image/hath/img_14.jpg)
    type ```UUID=YOURUUID /media/hd ext4 defaults 0      2```
![](static/image/hath/img_15.jpg)
    then press **```ESC```**, you will see that ```-- INSERT --``` disappear
![](static/image/hath/img_16.jpg)
    now type **```:wq```**, then press enter
![](static/image/hath/img_17.jpg)

12. Use ```sudo reboot``` to reboot the device,
and then use ```df -h``` to check if the external hard drive has been mounted
![](static/image/hath/img_18.jpg)

13. Now use ```sudo mkdir /media/hd/hath``` to create a folder,
and use ```sudo chmod 777 /media/hd/hath``` to give it permission
![](static/image/hath/img_19.jpg)

14. Use ```cd /media/hd/hath``` to go to ```hath``` folder,
then use ```sudo wget https://repo.e-hentai.org/hath/HentaiAtHome_1.6.0.zip``` to download the H@H
![](static/image/hath/img_20.jpg)

15. Use ```sudo unzip HentaiAtHome_1.6.0.zip``` to unzip H@H files
![](static/image/hath/img_21.jpg)

16. Use ```screen``` to start terminal in background
![](static/image/hath/img_22.jpg)
    you will see this
![](static/image/hath/img_23.jpg)
    just press enter to start
![](static/image/hath/img_24.jpg)

17. Use ```sudo java -jar HentaiAtHome.jar``` to start H@H
![](static/image/hath/img_25.jpg)

18. Enter your Client ID and Client Key
![](static/image/hath/img_26.jpg)

19. Running
![](static/image/hath/img_27.jpg)

20. Now press **Ctrl + A** and then press **D** to detach H@H
![](static/image/hath/img_28.jpg)

21. Finish
![](static/image/hath/img_29.jpg)