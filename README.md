OS X Mavericks for the 15-inch Mid-2015 MacBook Pro
This project adds support for running OS X Mavericks 10.9.5 build 13F34 on the 15-inch Mid-2015 MacBook Pro.
Supported models
MacBookPro11,5 — primary tested model
- Intel Iris Pro
- AMD Radeon R9 M370X
- Fully hardware-tested with this project
MacBookPro11,4 — experimental
- Receives the shared non-GPU hardware fixes.
- No GPU configuration changes are made.
- Physical hardware testing is still required.
Other Mac models, including 13-inch MacBook Pros, are not supported.
Confirmed working on MacBookPro11,5
Graphics and displays
- Intel Iris Pro graphics acceleration
- AMD Radeon R9 M370X graphics acceleration
- Internal display
- External displays
Networking and Bluetooth
- Native Wi-Fi menus
- Wi-Fi network discovery
- Wi-Fi authentication, DHCP and internet access
- Native Bluetooth menus
- Bluetooth discovery, pairing and connection
- Bluetooth on/off controls
- Thunderbolt-dock Ethernet
Wi-Fi uses the normal Mavericks menus and System Preferences. No third-party network utility is required.
Input devices
- Internal keyboard
- Keyboard backlight controls
- Brightness, volume and other function keys
- Trackpad movement and clicking
- Tap to click and secondary click
- Scrolling and tracking-speed controls
- Multi-touch gestures
- Zoom and rotation
- Mission Control, Launchpad and desktop gestures
- Force Touch feedback
Camera and audio
- FaceTime camera
- Internal speakers
- Internal microphone
- Laptop HDMI video and audio
- Thunderbolt-dock display and audio
- Laptop headphone output
- Laptop headset-microphone input
- Dock headphone output
- Dock microphone input
Storage and USB
- Internal SSD boot and storage
- USB storage
- USB installer booting
No hardware subsystem is currently confirmed broken on the tested MacBookPro11,5 installation.
Limited or untested
- Bluetooth discovery, pairing and connection are confirmed. Bluetooth audio was only tested with modern AirPods and was not reliable enough for a definitive compatibility claim.
- MacBookPro11,4 has not been tested on physical hardware.
- Exhaustive automatic GPU-switching scenarios have not been tested.
- Long-duration GPU, thermal, fan and power-management stress testing has not been performed.
- Time Machine and Time Machine restoration are untested.
- Recovery HD is unmodified, unsupported and should not be used.
- Games and modern application backports are outside the scope of this project.
Requirements
You will need:
- A USB drive large enough for the Mavericks installer
- The original, unmodified Mavericks installer DMG
- Mavericks-USB-Patcher.zip
- A separate partition or disk on which to install Mavericks
Obtaining the Mavericks DMG
Do not use a random Mavericks ISO or DMG. The required image must be built from Apple’s original Mavericks recovery installer.
On a Mac, open Terminal and run:
mkdir -p "$HOME/Desktop/MavericksDownload"
cd "$HOME/Desktop/MavericksDownload"

curl -fL "https://mavericksforever.com/get.sh" -o get.sh
/bin/sh get.sh
The script obtains temporary authorization from Apple, downloads the original Mavericks InstallESD.dmg directly from Apple’s servers, verifies it and creates:
InstallMacOSXMavericks.dmg
Verify the completed image:
shasum -a 256 InstallMacOSXMavericks.dmg
The required SHA-256 is:
0845d2ab27586604d01b99520a0f3ed10813021d10043a54799f55f099d8dd60
The filename does not matter. The USB patcher checks every .dmg file in its folder and automatically selects the image matching this hash.
Creating the installer USB
Warning: The selected USB drive will be completely erased. Every partition and file on it will be destroyed.

1. Create a new folder.
2. Place these two files inside it:
   - The original Mavericks DMG
   - Mavericks-USB-Patcher.zip
3. Double-click Mavericks-USB-Patcher.zip.
4. Confirm that the extracted Patch-Mavericks-Installer-USB.sh and the Mavericks DMG are in the same folder.
5. Open Terminal.
6. Type bash followed by a space.
7. Drag Patch-Mavericks-Installer-USB.sh into the Terminal window.
8. Press Return.
9. Enter your administrator password when requested.
10. The patcher displays all attached physical USB drives as a numbered list.
11. Enter the number corresponding to the USB drive you want to use.
12. Carefully verify the displayed device information.
13. Type:
yes
14. Press Return.
The script then automatically:
- Verifies the original Mavericks DMG
- Completely erases the selected USB
- Creates the official stock Mavericks installer
- Applies only the required installer bootability changes
- Preserves the stock installer kernelcache and boot.efi
- Copies the offline post-install patcher and its sealed hardware-support files onto the USB
- Verifies the completed installer
- Safely ejects the USB
Installing Mavericks
1. Restart the Mac while holding Option (⌥).
2. Select the Mavericks installer USB.
3. If necessary, open Disk Utility from the installer.
4. Select only the intended Mavericks destination.
5. Format it as:
Mac OS Extended (Journaled)
6. Do not modify or use Recovery HD.
7. Close Disk Utility and install Mavericks normally.
Applying the post-install patches
After the Mavericks installation finishes:
1. Restart while holding Option (⌥) again.
2. Boot the Mavericks installer USB a second time.
3. Open Terminal from the installer’s Utilities menu.
4. Run:
/post-install-patches.sh
No second USB is required. Live output is also saved to a timestamped log under:
/Mavericks115-Logs
5. Wait for the patcher to report SUCCESS.
6. Restart the Mac.
7. Select the installed Mavericks system.
Scope and safety
The post-install patcher does not modify:
- Recovery HD
- NVRAM
- The disk partition layout
- Unrelated operating systems
- Unrelated system files
