# OpenClaw Setup Guide for Android 
---

## What You’re Building

By the end of this guide, your Android phone will:

- Run OpenClaw locally
- Act as a 24/7 AI agent
- Be controllable from a web dashboard
- Operate without a PC or cloud server

---

## Requirements

Make sure you have:

- Android phone (Android 10 or above recommended)
- Stable internet connection
- Gemini API key (from Google AI Studio)
- Termux installed from F-Droid (not Play Store)

---

## Step 1: Install Termux

1. Go to **F-Droid.org**
2. Download and install **F-Droid**
3. Search for **Termux**
4. Install Termux
5. Open the Termux app

---

## Commands

```
pkg update && pkg upgrade -y

```
## install proot-distro
```
pkg install proot-distro

```

## install ubuntu
```
proot-distro install ubuntu

```

## login ubuntu
```
proot-distro login ubuntu

```
## Update system
```
apt update && apt upgrade -y

```

## Install curl 
```
apt install -y curl

```
## Add NodeSource repo

```
curl -fsSL https://deb.nodesource.com/setup_22.x | bash -

```
## Install Node.js
```
apt install -y nodejs

```
## Verify
```
node -v
npm -v

```

## update and install git
```
apt update
apt install -y git

```


##  Install OpenClaw
```
npm install -g openclaw@latest

```
After installation, check:

```
openclaw --version

```
---

## Fix Android Network Interface Error

Create the hijack script:


```
cat <<EOF > /root/hijack.js
const os = require('os');
os.networkInterfaces = () => ({});
EOF
```

Make it load automatically:


```
echo 'export NODE_OPTIONS="-r /root/hijack.js"' >> ~/.bashrc
source ~/.bashrc
```

---

## Run OpenClaw Setup Wizard

Start onboarding:


```
openclaw onboard
```

When prompted for **Gateway Bind**, select:



127.0.0.1 (Loopback)


---

## Launch the OpenClaw Gateway

Start the agent:


```
openclaw gateway --verbose
```

---

## Access the Web Dashboard

Open your mobile browser and go to:


```
http://127.0.0.1:18789

```
Get your gateway token:



openclaw config get gateway.auth.token


Paste the token into the dashboard login screen.

---

## Useful Agent Commands



/status

Check agent health.



/think high

Enable deep reasoning mode.



/reset

Clear memory and restart the session.

---

## Stability Tips

### Prevent Termux from Sleeping



termux-wake-lock


### Disable Battery Optimization

1. Go to Android Settings
2. Apps → Termux
3. Battery
4. Disable optimization

### Keep Device Plugged In

For true 24/7 operation, keep the phone connected to power.

---

## Security Tips

- Never share your API keys publicly
- Do not share your gateway token
- Use a separate Google account for AI keys if possible

---

## What You Can Do Next

- Automate research tasks
- Build a personal AI assistant
- Connect it to messaging apps
- Use it as a mobile automation node

---

## Final Note

If you followed each step correctly, your Android device is now running a fully functional AI agent locally.

Watch the full walkthrough again:

https://youtu.be/hM5LHJByJZk


