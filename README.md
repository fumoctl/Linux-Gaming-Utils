# Linux-Gaming-Utils
## Increase the Open File Limit (Crucial for Steam/Wine)
Edit the limits file ```/etc/security/limits.conf```

Add these lines at the bottom (replace yourusername with your actual login):

```
yourusername soft nofile 1048576
yourusername hard nofile 1048576
```
Reboot for this to take effect. You can verify it after rebooting by running ```ulimit -n``` in a terminal; it should show the new high number.
## increase vm.max_map_count
edit the "/etc/sysctl.conf" file, add "vm.max_map_count=2147483642" to the bottom and then run:
```
sudo sysctl -p
```
## gamescope (for upscaling most games including VNs while maintaining aspect ratio) (fullscreen, fit to screen (not fill or stretch) using fsr)
```
gamescope -f -S fit -F fsr -- %command%
```
## lsfg-vk (for frame generation, create a profile manually or with the UI and call it with this environment variable)
```
LSFG_PROCESS=<profile-name>
```
# Game examples i use
## The Finals
```
LSFG_PROCESS=performance PROTON_USE_NTSYNC=1 mangohud %command%
```
## Old VNs (ej. Majikoi)
```
gamescope -f -S fit -F fsr -- %command%
```
