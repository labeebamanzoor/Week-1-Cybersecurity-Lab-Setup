# VirtualBox Shared Folder

The Kali terminal screenshot shows a VirtualBox shared folder mounted at `/downloads`.

## Verify the mount

Run:

```bash
findmnt -t vboxsf
```

The recorded output showed:

```text
TARGET      SOURCE     FSTYPE
/downloads  Downloads  vboxsf
```

This indicates that the host folder named `Downloads` was mounted inside Kali using the VirtualBox shared-folder filesystem.

## Configure a shared folder in VirtualBox

1. Shut down Kali before changing VM settings.
2. Open **VirtualBox Manager → select the Kali VM → Settings → Shared Folders**.
3. Add the desired Windows folder.
4. Choose a clear folder name, such as `Downloads`.
5. Enable **Auto-mount** and **Make Permanent** when available.
6. Start Kali and verify the mount with `findmnt -t vboxsf`.

If the shared folder is not accessible, VirtualBox Guest Additions may be required. On Kali, the logged-in user may also need membership in the `vboxsf` group:

```bash
sudo usermod -aG vboxsf "$USER"
```

Log out and back in (or reboot) after changing group membership.
