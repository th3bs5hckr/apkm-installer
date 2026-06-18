# APKM Installer TUI 📦📱

An advanced, terminal-based desktop management panel built in Python. It safely parses, optimizes, and installs modern Android split application bundles (`.apkm`, `.apks`, `.xapk`) directly onto USB-connected devices via ADB.

---

## 🚀 Key Features

* **File Navigator:** Native multi-directory sidebar to quickly browse local system drives.
* **Device Profiling:** Automated ADB inspection parsing device model, CPU ABI priority layers, density buckets, and local system languages.
* **Smart Filter Matrix:** Auto-evaluates split assets to pre-select matching system dependencies for the active target phone.
* **Safety Lock Override:** Hard-locks vital system splits (e.g., `base.apk` or matching architecture files) from manual box removal to guarantee a clean installation process.
* **Live Logger:** High-precision, scrolling log widget tracking ongoing extraction benchmarks and instant ADB output errors.

---

## ⌨️ Global Keybindings

| Hotkey | Operational Action |
| :--- | :--- |
| `Q` | Instantly close and exit the application terminal. |
| `R` | Force-rescan and re-probe the system's USB stack for active ADB targets. |
| `Ctrl + A` | Batch-select every available split file inside the source folder. |
| `Ctrl + D` | Drop optional localized/asset packs while preserving core system splits. |

## 🛠️ Environment Setup (All Platforms)

### 1. Install System Dependencies
Install **Python 3** and **ADB (Android SDK Platform-Tools)** depending on your operating system:

* **Windows:**
    * Download and install Python 3 from [python.org](https://www.python.org/) *(Ensure the **"Add python.exe to PATH"** checkbox is ticked during installation)*.
    * Download [SDK Platform-Tools for Windows](https://developer.android.com/tools/releases/platform-tools), extract it to a permanent folder, and add that folder's path to your system's environment **Path** variable.
* **Linux (Debian/Ubuntu/Mint):**
    ```bash
    sudo apt update && sudo apt install adb python3 python3-pip -y
    ```
* **macOS:**
    Install via Homebrew (Terminal):
    ```bash
    brew install android-platform-tools python
    ```

---

### 2. Configure Your Android Device
1. On your Android phone, navigate to **Settings ➔ About Phone** and tap **Build Number** 7 times to unlock Developer Options.
2. Open the newly unlocked **Developer Options** menu and toggle **USB Debugging** to ON.
3. Connect your phone to your computer via a USB cable.
4. Verify the ADB link by running this command in your computer's terminal:
   ```bash
   adb devices
Check your phone's screen and tap Allow / Authorize on the USB debugging authorization prompt).
## 🏃 Launching the Installer App

Open your terminal inside the exact directory containing your script file, initialize the required text-user-interface (TUI) package elements, and execute the launcher module interface:

```bash
pip install textual rich
python3 apkm_installer.py

💡 Execution Notes:
​Managed Environments (Linux/macOS): If your terminal blocks the installation with an external environment error, simply append --break-system-packages to the end of your pip install command:  pip install textual rich --break-system-packages

Virtual Environments (Alternative): Alternatively, safely containerize the app build by setting up a local clean room configuration:
  python3 -m venv venv
  source venv/bin/activate  # On Windows use: venv\Scripts\activate
  pip install textual rich
  python3 apkm_installer.py