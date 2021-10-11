# Surface-laptop-3-thermald
A step by step guide onto managing thermals in sl3

# Step 1
Move all the `thermal-conf.xml` and `thermal-cpu-dev` to `/etc/thermald/`. In order to move it, you have to `rm -rf` default conf and use `gedit` to create new files and paste the content in it.

# Step 2
Install 40-surface-power.rules to `/usr/lib/udev/rules.d/` using gedit.
Install 50-surface.conf to `/etc/sysctl.d/` using gedit.

# Step 3 
Install thermald.service to `/lib/systemd/system/` and overwrite the old one.
 Maybe install to `/usr/lib/systemd/system/` too. Both using gedit.
-`systemctl daemon-reload`
-`systemctl restart udev`
-`systemctl restart thermald`

# Side Note
If your laptop is plugged into ac, thermald wont work due to the excess voltage that is coming from the ac. In retrospect of that, the processor will get super hot when doing strenous task. In order to fix this problem, go to `settings>power>` and select `Power Saver`. For some reason thermald wont work issue only occurs when it is plugged into AC. The ubuntu version that i tested with is 21.04. Im not sure about other version of ubuntu.
