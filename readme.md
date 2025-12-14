#### Warning

My code for audio devices hotplug support is kinda off, will likely break in weird ways if multiple programs using audio are running at the same time (when same wineserver and prefix). Looking at other possible solutions for now.

---

For haptic in Stellar Blade and Spider-Man Remastered/Miles Morales:

- 0001-mmdevapi-setupapi-HACK-Set-MMDevices-properties-in-s.patch
- 0002-setupapi-Set-DeviceContainers-registry-values-when-c.patch
- 0003-xaudio2-faudio-Implement-taking-device-ids-to-create.patch

For haptic when controller is hotplugged:

- 0004-winepulse-mmdevapi-Add-support-for-hotplugged-audio-.patch
- 0005-mmdevapi-Call-registered-IMMNotificationClients-when.patch

For haptic in Death Stranding Director's Cut and God of War Ragnarok:

- 0006-setupapi-SetupDiGetDeviceRegistryProperty-now-return.patch
- 0007-mmdevapi-Add-PROTON_MMDEV_FAKE_EXCLUSIVE-envvar-for-.patch

For DSDC crash when controller hotplug patched:

- 0008-faudio-xaudio2-Partially-rewrite-asserts-to-error-ha.patch

For DSDC crash when PulseAudio server is disconnected/restarted, and other misc changes:

- 0009-mmdevapi-faudio-xaudio2-Delay-create-thread-in-case-.patch

Note:

If you are patching on top of wine-staging, the following patch need to be excluded:

- winepulse-PulseAudio_Support/0001-winepulse.drv-Use-a-separate-mainloop-and-ctx-for-pu.patch

Change log:

- 2025-12-13 Delete device ids from device containers when removing devices
- 2025-12-12 Tries to fix crash when pulse server is disconnected
- 2025-12-11 Potential logic error in hotplugged audio devices support
- 2025-12-11 Rebased patches
- 2025-12-10 Misc changes attempt to the same fix
- 2025-12-10 Delay thread creation as an attempt to fix xaudio2_9.dll load crash.
- 2025-12-09 Fix wrong lock location in mmdevcol init
- 2025-12-09 Do not create thread in mmdev init (for hotplugged audio device support)
- 2025-12-09 Cleanup mmdev init and names
- 2025-12-08 Add support for God of War Ragnarok.
- 2025-12-08 Fix crash introduced in previous change when initializing xaudio2.
- 2025-12-07 Attempt to fix crash when selected audio device in Death Stranding is disconnected.
- 2025-12-07 Lower case for GUIDs strings when possible.
- 2025-12-07 Maybe fix a hang on startup init in mmdevapi audio device hotplug support.
- 2025-12-07 Add haptic support for DSDC. Need `PROTON_MMDEV_FAKE_EXCLUSIVE=1` set in envvar.
- 2025-12-04 Fix crash in Death Stranding Director's Cut when switching BB sound device (haptic still doesn't work)
- 2025-12-03 Fix potential deadlock in my pulse backend devices update routine (no builds uploaded to release for now)
- 2025-12-03 Fix controllers speakers not playing in Spider-Man
- 2025-12-02 Initial separated patch files

Fixed known issues (hopefully):

- ~~faudio/xaudio2 will crash if the audio device currently in use is disconnected. Working on a fix.~~
- ~~Sometimes after upgrading a prefix, you may encounter access violation error in winepulse.drv, it shouldn't happen in a fresh prefix. (Let me know if it does.)~~
