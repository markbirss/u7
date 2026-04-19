# U7-RK3506-128+256HMI
Rockchip RK3506G 7-Inch 1024*600 IPS Full Viewing Angle

@ $31

Feature | Working | Notes  |
|:--|:--|:--|
| WiFi | Yes | AP6212A |
| BLE | Still todo | missing UART and kernel modules ? |
| I2C Touch | Yes | goodix-ts |
| 1024x600 Display | Yes | 7inch IPS |
| Portrait Mode | Yes | fbcon=rotate:1  |
| On screen keyboard | Yes | fbkeyboard |
| USB Networking | Yes | 192.168.123.100 via USB 2.0 OTG Port |
| ADB | Yes | via USB 2.0 OTG Port |
| Serial Console | Yes | UART @ 115200 |
| USB Storage | Yes | USB 2.0 for rootfs |
| SPI Nand Flash | Yes | 256MB for startup |
| Power Input | Yes | 5/12/24v DC Power Input |


<img width="800" height="800" alt="H77bc5a1fbb104d97887a9dd94e903784L" src="https://github.com/user-attachments/assets/588b08a7-e538-45b7-970e-84e433609ae4" />

Changing bootargs fbcon rotate will rotate the display framebuffer

```
nano ./kernel-6.1/arch/arm/boot/dts/rp-rk3506b-board.dtsi

bootargs = "earlycon=uart8250,mmio32,0xff0a0000 console=tty1 console=ttyFIQ0 fbcon=rotate:1 
```


```
git clone -b usb-rootfs https://github.com/markbirss/u7.git
chmod +x ./u7/tools/linux/Linux_Upgrade_Tool/Linux_Upgrade_Tool/upgrade_tool
cd u7/buildroot/dl
7z x dl.7z.001
cd ../../

nano ./kernel-6.1/arch/arm/boot/dts/rp-rk3506b-board.dtsi
#change root= to /dev/sda1 for Armbian and /dev/sda3 for Ubuntu 24.04.x USB

bootargs = "earlycon=uart8250,mmio32,0xff0a0000 console=tty1 console=ttyFIQ0 root=/dev/sda3 rootfstype=ext4 rootwait snd_aloop.index=7 snd_aloop.use_raw_jiffies=1";

./build.sh lunch
Log colors: message notice warning error fatal

Log saved at /build/output/sessions/2026-04-11_10-32-00
Pick a defconfig:

1. U7-rk3506g_buildroot_defconfig
2. rp-rk3506b_buildroot_defconfig
3. rp-rk3506g_buildroot_defconfig
4. small-rk3506gx_buildroot_defconfig
5. u7-rk3506g_buildroot_ext4_defconfig
Which would you like? [1]:  5

./build.sh

/build/output/firmware/update-u7-rk3506g-buildroot-mipi-7-1024-600-20260411-102343.img

adb shell

modetest -M rockchip -s 74@71:1024x600

Onscreen framebuffer keyboard in Meshtastic Green (0x67EA94)

https://github.com/i-can-penguin/fbkeyboard
```

<img width="600" height="1024" alt="keyboard" src="https://github.com/user-attachments/assets/3bd5718b-1ec1-4f16-b498-2ca0e1e07325" />


```
/lib/systemd/system/keyboard.service
[Unit]
Description=Display Orientation Daemon
After=network-online.target

[Service]
Type=oneshot
ExecStart=/usr/bin/keyboard.sh
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target

/usr/bin/keyboard.sh
#!/bin/sh
/home/lyra/fbkeyboard/fbkeyboard -f /usr/share/fonts/truetype/noto/NotoMono-Regular.ttf -r 1 &
exit 0


evtest
No device specified, trying to scan all of /dev/input/event*
Available devices:
/dev/input/event0:      goodix-ts
/dev/input/event1:      gpio_event
/dev/input/event2:      bt-powerkey
/dev/input/event3:      adc-keys
/dev/input/event4:      fbkeyboard
Select the device event number [0-4]: 

Test suite for Linux framebuffer
https://github.com/markbirss/fb-test-app

fbgrab linux framebuffer screenshot utility.
https://github.com/markbirss/fbgrab

fbgrab screen.png
```
