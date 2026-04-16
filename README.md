# u7 - U7-RK3506-128+256HMI

@ $31



Rockchip RK3506G 7-Inch 1024*600 IPS Full Viewing Angle

128MB Ram

256MB SPI NAND Flash

1 x USB 2.0 Port

1 x USB OTG Port

1 x adapter cable for 5/12/24v power input

<img width="800" height="800" alt="H77bc5a1fbb104d97887a9dd94e903784L" src="https://github.com/user-attachments/assets/588b08a7-e538-45b7-970e-84e433609ae4" />

```
git clone https://github.com/markbirss/u7.git
chmod +x ./tools/linux/Linux_Upgrade_Tool/Linux_Upgrade_Tool/upgrade_tool
cd u7/buildroot/dl
7z x dl.7z.001
cd ../../

lyra@f08764082302:/build$ ./build.sh lunch
Log colors: message notice warning error fatal

Log saved at /build/output/sessions/2026-04-16_10-30-33
Pick a defconfig:

1. U7-rk3506g_buildroot_defconfig
2. rp-rk3506b_buildroot_defconfig
3. rp-rk3506g_buildroot_defconfig
4. small-rk3506gx_buildroot_defconfig
Which would you like? [1]: 1

./build.sh

./output/firmware/update-u7-rk3506g-buildroot-mipi-7-1024-600-20260411-102343.img

adb shell

modetest -M rockchip -s 74@71:1024x600
evtest

```
