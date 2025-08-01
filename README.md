# 🦆 duckpapa: Raspberry Pi HID Keyboard Gadget

Turn your **Raspberry Pi Zero W** into a powerful USB Rubber Ducky-style keyboard injector.  
`duckpapa` allows you to send automated keystrokes to a target system — all from a web interface!

---
## 🚀 Features

- 📱 Web UI built with Flask to trigger payloads
- 🔐 USB HID injection via `/dev/hidg0`
- ⚙️ Simple Bash setup for HID gadget mode
- 🌍 Optional Ngrok support for remote access
---

```bash
sudo bash setup_hid.sh
sudo python3 test.py
```
---

## 📁 Project Structure

| File/Folder         | Description                                 |
|---------------------|---------------------------------------------|
| `duckpapa.py`       | Main Python script to run HID payloads      |
| `webui.py`          | Flask Web UI for launching payloads         |
| `setup_hid.sh`      | One-time USB HID setup script               |
| `payloads/`         | Folder for Ducky-style text payloads        |

---

``` bash
sudo apt install python3-Flask
chmod +x duckpapa.py
sudo python3 webui.py

```
Access on:
📡 http://localhost:8080 or your Pi’s IP

Issue

 * Serving Flask app 'webui'
 * Debug mode: off
Address already in use
Port 8080 is in use by another program. Either identify and stop that program, or start the server with a different port.

```bash
sudo lsof -i :8080
```

COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
python3 1289 root    3u  IPv4  24703      0t0  TCP *:http-alt (LISTEN)
python3 1289 root    5u  IPv4  24703      0t0  TCP *:http-alt (LISTEN)

``` bash
sudo kill -9 PID
```
exp :- sudo kill -9 1289

## Optional
Ngrok Setup
``` bash
wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-stable-linux-arm.zip
unzip ngrok-stable-linux-arm.zip
sudo mv ngrok /usr/local/bin/
```
```bash
ngrok config add-authtoken <YOUR_AUTH_TOKEN>
```
```bash
ngrok http 8080
```
Test a Payload
``` bash
sudo python3 duckpapa.py /payloads/notepad.txt
```
![Screenshot_26-7-2025_13038_192 168 247 90](https://github.com/user-attachments/assets/a67ab291-e7f0-4570-ad9b-daeb1ea33ec4)
