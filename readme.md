For haptic in Stellar Blade and Spider-Man Remastered/Miles Morales:

- 0001-mmdevapi-setupapi-HACK-Set-MMDevices-properties-in-s.patch
- 0002-setupapi-Set-DeviceContainers-registry-values-when-c.patch
- 0003-xaudio2-faudio-Implement-taking-device-ids-to-create.patch

For haptic when controller is hotplugged:

- 0004-pulse-mmdevapi-Add-support-for-hotplugged-audio-devi.patch
- 0005-mmdevapi-Call-registered-IMMNotificationClients-when.patch

For Death Stranding Director's Cut:

- 0006-setupapi-SetupDiGetDeviceRegistryProperty-now-return.patch
- 0007-mmdevapi-Add-PROTON_MMDEV_FAKE_EXCLUSIVE-envvar-for-.patch

Note:

If you are patching on top of wine-staging, the following patch need to be excluded:

- winepulse-PulseAudio_Support/0001-winepulse.drv-Use-a-separate-mainloop-and-ctx-for-pu.patch

Change log:

- 2025-12-07 Attempt to fix crash when selected audio device in Death Stranding is disconnected.
- 2025-12-07 Lower case for GUIDs strings when possible.
- 2025-12-07 Maybe fix a hang on startup init in mmdevapi audio device hotplug support.
- 2025-12-07 Add haptic support for DSDC. Need `PROTON_MMDEV_FAKE_EXCLUSIVE=1` set in envvar.
- 2025-12-04 Fix crash in Death Stranding Director's Cut when switching BB sound device (haptic still doesn't work)
- 2025-12-03 Fix potential deadlock in my pulse backend devices update routine (no builds uploaded to release for now)
- 2025-12-03 Fix controllers speakers not playing in Spider-Man
- 2025-12-02 Initial separated patch files

Known issues:

- faudio/xaudio2 will crash if the audio device currently in use is disconnected. Working on a fix.

Fixed known issues (hopefully):

- Sometimes after upgrading a prefix, you may encounter access violation error in winepulse.drv, it shouldn't happen in a fresh prefix. (Let me know if it does.)
