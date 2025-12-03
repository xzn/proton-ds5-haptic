For haptic in Stellar Blade and Spider-Man Remastered/Miles Morales:

- 0001-mmdevapi-setupapi-HACK-Set-MMDevices-properties-in-s.patch
- 0002-setupapi-Set-DeviceContainers-registry-values-when-c.patch
- 0003-xaudio2-faudio-Implement-taking-device-ids-to-create.patch

For haptic when controller is hotplugged:

- 0004-pulse-mmdevapi-Add-support-for-hotplugged-audio-devi.patch
- 0005-mmdevapi-Call-registered-IMMNotificationClients-when.patch

Note:

If you are patching on top of wine-staging, the following patch need to be excluded:

- winepulse-PulseAudio_Support/0001-winepulse.drv-Use-a-separate-mainloop-and-ctx-for-pu.patch
