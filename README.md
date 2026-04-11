# u7 - U7-RK3506-128+256HMI

U7-RK3506G2-KD-12A

Rockchip Micro RK3506G Development Board 7-Inch 1024*600 IPS Full Viewing Angle 7-inch 1024*600 IPS Low Cost Labor Control

5/12/24v power input

$31

<img width="800" height="800" alt="H77bc5a1fbb104d97887a9dd94e903784L" src="https://github.com/user-attachments/assets/588b08a7-e538-45b7-970e-84e433609ae4" />


```
git clone https://github.com/markbirss/u7.git
cd u7/buildroot/dl
7z x dl.7z.001
cd ../../

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
evtest

```
