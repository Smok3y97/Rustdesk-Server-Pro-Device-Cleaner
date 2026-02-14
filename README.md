# Rustdesk-Server-Pro-Device-Cleaner

![Python](https://img.shields.io/badge/Python-3.x-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Status-Production%20Ready-success)

A Python script to automate the maintenance of **RustDesk Server Pro**. It solves the critical issue of **license slot exhaustion** caused by inactive devices or one-time "Quick Support" sessions.

## 👨‍💻 Background & Origin Story

> **"Built by a SysAdmin, for SysAdmins."**

I am a System Integrator, not a professional software developer. I created this tool because we faced a massive issue with our RustDesk license limit in a production environment.

* **⚡ Vibe-Coding:** This script was created using **AI-Assisted Development** (Google Gemini / Google Antigravity).
* **🏭 Battle-Tested:** Despite its AI origins, this script is currently running successfully in our live production environment, keeping our license slots clean.
* **🤝 Open Source:** I am sharing this so others don't have to pay for license upgrades just because of "dead" clients. If you are a dev, feel free to submit Pull Requests to clean up the code!

---

## 🛑 The Problem

In RustDesk Server Pro, every connected device consumes a license slot. This includes:
1.  **Quick Support Clients:** Customers you helped once (e.g., via the "Run Only" client).
2.  **Old Devices:** Laptops or PCs that haven't been online for months.

These devices remain in your server list as "ungrouped" or inactive entries, permanently blocking a license slot. The RustDesk API does not allow deleting a device directly; it **must be disabled first**, making manual cleanup tedious.

*Reference:* [RustDesk Server Pro Discussion #182](https://github.com/rustdesk/rustdesk-server-pro/discussions/182)

## 🚀 The Solution

This script automates the entire cleanup workflow:
1.  **Filter:** Finds devices that are ungrouped OR offline for X days.
2.  **Disable:** Sends the disable command to the API.
3.  **Delete:** Deletes the device to free up the license.

---

## 📥 Installation

You can install the script either by cloning the repository (recommended for updates) or by downloading the single file directly.

### Prerequisites
Ensure you have Python 3 and the `requests` library installed.

~~~bash
# Debian / Ubuntu
sudo apt update && sudo apt install python3 python3-pip
pip3 install requests
~~~

### Option A: Clone Repository (Recommended)
Best if you want to keep the script updated easily via `git pull`.

~~~bash
git clone https://github.com/Smok3y97/Rustdesk-Server-Pro-Device-Cleaner.git
cd Rustdesk-Server-Pro-Device-Cleaner
~~~

### Option B: Single File Download (Quick Setup)
Best for quick deployment on a server without downloading git history.

~~~bash
wget https://raw.githubusercontent.com/Smok3y97/Rustdesk-Server-Pro-Device-Cleaner/main/rustdesk_cleaner.py
chmod +x rustdesk_cleaner.py
~~~

### 🚀 Run
To start the script in simulation mode (Dry Run):

~~~bash
python3 rustdesk_cleaner.py delete
~~~

> **⚠️ Important:** Before running the script, open `rustdesk_cleaner.py` and set your `API_URL` and `API_TOKEN` at the top of the file!
