# Legacy Android Tablet Revitalization Prompt

Copy and paste the prompt below into your AI Agent (Antigravity, Cursor, Claude Code, ChatGPT, etc.) when your old Android tablet is connected via USB:

---

## 🎯 Main Prompt (Diagnostic, Benchmark & Debloat)

```markdown
You are an expert embedded systems and Android performance optimization engineer. 
A legacy Android tablet is connected to this host computer via USB.

Execute the following systematic revitalization workflow using your terminal/shell tools:

### Step 1: Detect & Connect
1. Verify if Android Debug Bridge (`adb`) is present. If missing, download/extract Google's standalone platform-tools in a scratch directory.
2. Run `adb devices -l` to identify the device connection status and authorization.
3. If unauthorized or offline, guide the user on granting USB debugging permissions on the tablet display.

### Step 2: Deep Hardware & OS Profiling
Gather and summarize the hardware specifications:
- **SoC & Architecture**: CPU part, core count, frequency, governor (`/proc/cpuinfo`, `sys/devices/system/cpu/...`).
- **Memory**: Usable RAM, free RAM, and active memory pressure (`/proc/meminfo`, `dumpsys meminfo`).
- **Storage**: Partition table, mount points, internal flash, and external SD slot (`df`, `cat /proc/mounts`).
- **Display & Graphics**: Resolution, density, refresh rate, and GPU model.
- **Connectivity & Peripherals**: Wi-Fi status, IP, battery health/temp, and USB-OTG host support (`dumpsys battery`, `netcfg` / `ifconfig`).
- **Privilege Level**: Kernel version, build number, and root privilege status (`id`, `which su`).

### Step 3: Package & Bloatware Audit
1. Enumerate user-installed applications (`pm list packages -3 -f`).
2. Identify top memory consumers (`dumpsys meminfo`).
3. Audit pre-installed bloatware, telemetry, obsolete update daemons, and Google Play Services (`com.google.android.gms`).
4. Calculate storage consumed in `/data/data` and `/data/app` by sunset apps.

### Step 4: Safe Debloating & Memory Recovery
Once confirmed or instructed:
1. **Uninstall User-Space Dead Apps**: Remove sunset Google services (`com.google.android.gms`, `com.google.android.youtube`, `com.google.android.apps.maps`, `com.android.chrome`, etc.) and carrier/OEM affiliates.
2. **Disable System-Level Bloatware**: Safely disable background telemetry daemons, obsolete OTA updaters, and legacy sync adapters via `pm disable <package>`.
3. **Preserve System Stability**: Keep core framework, input methods (keyboards), hardware calibration, audio engines, and root access (`su` / BusyBox) intact.
4. **Tune UI Responsiveness**: Set window, transition, and animator scales to `0.5x` via `settings put global ...` to eliminate interface rendering lag.

### Step 5: Benchmark & Repurposing Roadmap
1. Measure and report Before vs. After metrics in a clear comparison table:
   - Free System RAM (`MemFree`)
   - Total App Memory PSS load
   - Free `/data` storage
   - Background process count
2. Present tailored, realistic modern use cases matching the hardware profile (e.g., PC Hardware Monitor screen, Home Assistant dashboard, Retro Emulation station, Desk Clock / Hi-Fi Audio player, Distraction-free E-Reader).
```

---

## 🏠 Optional Add-on Prompt: Home Assistant Kiosk (TileBoard)

> **Run this optional follow-up prompt only if you want to turn the tablet into a 24/7 Home Assistant wall-mount dashboard:**

```markdown
Configure this connected Android tablet for 24/7 Home Assistant Kiosk Wall Panel duty:

1. Kiosk Keep-Awake Settings:
   - Configure Wi-Fi to never sleep when idle: `settings put global wifi_sleep_policy 2`
   - Keep screen permanently awake while connected to USB/AC power: `settings put global stay_on_while_plugged_in 7`
   - Set fallback screen timeout: `settings put system screen_off_timeout 1800000`

2. Lightweight Browser:
   - Install a lightweight, low-RAM browser with full-screen kiosk support (e.g., Lightning Browser from F-Droid, ~2.3MB APK footprint).

3. Provide a tailored TileBoard configuration blueprint (`config.js`) matching the tablet's resolution (e.g., 800x480) with tiles for Clock, Weather, Lights, Switches, and Thermostat.
```
