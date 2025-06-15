# Auto-flatpak-update - systemd Service and Timer

**1. Pull repo to download files**
- flatpak-auto-update.service
- flatpak-auto-update.timer

<br>

**2. Create user-specific systemd directory (if does not exist)**
```shell
mkdir -p ~/.config/systemd/user
```

<br>

**3. Copy or move the files to the new user-specific systemd location**
```shell
cp flatpak-auto-update.service ~/.config/systemd/user/
cp flatpak-auto-update.timer ~/.config/systemd/user/
```

<br>

**4. Reload systemd to implement changes**
```shell
systemctl --user daemon-reload
```

<br>

**5. Start and enable systemd unit**
```shell
systemctl --user enable --now flatpak-auto-update.timer
```

<br>

# Done
Flatpaks will auto-update daily after current user login.
