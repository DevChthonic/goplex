
![GOPLEX-5-23-2025](https://github.com/user-attachments/assets/a47cfe47-40a2-49c2-ba1e-89f62b55f555)

# goplex

A simple shell script to quickly tunnel Plex through your Raspberry Pi for local browser access.

For use when your Plex Media Server is running on a headless Pi and needs temporary local forwarding.

This issue popped up when I installed plexmediaserver to my Raspberry Pi 5 in a headless manner and then could not access the usual `https://localhost:32400/web` page. A local port forward resolved this and now I simply run `goplex` in my terminal whenever I would like to watch something on my plex server.

---

## 🔧 Features

- Port forwards Plex (default port `32400`) from your Raspberry Pi to your local machine on port `8888`.
- Quick access to Plex via `http://localhost:8888/web`.
- Automatically uses SSH to tunnel the port.
- Automatically opens Google Chrome.

---

## ⚙️ Requirements

- Raspberry Pi accessible via SSH (e.g., `dev@raspberrypi.local` or `dev@10.0.0.1` or `dev@192.168.0.1`)
- SSH credentials setup (password or key)
- Plex running and listening on port `32400` on the Pi

---

## 🚀 Usage

```bash
goplex
```
This opens a local tunnel to your Pi’s Plex server. Then just open:

```bash
http://localhost:8888/web
```
in your browser to use the Plex UI.

---

## 🛠 Script Setup

You must change the address to your pi. `username@pihostname.local`

You may change `8888` to any free port you wish if there are conflicting ports. (e.g., 2727, 3636, 4242)

The script is setup with a `6 second sleep delay` for you to enter your ssh password. You can increase this delay if it takes you longer than 6 seconds to complete the password entry. (e.g., `sleep 12`, `sleep 18`, `sleep 24`)

The script also automatically opens Google Chrome. You can delete the `open -a "Google Chrome" http://localhost:8888` line (or comment it out) if you would prefer to navigate to your new port forward manually.

---
 
## ✅ Bonus Tip

If you use SSH keys for authentication, the script will connect instantly without requiring a password.

You may make this script executable with `chmod +x goplex` and then add this script to your $PATH so that you may type `goplex` in any directory which will enable you to `goplex` from any place in your terminal.

## 📂 What This Script Does

```bash
ssh -L 8888:localhost:32400 dev@raspberrypi.local
```

GOPLEX README.md image created using textstudio.com.
