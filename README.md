# OneKey Wallet Flatpak

Official [Flathub package](https://flathub.org/apps/details/so.onekey.Wallet) of [OneKey Wallet](https://onekey.so/).

You need to install and enable **PCSC daemon** to use this app.


## Install

1. [Add Flathub](https://flatpak.org/setup/) to your system.
2. Install and enable PCSC daemon.

   ```sh
   # Fedora
   sudo dnf install pcsc-lite pcsc-lite-ccid
   sudo systemctl enable --now pcscd.socket

   # Debian / Ubuntu
   sudo apt install pcscd libccid
   sudo systemctl enable --now pcscd.socket

   # Arch
   sudo pacman -S pcsclite ccid
   sudo systemctl enable --now pcscd.socket
   ```
3. Install OneKey Wallet from Flathub:

   ```sh
   flatpak install flathub so.onekey.Wallet
   ```

## Troubleshooting

If network requests fail in Flatpak, check these first:

```sh
# 1) Verify the app still has network permission
flatpak info --show-permissions so.onekey.Wallet

# 2) Check whether any local override removed network access
flatpak override --show so.onekey.Wallet

# 3) Start with Electron logs enabled and check network/TLS errors
flatpak run --env=ELECTRON_ENABLE_LOGGING=1 so.onekey.Wallet

# 4) If `network` was overridden, reset/restore network permission
flatpak override --user --share=network so.onekey.Wallet
```
