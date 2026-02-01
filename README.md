# 3D Printer Docker Standup

This is a docker-compose configuration to run 3D printer management tools on a Synology NAS.

## 🚀 Services

| Service | Description |
| :--- | :--- |
| [Spoolman](https://github.com/Donkie/Spoolman) | Filament inventory tracking for your 3D printer collection. |
| [Bambu AMS Integration](https://github.com/Rdiger-36/bambulab-ams-spoolman-filamentstatus) | Automates filament usage tracking from a Bambu AMS to Spoolman. |

## 📋 Prerequisites

- Synology NAS (DSM 7.x recommended)
- [Git](https://git-scm.com/) installed via SynoCommunity
- [Docker / Container Manager](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## 🛠️ Setup

1. **Clone the project**:
   ```bash
   git clone https://github.com/phikai/3dprinter-docker-standup.git
   ```
2. **Environment Configuration**:
   - Copy `sample.env` to `.env` and update the variables.
   - Copy `sample.printers.json` to `${BASE_DOCKER_PATH}/amsfilament/printers/printers.json`.
3. **Printer Configuration**:
   - Update `printers.json` with your printer's Serial Number and Access Code.
4. **Deploy**:
   ```bash
   docker compose up -d
   ```

### 🔍 Finding Your Printer Details

| Attribute | Source |
| :--- | :--- |
| **Serial Number** | Found in the printer settings or [Bambu Wiki](https://wiki.bambulab.com/en/general/find-sn). |
| **Access Code** | Found in the printer's Network/Account settings on the touchscreen. |

#### How to find the Access Code:
1. Tap the **Settings** icon on the touchscreen.
2. Select **Wireless LAN (or Wi-Fi)** and ensure you are connected.
3. Tap the **Account** tab.
4. The Access Code (and a QR code) will be displayed here.

## 🌐 Accessing Apps

| App | Default URL |
| :--- | :--- |
| **Spoolman** | `http://<NAS_IP>:${SPOOLMAN_PORT}` |
| **AMS Integration** | `http://<NAS_IP>:${BAMBUAMS_PORT}` |

## ⚙️ Environment Variables

A full list of variables is available in the `sample.env` file. Key variables include:
- `BASE_DOCKER_PATH`: The root directory for container data (e.g., `/volume1/docker`).
- `PUID/PGID`: Your local user/group IDs (find these by running `id` via SSH).
- `TZ`: Your timezone (e.g., `America/New_York`).

---

If this project has helped you, please consider supporting my work!

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/G2G71SUNID)

---

# Disclaimer

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED. IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY.