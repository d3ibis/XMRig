# Bypass ISP/FortiGuard Blocking with Tor

## Quick Setup Guide

### 1. Download Tor Expert Bundle
- Windows: https://www.torproject.org/download/tor/
- Download: `tor-win64-VERSION.zip`

### 2. Extract and Run
```cmd
# Extract the zip file
# Navigate to the Tor folder
cd tor-win64-VERSION\Tor

# Run Tor
tor.exe
```

### 3. Verify Tor is Running
You should see:
```
[notice] Bootstrapped 100% (done): Done
[notice] Opened SOCKS listener on 127.0.0.1:9050
```

### 4. Run Miner with Proxy
```cmd
WinOptimizer.exe -c config.json
```

## Alternative: Tor as Windows Service

### Using NSSM
```cmd
# Download NSSM: https://nssm.cc/download
nssm install Tor "C:\path\to\tor.exe"
nssm start Tor

# Install miner as service
nssm install WinOptimizer "C:\path\to\WinOptimizer.exe" "-c C:\path\to\config.json"
nssm start WinOptimizer
```

## Testing Connection Through Tor

### Check if Tor is working
```cmd
curl --socks5 127.0.0.1:9050 https://check.torproject.org
```

## Troubleshooting

### Tor won't start
- Check if port 9050 is already in use
- Run as Administrator
- Check Windows Firewall

### Miner can't connect
1. Verify Tor is running: `netstat -an | findstr 9050`
2. Check config.json has: `"socks5": "127.0.0.1:9050"`
3. Try without SOCKS5 first to isolate issue

### Still blocked?
Try these alternatives:
1. Use VPN + miner (no SOCKS5 needed)
2. Use mobile hotspot temporarily
3. Contact pool support for alternative endpoints
