# kodi-remote

A repo to keep my custom Kodi (v18+)/LibreELEC remote control setup (Sony 
RMT-D109A.)

## Usage

Copy the repo's `storage/` directory to `/storage/` on the target LibreELEC box, restart Kodi.

## Setting up key codes

- Stop kodi and eventlircd `systemctl stop eventlircd && systemctl stop kodi`
- Display the codes `ir-keytable -t` and press keys
- Add the codes to `/storage/.config/rc_keymaps/my_remote`
- Reload the keytable `ir-keytable -c -w /storage/.config/rc_keymaps/my_remote`
- Restart Kodi

## Debugging
- Stop Kodi and eventlircd
- Check if the keypresses are recognized with `ir-keytable -t`
- Check if they also show up when `irw` is running
- Check if the action from `Lircmap.xml` matches `remote.xml`
- Enable debug logging in kodi

## Additional resources

- https://kodi.wiki/view/Window_IDs
- https://kodi.wiki/view/Keymap
- https://wiki.libreelec.tv/infrared_remotes
- https://gist.github.com/unforgiven512/0c232f4112b63021a8e0df6eedfb2ff3
- `irrecord -l | grep ^KEY` for a list of supported keys

## Notes

`/storage/.kodi/userdata/keymaps/remote.xml` overlays `/usr/share/kodi/system/keymaps/remote.xml` and `/storage/.kodi/userdata/Lircmap.xml` overlays `/usr/share/kodi/system/Lircmap.xml`
