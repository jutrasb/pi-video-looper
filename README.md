# Pi Video Looper

A set of scripts to allow the Raspberry Pi lite operating system to automatically mount USB mass storage devices and play videos using VLC media player.

Based on information found at https://github.com/term7/RaspberryPi-VLC_Videolooper

## Prerequisites

1. Update the operating system:
	```
	sudo apt-get update && sudo apt-get upgrade -y
	```

1. Install required packages:
	```
	sudo apt-get install git exfat-fuse exfatprogs vlc -y
	```

1. Clone this repository.
	```
	git clone https://github.com/jutrasb/pi-video-looper.git
	```

## Installation

1. Install `udev-media-automount` from [here](https://github.com/Ferk/udev-media-automount). After installation, USB mass storage devices will automatically be mounted to the `/media` folder.
1. Copy the VLC autoplay service `autoplay.service` from this repository to `/lib/systemd/system/autoplay.service`.
	```
	sudo cp ~/pi-video-looper/files/autoplay.service /lib/systemd/system/autoplay.service
	```
1. Create the `scripts` folder.
	```
	mkdir ~/scripts
	```
1. Copy the autoplay script `autoplay.sh` from this repository to `~/scripts/autoplay.sh`.
	```
	cp ~/pi-video-looper/files/autoplay.sh ~/scripts/autoplay.sh
	```

1. Make the autoplay script executable:
	```
	sudo chmod +x ~/scripts/autoplay.sh
	```

1. Enable the VLC autoplay service
	```
	sudo systemctl enable autoplay.service
	```
1. Attach a USB mass storage device and ensure it is mounted to `/media`
1. Reboot the Pi.
	```
	sudo reboot
	```
