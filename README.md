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
