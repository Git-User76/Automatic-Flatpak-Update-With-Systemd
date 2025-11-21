# Flatpak-auto-update 

Simple systemd user `service` and `timer` units for scheduling daily Flatpak updates for the current user.

---
<br>

## Installation
Run these commands as a regular user.
```shell
# Download the unit files from this GitHub repo to the current directory
wget https://raw.githubusercontent.com/Git-User76/Automatic-Flatpak-Update-With-Systemd/main/flatpak-auto-update.service
wget https://raw.githubusercontent.com/Git-User76/Automatic-Flatpak-Update-With-Systemd/main/flatpak-auto-update.timer

# Create the user-specific systemd directory (if it doesn't exist)
mkdir -p ~/.config/systemd/user

# Move the service and timer unit files to the user-specific systemd directory
mv flatpak-auto-update.service ~/.config/systemd/user/
mv flatpak-auto-update.timer ~/.config/systemd/user/

# Reload user systemd to read the new unit files
systemctl --user daemon-reload

# Start and enable timer
systemctl --user enable --now flatpak-auto-update.timer
```

---
<br>

## Verify Installation
```shell
# Check timer status:
systemctl --user status flatpak-auto-update.timer

# List upcoming timer runs
systemctl --user list-timers
```

---
<br>

## How It Works
- The timer runs daily with a randomized delay of up to 1 hour.
- Updates are performed non-interactively and only when the network is available. Missed updates (e.g., system was off) will run after the next boot.
- Flatpaks will auto-update daily after current user login.
- There is NO need for manually updating flatpaks or updating from the store.
