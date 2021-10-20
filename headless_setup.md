# Headless Set Up

_Markdown wrote with : https://dillinger.io/_
## Installation

Source: https://www.youtube.com/watch?v=G59JsJ04t14

#### Plug in the SD card in the laptop

#### Get the Rasperry Pi Imager or Ubuntu  https://www.raspberrypi.com/software

#### Double click on the .dmg file from the dowloads folder. 
Do not drag the icon in the folder, just double click in it (just in case you want to update it in the future)

#### Extract and reinsert the SD card 

Open Terminal, Type 


```
cd /Volumes/boot
```

Then 
```
touch ssh 
```
(touch creates a new file)


We are going to create and format a new file directly with the nano text editor in the mac 

```
nano wpa_supplicant.conf
```

In the file add: 

```
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
scan_ssid=1
ssid="YOUR-NETWORK-NAME"
psk="Your WiFi password"
}
```

Close the terminal window and eject the SD card. Then unplug

---

SD card back in the pi. Wait 2 minutes. 

Open a new terminal: 

```
ssh pi@raspberrypi.local (or ssh pi@raspberrypi)
```

If it's the first time accessing it use raspberry as the password 

Change the password: 
```
passwd
```
Make sure to take a note 

Now we want to configure the pi in a way in which the VNC client can act as a remote desktop 
```
sudo raspi-config
```

Go to 3. Interface options > VNC > Yes 

Now we need to configure the VNC client
```
sudo nano /root/.vnc/config.d/vncserver-x11
```

If there is a line that for the authentication update it to match the one below otherwise just add it: 
```
Authentication=VncAuth
```

You can enter the same password as above for the VNC service 
```
sudo vncpasswd -service
```

```
sudo reboot
```

Now open spotliht, select screen sharing app, in connect to add: 
```
raspberrypi.local
```




