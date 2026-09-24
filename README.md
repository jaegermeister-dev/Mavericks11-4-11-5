OS X Mavericks for the 15-inch Mid-2015 MacBook Pro
This project adds OS X Mavericks 10.9.5 build 13F34 support to the 15-inch Mid-2015 MacBook Pro.
Supported models
- MacBookPro11,5 — fully hardware-tested
  - Intel Iris Pro
  - AMD Radeon R9 M370X
- MacBookPro11,4 — experimental
  - Receives the shared non-GPU hardware fixes.
  - No GPU configuration changes are made.
  - Physical hardware testing is still required.
Other Mac models, including 13-inch MacBook Pros, are not supported.
What you need
- A USB drive large enough for the Mavericks installer.
- The original, unmodified Mavericks DMG.
- Mavericks-USB-Patcher.zip
- A separate partition or disk for Mavericks.
The original DMG must match this SHA-256:
0845d2ab27586604d01b99520a0f3ed10813021d10043a54799f55f099d8dd60
The DMG filename does not matter. The patcher automatically checks every .dmg file in its folder and selects the matching original image.
Creating the installer USB
Warning: The selected USB drive will be completely erased, including every partition and file on it.

1. Create a new folder.
2. Put the original Mavericks DMG and Mavericks-USB-Patcher.zip inside it.
3. Double-click Mavericks-USB-Patcher.zip.
4. Confirm that the extracted Patch-Mavericks-Installer-USB.sh and the DMG are in the same folder.
5. Open Terminal.
6. Type bash followed by a space.
7. Drag Patch-Mavericks-Installer-USB.sh into the Terminal window.
8. Press Return.
9. Enter the administrator password when requested.
10. The patcher displays the attached physical USB drives as a numbered list.
11. Enter the number of the USB you want to use.
12. Carefully verify the displayed device.
13. Type yes and press Return.
The script then automatically:
- Verifies the original Mavericks DMG.
- Completely erases the selected USB.
- Creates the official stock Mavericks installer.
- Applies only the required installer bootability changes.
- Preserves the stock installer kernelcache and boot.efi.
- Copies the post-install patcher and its sealed hardware-support files onto the USB.
- Verifies and ejects the completed USB.
Installing Mavericks
1. Restart the Mac while holding Option/Alt.
2. Select the Mavericks installer USB.
3. Open Disk Utility from the installer if the Mavericks destination needs to be erased or formatted.
4. Format only the intended Mavericks destination as Mac OS Extended (Journaled).
5. Do not modify or use Recovery HD.
6. Close Disk Utility and install Mavericks normally.
7. When installation finishes, restart while holding Option/Alt again.
8. Boot the Mavericks installer USB a second time.
9. Open Terminal from the installer’s Utilities menu.
10. Run:
/post-install-patches.sh
No second USB is required. Live output is saved to a timestamped log under /Mavericks115-Logs on the installer USB.
11. Wait for the patcher to report SUCCESS.
12. Restart and select the installed Mavericks system.
Confirmed working on MacBookPro11,5
- OS X Mavericks 10.9.5 build 13F34
- Intel Iris Pro graphics acceleration
- AMD Radeon R9 M370X graphics acceleration
- Internal display
- External displays
- Native Wi-Fi menus, network discovery, authentication, DHCP and internet access
- Native Bluetooth menus, discovery, pairing and on/off controls
- Internal keyboard
- Keyboard backlight controls
- Brightness, volume and other function keys
- Trackpad movement and clicking
- Tap to click and secondary click
- Scrolling and tracking-speed controls
- Multi-touch gestures, zoom and rotation
- Mission Control, Launchpad and desktop gestures
- Force Touch feedback
- FaceTime camera
- Internal speakers
- Internal microphone
- Laptop HDMI video and audio
- Thunderbolt-dock display and audio
- Laptop headphone output
- Laptop headset-microphone input
- Dock headphone output
- Dock microphone input
- Thunderbolt-dock Ethernet
- USB storage and installer booting
- Internal SSD boot and storage
Wi-Fi uses the normal Mavericks menus and System Preferences. No third-party network utility is required.
Limited or untested
- Bluetooth discovery, pairing and connection are confirmed. Bluetooth audio was only tested with modern AirPods and was not reliable enough for a definitive compatibility claim.
- MacBookPro11,4 has not been tested on physical hardware.
- Exhaustive automatic GPU-switching scenarios have not been tested.
- Long-duration GPU, thermal, fan and power-management stress testing has not been performed.
- Time Machine and Time Machine restoration are untested.
- Recovery HD is unmodified, unsupported and should not be used.
- Games and modern application backports are outside this project.
No hardware subsystem is currently confirmed broken on the tested MacBookPro11,5 installation.
Scope and safety
The post-install patcher does not modify:
- Recovery HD
- NVRAM
- The disk partition layout
- Unrelated operating systems
- Unrelated system files
