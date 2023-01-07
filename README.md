# Gaming in Docker

![](./overlay/usr/share/backgrounds/docker-box.png)

All credits to https://github.com/Steam-Headless/docker-steam-headless
This project was made for personal-use only, but all contributions are welcome via PRs.

The goal is to have single-docker image endpoint for retro and some-modern gaming through Moonlight (https://github.com/moonlight-stream) with no multi-client support.

## Changes from original project (docker-steam-headless):
- Ubuntu 22.04 based
- Added RetroArch via PPA
- Migrated to new Sunshine branch (from https://github.com/LizardByte/Sunshine)
- Added all mesa packages
- Deleted: SSH/dind
- No Host X server support

---
## Installation:

- [Cloning and building an image]

```
git clone https://github.com/QuaiGoner/docker-box && cd docker-box && docker build -t docker-box . && docker image prune -f

#Change /mnt/Games mountpoint to your likings in compose file

docker compose up -d

```

---
## TODO:
- More refactoring and plug&play
	- **Closing applications from Moonlight** - starting is working, but not closing (Same issue here: https://github.com/Steam-Headless/docker-steam-headless/issues/23)
	- Make image more lightweight with package trimming
- **Test HW Acceleration of Sunshine encoding** - seems to be working, but vainfo doesnt give anything, needs proper testing on all GPU vendors
	- AMD
	- NVIDIA
	- Intel
- **Test 3D HW Acceleration in games**
	- AMD
	- NVIDIA
	- Intel
- Github workflows
	- Build and publish latest image
	- Dockerfile testing
	- Shell testing

## Long-distance TODO:
- **Rendering application window only (Wayland?)**
- EmulationStation integrated?
- Auto-scanning of /mnt/Games
- Add most-used cores & assets to image (probably already in the image just need to fix the paths in RA)
- Different images for different GPUs?
- Create virtual application windows dimensions based on the client (Resolution/HDR, now its hardcoded)