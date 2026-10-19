# Pyrite

Pyrite is Fedora Silverblue image taken from ublue-os/silverblue-main for novideo (nvidia) users - currently only 16xx series and newer.
It uses negativo17 repository for its nvidia drivers.

## Variants

- **liquid-pyrite:** stock Fedora kernel + Nvidia akmods
- **volatile-pyrite:** OGC kernel + Nvidia OGC akmods

You can freely rebase between them whenever you want.

## Installation

### Switch from an existing Fedora Atomic / Universal Blue system
```
# Main: liquid-pyrite
sudo bootc switch --enforce-container-sigpolicy ghcr.io/kajzio/liquid-pyrite:latest

# OGC: volatile-pyrite
sudo bootc switch --enforce-container-sigpolicy ghcr.io/kajzio/volatile-pyrite:latest
```

### Install via ISO

Not released yet.

### Image Verification
All images are signed with Cosign. The public key is included in this repository as cosign.pub.
```
cosign verify --key cosign.pub ghcr.io/kajzio/liquid-pyrite:latest
```
### Changing Channels
Switch your system to a different release channel at any time:

### Rollback
If an update causes issues, you can roll back to the previous deployment without re-downloading anything:
```
sudo bootc rollback
systemctl reboot
```
### Building Locally
Pyrite uses Just for build automation (available by default on all Universal Blue images).

#### Container Images
```
just build                  # Base variant
```
#### ISOs
```
just build-iso              # Base variant
```
#### QCOW2 VM Images
```
just build-qcow2            # Build base QCOW2
just run-vm-qcow2           # Build and run in a VM
```
Run `just` with no arguments to see all available recipes.

### License
Apache-2.0
