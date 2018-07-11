# lpc21isp_py
Simple python wrapper to use LPC21ISP programming interface. Works with python 2.7 or later

## Cloning / Downloading

In order to clone this module, either download its zip package directly from github or run the following command:

    git clone --recursive https://github.com/lnls-dig/lpc21isp_py

If you already cloned without the `--recursive` option, run instead:

    cd lpc21isp_py/
    git submodule update --init --recursive

Go into lpc21isp submodule folder and compile it:

    cd lpc21isp/
    make


## Usage

In order to use this module in a python script simply import it, create a `LPC21ISP` object and call the `program(<bin_path>)` function:

```python
from lpc21isp import *

lpc = LPC21ISP('/dev/ttyUSB0')
lpc.program('test.bin')
```

If the programming is successful, the function will return `True` value. If any errors happen, it will just return `False` or raise a `CalledProcessError`from the subproccess module

## Known problems

1. The error handling in the module is really bad. The only exception raised are from the subprocess module and are related with problems when trying to call the `lpc21isp` binary itself.
All the other problems (no serial port found, could not synchronize with device, protected memory regions, etc) are squashed into the `False` return value and not treated.
