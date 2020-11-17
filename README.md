# qrcode

[中文页](README_ZH.md) | English

## 1 Introduction

**qrcode** is a software package used to generate a QR code from a string. This software package is a port of **RT-Thread** based on [ricmoo/QRCode](https://github.com/ricmoo/QRCode) open source library.

### 1.1 Directory structure

| Name | Description |
| ---- | ---- |
| examples | Examples directory, and some corresponding instructions |
| inc | Header file directory |
| src | Source Code Directory |

### 1.2 License

The `qrcode` software package extends the `QRCode` software package license agreement, please see the `qrcode/LICENSE` file.

### 1.3 Dependency

- RT-Thread 3.0+

## 2. How to open qrcode

To use qrcodepackage, you need to select it in the package manager of RT-Thread. The specific path is as follows:

```shell
RT-Thread online packages
    tools packages --->
        [*] qrcode: A simple library for generating QR codes in C
            [*] Enable qrcode sample
```

- `Enable qrcode sample`: Enable QR code sample;

Then let RT-Thread's package manager automatically update, or use the `pkgs --update` command to update the package to the BSP.

## 3. Use qrcode

### Generate QR code

When using the qrcode software package, you must first define a structure to manage the QR code.

```c
QRCode qrcode;
```

Then apply for dynamic memory according to the version number to save the generated QR code,

```c
uint8_t *qrcodeBytes = (uint8_t *)rt_calloc(1, qrcode_getBufferSize(DEFAULT_QR_VERSION));
```

Finally, use the QR code generation function to generate the QR code.

```c
qrcode_initText(&qrcode, qrcodeBytes, DEFAULT_QR_VERSION, ECC_LOW, "HELLO WORLD");
```

### Print QR code

The generated two-dimensional code is dot matrix data, 8 dots constitute a Byte. The following codes can be used to display the QR code

```c
for (uint8 y = 0; y <qrcode.size; y++) {
    for (uint8 x = 0; x <qrcode.size; x++) {
        if (qrcode_getModule(&qrcode, x, y) {
            rt_kprintf("**");
        } else {
            rt_kprintf(" ");
        }
    }
    Serial.print("\n");
}
```

## 4. Demo

In this example, the QR code routine needs to be opened in the qrcode software package.

Enter the command qrcode RT-Thread in MSH, you can print out a QR code on the serial port assistant, scan it with the mobile phone code scanning software, you can see the result is RT-Thread.

![qrcode](figures/qrcode.gif)

## 5. Matters needing attention

- When generating a QR code, the higher the version used, the larger the dynamic memory that needs to be applied for.
- When scanning the QR code on the serial port assistant, pay attention to setting the serial port assistant with black characters on a white background.
- When scanning the QR code on the serial port assistant, pay attention to reducing the text display to reduce the space between *.

## 6. Contact & Thanks

* Maintenance: [qgyhd1234](https://github.com/qgyhd1234)
* Homepage: https://github.com/RT-Thread-packages/qrcode
