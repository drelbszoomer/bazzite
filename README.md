# DrelbsOS

An Atari-approved, Spectrum-certified, disgustingly personal variant of [Bazzite](https://github.com/ublue-os/bazzite).

Notably it

- Is Nvidia/GNOME focused only.
- Removes all Steam Deck and non-desktop-related packages, patched variants, firmwares, and etc. This includes removing Bazzite/Valve patched versions of system components like Pipewire, Mesa, Mutter, etc where the patches are really only for Steam Deck usage, and using (more up to date, usually) straight Fedora versions of these packages instead.
- Does not install Steam/Lutris/Wine and the many assorted support apps as system components - these are all available as flatpaks, which are strongly recommended.
- No system components also means ~all of the system-level multilib munging and surgery Bazzite does is gone.
- Then several disgustingly personal packages added in:
  - zsh standard
  - cdemu bits installed by default
  - misc bits and bobs

Pretty much the only things kept from Bazzite are the use of the fsync kernel, the use of Bazzite/UBlue's kmod and container build infra, a few generally-useful addons, and the opinions around what third party repos to pull Nvidia drivers from.

DrelbsOS is indebted to the amazing work Bazzite has done to make building UBlue/Fedora OSTree variants ridiculously simple.

## Image builds

New images are built and published automatically every Wednesday 10:05 AM EST

##  Image signature

Pubkey for the signed images published by this repo is `cosign.pub` in the root of this repo.

## Secure Boot

Secure boot is supported with the Bazzite custom key. The pub key can be found in the root of their repository [here](https://github.com/ublue-os/bazzite/blob/main/secure_boot.der).

If you'd like to enroll this key prior to installation or rebase, download the key and run the following:

```bash
sudo mokutil --timeout -1
sudo mokutil --import secure_boot.der
```

For users already on a Universal Blue image, you may instead run `ujust enroll-secure-boot-key`.

If asked for a password, use `universalblue`.
