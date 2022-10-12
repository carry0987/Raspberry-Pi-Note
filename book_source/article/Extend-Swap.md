# Enabling & Increasing Raspberry Pi Swap

> **Note: Due to RAM limitations on the Raspberry Pi 3 and earlier, we now recommend ALL users use Neblio with a Raspberry Pi 4. Any Raspberry Pi 4 model should work, the models with more RAM are more future-proof for running Neblio.**

Users of Neblio who stake on Raspberry Pis earlier than the Raspberry Pi 3 (such as the Original Raspberry Pi, Raspberry Pi Zero, and potentially the Raspberry Pi 2) may benefit from a significant increase in performance by enabling and/or increasing the size of the Raspberry Pi's swap file.

To enable the Raspberry Pi swap file and set it to a size of 1 GB (1024 MB), run the following commands on the Raspberry Pi in a terminal window:

## 1. Temporarily Stop Swap
```bash
sudo dphys-swapfile swapoff
```

## 2. Modify the size of the swap
As root, edit the file /etc/dphys-swapfile and modify the variable CONF_SWAPSIZE to 1024:
```bash
CONF_SWAPSIZE=1024
```
Using a command such as:
```bash
sudo nano /etc/dphys-swapfile
```

## 3. Initialize Swap File
```bash
sudo dphys-swapfile setup
```

## 4. Start Swap
```bash
sudo dphys-swapfile swapon
```
