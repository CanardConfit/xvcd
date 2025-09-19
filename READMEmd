# XVCD for FT2232C/H

This is a daemon that listens to "xilinx_xvc" (xilinx virtual cable) traffic and operates JTAG over an FTDI in bitbang mode.

This version is hardcoded to use an FTDI cable with an FT2232C/H chip. It does not use MPSSE but rather bitbang mode. It uses ftdi_write_async which might not be available on your platform. You can use the (much slower) non-async version instead.

Have fun!

# Usage

```bash
usage: ./bin/xvcd [-v] [-V vendor] [-P product] [-S serial] [-I index] [-i interface] [-f frequency] [-p port] [-D device]

          -v: verbosity, increase verbosity by adding more v's
          -V: vendor ID, use to select the desired FTDI device if multiple on host. (default = 0x0403)
          -P: product ID, use to select the desired FTDI device if multiple on host. (default = 0x6010)
          -S: serial number, use to select the desired FTDI device if multiple devices with same vendor
              and product IDs on host. 'lsusb -v' can be used to find the serial numbers.
          -I: USB index, use to select the desired FTDI device if multiple devices with same vendor
              and product IDs on host. Can be used instead of -S but -S is more definitive. (default = 0)
          -i: interface, select which 'port' on the selected device to use if multiple port device. (default = 0)
          -f: frequency in Hz, force TCK frequency. If set to 0, set from settck commands sent by client. (default = 0)
          -D: device ID, use to select FT chip. Can be: FT2232C ; FT2232H (default = FT2232C)
          -p: TCP port, TCP port to listen for connections from client (default = 2542)
```

# Debug to work with your card

- Use multiple `-v` to increase verbosity.
- Change interface, because sometime the JTAG is not on the `port A`. Check the reference manual of your card.
- Check your chip model, supported/tested are FT2232C and FT2232H!

# Cards

## Digilent Nexys Video

Has a FT2232H. The JTAG is connected to the `port B`, so the command example is: `/bin/xvcd -D FT2232H -i 1`
