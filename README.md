# Linux-Gaming-Utils
## Increase the Open File Limit (Crucial for Steam/Wine)
Edit the limits file ```/etc/security/limits.conf```

Add these lines at the bottom (* means for all users):

```
* soft nofile 1048576
* hard nofile 1048576
```
sometimes systemd overrides this so try doing it like this: edit ```/etc/systemd/user.conf```
add the following to the end
```
DefaultLimitNOFILE=1048576:1048576
```

Reboot for this to take effect. You can verify it after rebooting by running ```ulimit -n``` in a terminal; it should show the new high number.
## increase vm.max_map_count
edit the ```/etc/sysctl.conf``` file, add ```vm.max_map_count=2147483642``` to the bottom and then run:
```
sudo sysctl -p
```
systemd might also fuck this up so try this instead:
make a new file called ```/etc/sysctl.d/99-max-map-count.conf```
add this to it
```
vm.max_map_count=2147483642
```
reboot 

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
## Mortal Kombat 9 (as non steam game)
```
STEAM_COMPAT_DATA_PATH="/home/fumo/Games/steam/steamapps/compatdata/MK9" gamescope -w 1920 -h 1080 -b -F fsr -- %command%
```
## Majikoi S (as non steam game(with translation patch))
```
LANG=ja_JP.UTF-8 STEAM_COMPAT_DATA_PATH="/home/fumo/Games/steam/steamapps/compatdata/Majikoi S" gamescope -f -S fit -F fsr -- %command%
```
