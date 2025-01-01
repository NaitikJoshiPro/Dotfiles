# Disclaimer
Some commands in this guide, such as direct package installation and configuration copy commands, might not work as expected. This could be due to differences in configuration directory paths, variations in package names across distributions, or packages being outdated at the time of installation. Please review and adapt the commands according to your system's requirements. Also use San Fransico Pro "SF Pro" Font from Apple in your system to get a better MACOS look.

# Linux System Setup Instructions

## Step 1: Update and Upgrade
Boot into a fresh Linux system and run the following commands:
```bash
sudo apt update
sudo apt upgrade -y
```

## Step 2: Install Basic Utilities
Install essential tools for development and system management:
```bash
sudo apt install git curl wget unzip -y
```

## Step 3: Install Alacritty (or Check Availability)
Before installing Alacritty, check if it is available in your distro's repositories:
```bash
apt search alacritty
```
If available, install it directly. If not, follow these steps to build and install it from source:

1. **Install Required Dependencies**
   Ensure you have the necessary tools installed to build Alacritty:
   ```bash
   sudo apt install cmake pkg-config libfreetype6-dev libfontconfig1-dev libxcb-xfixes0-dev libxkbcommon-dev python3 -y
   ```

2. **Clone the Alacritty Repository**
   ```bash
   git clone https://github.com/alacritty/alacritty.git
   cd alacritty
   ```

3. **Build Alacritty**
   Use `cargo` (Rust's package manager) to build Alacritty:
   ```bash
   cargo build --release
   ```

4. **Install Alacritty**
   Copy the built binary to a location in your system's PATH:
   ```bash
   sudo cp target/release/alacritty /usr/local/bin
   ```

5. **Set Up Desktop Entry**
   To integrate Alacritty with your system's application launcher:
   ```bash
   sudo cp extra/alacritty.desktop /usr/share/applications/
   ```
   Update the `Exec` path in the `.desktop` file if necessary.

6. **Verify Installation**
   Run `alacritty` from your terminal to confirm that it was installed successfully.

## Step 4: Install Additional Packages
A `packages.txt` file is included in this repository. It lists the necessary packages for this setup. Package names may vary between Linux distributions, so use your discretion to install the appropriate ones. For example:
```bash
sudo apt install $(cat packages.txt)
```
*Note: For non-Debian-based distros, replace `apt` with your package manager (e.g., `pacman`, `dnf`, or `zypper`).*

## Step 5: Configure Polybar
Polybar is a customizable status bar for Linux desktops. To set it up:

1. **Install Polybar**
   Ensure Polybar is installed using the `packages.txt` file. If it's not installed, you can build it from source by following the official Polybar documentation.

2. **Clone Your Polybar Configuration**
   Use your preferred method to fetch your Polybar configuration files. For example:
   ```bash
   git clone https://github.com/yourusername/dotfiles.git ~/dotfiles
   ```
   Replace `yourusername` with your GitHub username.

3. **Copy Configuration Files**
   Copy the Polybar configuration files to the appropriate directory:
   ```bash
   mkdir -p ~/.config/polybar
   cp ~/dotfiles/polybar/* ~/.config/polybar/
   ```

4. **Edit Configuration**
   Open the `config` file in your editor of choice to customize Polybar:
   ```bash
   nano ~/.config/polybar/config
   ```
   Adjust the settings, modules, and colors to fit your preferences.

5. **Launch Polybar**
   Test your configuration by running:
   ```bash
   ~/.config/polybar/launch.sh
   ```
   Ensure the `launch.sh` script is executable. If not, set the appropriate permissions:
   ```bash
   chmod +x ~/.config/polybar/launch.sh
   ```

6. **Resources**
   - Official Polybar documentation: [https://github.com/polybar/polybar](https://github.com/polybar/polybar)
   - Community themes and configurations: [Polybar Wiki](https://github.com/polybar/polybar/wiki)

## Future Enhancements

1. **Centralized Command Center**
   - The planned command center will function as a unified search and execution tool, similar to macOS Spotlight.
   - Users will be able to search for files, launch applications, and execute commands efficiently from a single interface.
   - Future updates will include integration with system notifications and user-defined shortcuts for enhanced productivity.

2. **Polybar Improvements**
   - Additional modules and functionality will be added to Polybar, including but not limited to:
     - System monitoring (e.g., CPU, RAM, and network usage).
     - Custom widgets for weather, cryptocurrency prices, and calendar integration.
     - Interactive elements like volume control and media playback.
   - Configurations will be modular, allowing users to enable or disable features easily.

Feel free to customize these instructions based on your Linux distribution and preferences.
