Sure! Here's an improved version of your README with added details in the overview and a new key features section. I've also used unique GitHub text fonts and improved readability.

---

# Surface Laptop 3 Thermald

A step-by-step guide to managing thermals on Surface Laptop 3.

## Overview

The default Linux thermal management on Surface devices often relies on the CPU driver rather than the operating system itself. This guide provides a custom solution to manage the thermals more effectively, ensuring better performance and longevity of your Surface Laptop 3.

## Key Features

- **Custom Thermal Configuration**: Replace default thermal configuration files with custom ones for better thermal management.
- **Udev and Sysctl Rules**: Implement specific rules to optimize power management.
- **Service Updates**: Overwrite and update the thermald service to ensure it functions correctly.

## Step 1: Configure Thermal Files

Move all the `thermal-conf.xml` and `thermal-cpu-dev` files to `/etc/thermald/`.

1. **Remove the default configuration files**:
    ```bash
    sudo rm -rf /etc/thermald/*
    ```

2. **Create new configuration files and paste the content using `gedit`**:
    ```bash
    sudo gedit /etc/thermald/thermal-conf.xml
    sudo gedit /etc/thermald/thermal-cpu-dev
    ```

## Step 2: Install Udev and Sysctl Rules

1. **Install `40-surface-power.rules` to `/usr/lib/udev/rules.d/` using `gedit`**:
    ```bash
    sudo gedit /usr/lib/udev/rules.d/40-surface-power.rules
    ```

2. **Install `50-surface.conf` to `/etc/sysctl.d/` using `gedit`**:
    ```bash
    sudo gedit /etc/sysctl.d/50-surface.conf
    ```

## Step 3: Update Thermald Service

1. **Install `thermald.service` to `/lib/systemd/system/` and optionally to `/usr/lib/systemd/system/`, overwriting the old one**:
    ```bash
    sudo gedit /lib/systemd/system/thermald.service
    sudo gedit /usr/lib/systemd/system/thermald.service
    ```

2. **Reload the system daemon and restart services**:
    ```bash
    sudo systemctl daemon-reload
    sudo systemctl restart udev
    sudo systemctl restart thermald
    ```

## Side Note

If your laptop is plugged into AC, thermald may not work due to excess voltage. This can cause the processor to overheat during strenuous tasks. To mitigate this:

1. Go to `Settings > Power`.
2. Select `Power Saver`.

This issue was observed on Ubuntu 21.04. Other versions may not have this problem.
