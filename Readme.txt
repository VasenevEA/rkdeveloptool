# rkdeveloptool

rkdeveloptool offers a straightforward method to read/write to Rockusb devices. Let's dive in.

## Compile and Install

Install libusb and libudev:
```bash
sudo apt-get install libudev-dev libusb-1.0-0-dev dh-autoreconf
```
Navigate to the root of rkdeveloptool.
Set up the build system:
```bash
aclocal
autoreconf -i
autoheader
automake --add-missing
./configure
make
```

## Usage

Get a list of commands with:
```bash
rkdeveloptool -h
```

Example:
Download kernel.img:
```bash
sudo ./rkdeveloptool db RKXXLoader.bin # Download usbplug to the device
sudo ./rkdeveloptool wl 0x8000 kernel.img # 0x8000 is the base address for the kernel partition; unit is sector
sudo ./rkdeveloptool rd # Reset the device
```
## Troubleshooting

If you face the error below:
```bash
./configure: line 4269: syntax error near unexpected token LIBUSB1,libusb-1.0' ./configure: line 4269: PKG_CHECK_MODULES(LIBUSB1,libusb-1.0)'
```

You might need to install pkg-config and libusb-1.0:
```bash
sudo apt-get install pkg-config libusb-1.0
```