# Tailscale for Linux (No Sudo Required!)  
*Run Tailscale VPN in Linux machines with persistent IPs – without requiring sudo priveleges. Simple and secure setup.*  

[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)  

## Why Use This?  
- 🌐 **Same IP every time** – No more reconfiguring tools  
- 🔒 **Private networking** – Enjoy encrypted peer-to-peer connections of Tailscale 
- ⚡ **Easy Setup** – Ready in seconds!  
- 🚫 **No high priveleges permissions** – Works without `sudo`  

---

## Getting Started  

### 1. Install Tailscale  
```bash
curl -fsSL https://tailscale.com/install.sh | sh
```
### 2. Obtaining an Auth Key
1. Login with your Tailscale Account.
2. Get a key from [Tailscale - AuthKeys](https://login.tailscale.com/admin/authkeys)
### 3. Setup your Auth Key

> For Github Codespaces:
>
> 1. Visit github.com
> 2. Go to Profile -> Settings -> [Codespaces](https://github.com/settings/codespaces)
> 3. Under **Secrets**, tap on "New secret" button.
> 4. Paste `TS_AUTH_KEY` inside the input box which is below the "Name" field, and Paste the copied [Tailscale - AuthKeys](https://login.tailscale.com/admin/authkeys) inside the input box of the "Value" field.
> 5. Click on the "Select repositories" button and select the repos in which you want to access your AuthKey.
> 6. Lastly, click on the Add secret button.

> For Linux machines 
>
> ```
> echo 'export TS_AUTH_KEY="tskey-auth-XXXXXX"' >> ~/.bashrc   # bash
> echo 'export TS_AUTH_KEY="tskey-auth-XXXXXX"' >> ~/.zshrc    # zsh
> source ~/.bashrc  # or source ~/.zshrc
> ```
> **Replace `tskey-auth-XXXXXX`with your actual authkey.**

### 4. Download Control Scripts
```bash
wget -O ~/.local/bin/start-tailscale https://raw.githubusercontent.com/itsMeRaj69/tailscale-nosudo/main/scripts/start-tailscale
wget -O ~/.local/bin/stop-tailscale https://raw.githubusercontent.com/itsMeRaj69/tailscale-nosudo/main/scripts/stop-tailscale
wget -0 ~/.local/bin/status-tailscale https://raw.gihubusercontent.com/itsMeRaj69/tailscale-nosudo/main/scripts/status-tailscale
```
### 5. Make them executable
```bash
chmod +x ~/.local/bin/start-tailscale ~/.local/bin/stop-tailscale ~/.local/bin/status-tailscale
```

---

## Usage  
| Command | What It Does |  
|---------|--------------|  
| `start-tailscale` | Start Tailscale connection |  
| `stop-tailscale`  | Stop/Disconnect safely |  
| `status-tailscale` | Check Tailscale Status |

---
- All scripts support a `--verbose` flag for full status output. (e.g: start-tailscale --verbose)

## Tips  
- **Revoke old keys** in [Tailscale - AuthKeys](https://login.tailscale.com/admin/authkeys)  

---

## Need Help?
```bash
# Check logs
cat /tmp/tailscaled.log 

# Reset everything
rm -rf ~/.config/tailscale/ /tmp/tailscale*
```

## License  
[MIT Licensed](./LICENSE) — *Not affiliated with Tailscale Inc.*
