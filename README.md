# SequoiaOptiplex7010
EFI for Sequoia on Optiplex7010

OpenCore 0.8.8

i7 3770 - iUHD4000
8GB RAM
64GB SATA SSD

### works:
pretty much everything except unmapped usb ports -> but those will work after mapping

### does not work:
i don't use a dgpu or a wlan/bluetooth adapter so I didn't add kexts/drivers for those but that can be resolved easily
drm because unsupported igpus are broken under new macos

### notes:
may require usb port mapping

does not use opencanopy

graphics acceleration requires OCLP patch but that's just a single click install since I disabled SIP and AMFI and set csr-active-config to 03080000

### differences between bigsur and sequoia:
no longer need boot-arg to disable AMFI -> replaced with a kext (AMFIPass.kext)

new macos versions dropped avx2.0 support so booting will result in kernel panic -> "libsystem.8.dylib: no such file or directory" -> resolution is to use CryptexFixup.kext that gets injected in the macOS installer (will need to reinstall macOS if installed without CryptexFixup)
