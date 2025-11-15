# gigabyte-laptop-wmi

This is an experimental kernel driver for Gigabyte GiMATE-enabled Gigabyte Gaming laptops to
interact with the embedded controller.

## Overview

Virtually all Gigabyte laptops have most of their sensor data and controls in
the embedded controller (EC), which can only be accessed through Gigabyte's
Control Center on Windows. Because it is implemented as a WMI device,
interacting with it on Linux is difficult.

This kernel driver enables interaction with the EC via WMI methods `WMBC` and `WMBD`.
The controls are made available through sysfs, while the sensor data are available through HWMON.

The objective is to eliminate the need to use "hacks" to interact with the EC,
such as calling ACPI directly from userspace (as root) or by loading `ec-sys`
to set specific bits in EC memory ourselves (see [this repository](https://github.com/jertel/p37-ec) and [this fork](https://github.com/christiansteinert/p37-ec-aero-14)).

## Model support

The following models are currently supported:

- GiMATE-enabled Gigabyte Gaming models

The following models are not supported:

- Gigabyte Gaming models (both are rebadged Clevo laptops,
  use [this driver](https://github.com/wessel-novacustom/clevo-keyboard/tree/master) instead),
  **but not GiMATE-enabled models** (which using this driver)

## GiMATE-enabled laptops support state

- Battery charge limit - working
- Fan speed modes - +/- (auto, normal, and fixed mode is working, others is ~)
- Temperature - is correct
- Fan - fixed by default, and it is working correctly

## Installation/Usage

All information for this have been moved to [INSTALL.md](INSTALL.md) and [USAGE.md](USAGE.md).
You can also check the [wiki](https://github.com/tangalbert919/gigabyte-laptop-wmi/wiki) on how to install and use this
kernel driver.
