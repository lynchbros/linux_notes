# Fedora Workstation Gnome Setup

## Initial Installation

1. Use Ventoy to create a bootable USB drive with the Fedora Workstation ISO.
2. Boot from the USB drive and select "Install Fedora Workstation".
3. Follow the installation prompts:
   - Choose your language and keyboard layout.
   - Select "Install to Hard Drive".
   - Choose the installation destination (your hard drive).
   - Set up your user account and password.
   - Review the installation summary and click "Begin Installation".
4. Wait for the installation to complete and then reboot your system.
5. After rebooting, log in with your user account.

## Post-Installation Setup

1. Open Software Center and remove any unwanted applications.
2. Open a terminal and run the following commands to update your system:

   ```bash
   sudo dnf -y upgrade
   sudo dnf clean all
   sudo dnf autoremove
   ```

3. Install Gnome Extensions and Tweaks:

   ```bash
   sudo dnf install -y gnome-tweaks
   sudo flatpak install com.mattjakeman.ExtensionManager
   ```

4. Configure Gnome Tweaks and Extensions:
   - Open Gnome Tweaks from the applications menu
    - Add Minimize/Maximize buttons to the title bar
    - Center New Windows
   - Open Extension Manager from the applications menu
     - Browse and install useful extensions such as:
       - Alphabetical App Grid
       - Dash to Panel
       - GSConnect (for Android phone integration)
       - Quick Settings Audio Devices Hider
       - Vitals
   - Customize the appearance, fonts, and other settings as desired

5. Configure System Settings:
   - Open Settings from the applications menu
   - Sound -> Alert Sound -> None
   - Power -> Power Button Behavior -> Power Off
   - Power -> Show Battery Percentage -> On
   - Power -> Power Saving Tab -> Automatic Screen Brightness -> Off
   - Multitasking -> Workspaces -> Workspaces on all displays
   - Appearance -> Style -> Dark
   - Apps -> Default Applications -> Web -> Chrome
   - Sharing -> Device Name -> <whatever you want>
   - Keyboard -> Keyboard Shortcuts -> View and Customize shortcuts as needed
    - Launchers -> Home Folder -> Super+E
    - Navigation -> Switch Windows -> Alt+Tab
    - Custom Shortcuts -> Add Custom Shortcut for Terminal
      - Name: Terminal
      - Command: ptyxis --new-window
      - Shortcut: Ctrl+Alt+T
  - Privacy & Security -> File History & Trash -> File History Duration -> 30 Days
  - Privacy & Security -> File History & Trash -> Automatically Empty Trash -> On
  - Privacy & Security -> File History & Trash -> Automatically Delete Temporary Files -> On
  - System -> Date & Time -> Week Day -> On
  - System -> Date & Time -> Seconds -> On

6. Install Google Chrome and VS Code from their official websites:

7. Setup Media Codec Support

  ```bash
  sudo dnf install \
  https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm \
  https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

  sudo dnf update --refresh

  sudo dnf5 install -y --allowerasing gstreamer1-plugins-base-tools gstreamer1-plugins-good-extras gstreamer1-plugins-ugly gstreamer1-plugins-bad-freeworld gstreamer1-libav gstreamer1-plugin-openh264 lame* ffmpeg libva libva-utils vdpauinfo intel-media-driver mesa-va-drivers mesa-vdpau-drivers
  ```

8. Enable HW Acceleration in Chrome:
   - Open Chrome and go to `chrome://flags`
   - Enable "Override software rendering list"
   - Relaunch Chrome
