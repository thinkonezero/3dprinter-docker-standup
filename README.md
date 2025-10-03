# 3D Printer Docker Standup

---
This is a simple docker-compose configuration to run some 3D printer apps on a Synology NAS.

## Services

- [Spoolman](github.com/Donkie/Spoolman) - for filament inventory tracking
- [Bambu AMS Spoolman Integration](https://github.com/Rdiger-36/bambulab-ams-spoolman-filamentstatus) - for automating the filament usage tracking from a Bambu AMS to Spoolman

## Install Instructions

### Prerequisites

- Synology NAS
- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/)
- [Docker-Compose](https://docs.docker.com/compose/)

### Setup

1. Clone this project
1. Copy `sample.env` to `.env` and update variables as appropriate
1. Copy `sample.printers.json` to `${BASE_DOCKER_PATH}/amsfilament/printers/printers.json`
1. Update `printers.json` with the information from your printer
1. Run `docker-compose up -d` to start the services

| Attributes | Printer |
| ------ | ------ |
| id | Serial from Printer |
| code | AccessCode from Printer |

#### Serial Number 

- [How to find your serial number](https://wiki.bambulab.com/en/general/find-sn)

#### Access Code

To find your Bambu printer access code, navigate to the Settings menu on your printer's screen, then go to the Wireless LAN (or Wi-Fi) settings and enable the network slider. Log in to your network, and then return to the Settings menu to find an Account section, which displays a QR code. Scan this QR code with the Bambu Handy app to link your printer and obtain the access code for local network control. 
On the Printer's Screen

1. On your printer's touchscreen, tap the Settings icon. 
1. Select Wireless LAN (or Wi-Fi) from the menu.
1. Turn on the network slider and log into your Wi-Fi network. 
1. Return to the Settings menu and tap on the Account tab. 
1. You should see a QR code displayed on this screen. 

## Accessing Apps

1. Spoolman will be available at the IP Address on the `SPOOLMAN_PORT`, `http://192.168.x.x:48000`
1. AMS Integration will be available at the IP Adddress on the `BAMBUAMS_PORT`, `http://192.168.x.x:45001`

## Environment File

```plaintext
LOCALUSER=
HOSTNAME=
IP_ADDRESS=
PUID=
PGID=
LOG_FILE_NUM=5
LOG_FILE_SIZE=10m
TZ=
BASE_DOCKER_PATH=/volume1/docker
SPOOLMAN_PORT=
BAMBUAMS_PORT=
SPOOLMAN_ENDPOINT=http(s)://<spoolman_ip_address>:<spoolman_port>[/<spoolman_subfolder>]
UPDATE_INTERVAL=120000
BAMBUAMS_MODE=automatic
```

---

If this project has helped you in anyway, and you'd like to say thanks...

[![Donate](https://img.shields.io/badge/Donate-SquareCash-brightgreen.svg)](https://cash.me/$phikai)

_AFFILIATE DISCLOSURE: You can also support this project by purchasing a VPN Subscription via one of the links in this README._

---

# Disclaimer

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
