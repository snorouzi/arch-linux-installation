# flclash – Cross‑Platform Proxy GUI Client

flclash is a cross‑platform graphical client for managing proxy connections based on Clash cores. It supports multiple proxy cores (Clash, Clash Meta, etc.) and protocols (SS, SSr, VMess, VLESS, Trojan, etc.), making it a versatile tool for bypassing internet censorship and protecting online privacy.

> **ℹ️ Note:** flclash is available in the Arch User Repository (AUR). This guide uses `yay` as the AUR helper.

---

## Table of Contents

- [flclash – Cross‑Platform Proxy GUI Client](#flclash--crossplatform-proxy-gui-client)
  - [Table of Contents](#table-of-contents)
  - [1. Features Overview](#1-features-overview)
  - [2. Installation](#2-installation)
  - [3. Launching flclash](#3-launching-flclash)
  - [4. Basic Configuration](#4-basic-configuration)
    - [4.1. First Run & Core Setup](#41-first-run--core-setup)
    - [4.2. Adding a Server / Importing Subscription](#42-adding-a-server--importing-subscription)
      - [Via Subscription URL (Recommended)](#via-subscription-url-recommended)
      - [Manually Adding a Server](#manually-adding-a-server)
    - [4.3. Setting System Proxy](#43-setting-system-proxy)
    - [4.4. Enabling TUN Mode (Global Proxy)](#44-enabling-tun-mode-global-proxy)
  - [5. Updating flclash](#5-updating-flclash)
  - [6. Uninstalling flclash](#6-uninstalling-flclash)
  - [7. Troubleshooting](#7-troubleshooting)
  - [8. References](#8-references)

---

## 1. Features Overview

| Feature                      | Description                                                    |
| ---------------------------- | -------------------------------------------------------------- |
| **Multi‑Core Support**       | Supports Clash, Clash Meta, and other cores (selectable).      |
| **Protocol Support**         | SS, SSr, VMess, VLESS, Trojan, SOCKS5, HTTP, and more.         |
| **TUN Mode**                 | One‑click global transparent proxy (system‑wide).              |
| **Routing**                  | Flexible rule‑based routing (bypass LAN, CN IP, custom rules). |
| **Subscription Management**  | Import/update server lists via subscription URLs.              |
| **System Proxy Integration** | Auto‑configure system proxy settings (PAC or global).          |
| **Cross‑Platform**           | Works on Windows, Linux, and macOS.                            |
| **Modern UI**                | Clean and intuitive user interface.                            |

---

## 2. Installation

The AUR provides the package `flclash-bin` (pre‑compiled binary). This guide uses the binary package for faster installation.

```bash
yay -S flclash-bin
```

> **💡 Tip:** The AUR page recommends the `-bin` version for Arch Linux systems. If you prefer building from source, check the AUR for `flclash` (without `-bin`).

---

## 3. Launching flclash

- **From the application menu** – look for “flclash” in your desktop environment’s launcher.
- **From the terminal** – run:

  ```bash
  flclash
  ```

> **ℹ️ Note:** On first launch, flclash may need to download the selected core (Clash, Clash Meta, etc.). Ensure you have an internet connection.

---

## 4. Basic Configuration

### 4.1. First Run & Core Setup

1. Launch flclash.
2. If a “Core not found” warning appears, go to **Settings → Core**.
3. Select a core (e.g., **Clash Meta** or **Clash**) and click **Download**. Wait for the download to complete.

### 4.2. Adding a Server / Importing Subscription

#### Via Subscription URL (Recommended)

1. Click the **Proxy** tab → **Profiles** → **Add**.
2. Paste your subscription URL (provided by your proxy service).
3. Click **OK**, then click the **Update** button to refresh the subscription.
4. The server list will populate with available nodes.

#### Manually Adding a Server

1. Click the **Proxy** tab → **Proxies** → **Add**.
2. Choose protocol (SS, SSr, VMess, VLESS, Trojan, etc.).
3. Fill in the server address, port, password/UUID, encryption, etc.
4. Click **Save**.

### 4.3. Setting System Proxy

After adding a server, select a node from the list, then click the **System Proxy** button in the bottom‑left corner to enable system‑wide proxy.

### 4.4. Enabling TUN Mode (Global Proxy)

TUN Mode allows all system traffic (including terminal, games, and non‑HTTP applications) to be routed through the proxy.

1. Ensure you have selected a server node.
2. Click the **TUN** button in the bottom‑left corner.
3. You may be prompted for your **sudo password** (TUN mode requires root privileges on Linux).
4. Once enabled, the TUN button should turn **green**.

> **⚠️ Important:** TUN Mode is not stable on all Linux distributions, and some users report network issues after enabling/disabling it. To revert, click the **TUN** button again to disable it. If your network remains down, restart your network manager:
>
> ```bash
> sudo systemctl restart NetworkManager
> ```

---

## 5. Updating flclash

```bash
yay -Syu flclash-bin
```

To update the proxy core itself, use **Settings → Core → Check Core Updates** inside the application.

---

## 6. Uninstalling flclash

```bash
yay -Rns flclash-bin
```

Remove configuration files and cores:

```bash
rm -rf ~/.config/flclash
rm -rf ~/.local/share/flclash
```

---

## 7. Troubleshooting

| Problem                                                 | Solution                                                                                                               |
| ------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **`flclash: command not found`**                        | flclash is not installed. Run `yay -S flclash-bin`.                                                                      |
| **Core not found / “The Clash core file was not found”** | Go to **Settings → Core**, select a core, and click **Download**.                                         |
| **TUN Mode does not work / network goes down**          | TUN mode is not fully stable on Linux. Try running flclash as root: `sudo flclash` or use **System Proxy** mode instead. |
| **No internet after disabling TUN mode**                | Restart your network manager: `sudo systemctl restart NetworkManager`.                                                 |
| **Subscription fails to update**                        | Check your subscription URL. If it uses HTTPS, ensure your system time is correct.                                     |
| **Unable to connect (proxy not working)**               | Verify that the server node is online (right‑click → **Test Latency**). Ensure the correct proxy mode is enabled.    |
| **GUI not appearing after launch**                      | flclash runs in the system tray. Look for its icon in your desktop’s notification area.                                 |

---

## 8. References

- **Official GitHub repository:** [chen08209/FlClash](https://github.com/chen08209/FlClash)
- **Download page:** [flclash.cc/en/download](https://flclash.cc/en/download)
- **AUR package:** [flclash-bin](https://aur.archlinux.org/packages/flclash-bin)

---

Your flclash setup is now ready to manage your proxy connections with a user‑friendly GUI. Enjoy safer and more open access to the web!