# Docker Setup Guide

**Complete this before Lesson 4.4.** This guide walks you through installing Docker on your computer so you're ready to build and run containers.

**Follow the section that matches your computer:**
- **Windows (using WSL)** → follow [Part A](#part-a-windows-with-wsl)
- **Mac** → follow [Part B](#part-b-mac)

Both paths end at the same place: a working `docker` command and a successful test run.

---

## Part A: Windows (with WSL)

Most of you are on Windows using WSL (Windows Subsystem for Linux) for your terminal. This section assumes you already have WSL set up from earlier coursework. **Important:** Docker itself is installed on **Windows**, not inside WSL — WSL just needs one extra setting turned on afterward so it can "see" Docker.

### Before you start: quick requirements check

- **Windows version:** Windows 10 64-bit version 21H2 or newer, or any Windows 11. (Check: **Settings → System → About** — look at "Version" or "OS Build.")
- **Admin account:** You'll need administrator access on your machine — the installer adds you to a system group and registers a background service, both of which require admin rights.
- **Disk space:** At least 6 GB free.
- **Virtualization:** Should already be on for most laptops from the last several years. If Docker Desktop later fails to start with a virtualization-related error, see [Troubleshooting](#troubleshooting) below.

If all of that looks fine, continue to Step 1.

### Step 1: Confirm WSL2 is installed

Open **PowerShell** (not WSL) and run:

```powershell
wsl --version
```

**Expected:** You should see a WSL version number (2.x.x.x). If instead you get an error saying `wsl` is not recognized, or the command shows no version info at all, install WSL first:

```powershell
wsl --install
```

Then **restart your computer** before continuing.

### Step 2: Download Docker Desktop for Windows

1. Go to [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)
2. Click **Download for Windows**
3. Run the downloaded installer (`Docker Desktop Installer.exe`)

### Step 3: Run the installer

1. During installation, make sure **"Use WSL 2 instead of Hyper-V"** (sometimes shown as "Use WSL 2 based engine") is **checked** — this is the default option, so you usually don't need to change anything
2. Finish the installation
3. **Restart your computer** if prompted

### Step 4: Start Docker Desktop

1. Open **Docker Desktop** from the Windows Start menu
2. Wait for it to fully start (the whale icon in your system tray should stop animating and show it's running)
3. **Leave Docker Desktop running in the background** — it needs to stay open whenever you want to use Docker

### Step 5: Turn on WSL Integration (the extra step)

This is the step that connects Docker to your WSL terminal:

1. In Docker Desktop, click the **gear icon** (Settings) in the top right
2. Click **Resources** in the left sidebar
3. Click **WSL Integration**
4. Turn **ON** the toggle for your Linux distro (usually named **Ubuntu**)
5. Click **Apply & Restart**

### Step 6: Verify Docker works from WSL

1. Open your **WSL terminal** (e.g., Ubuntu — not PowerShell, not Command Prompt)
2. Run:
   ```bash
   docker --version
   ```
   **Expected:** Something like `Docker version 27.x.x, build xxxxxxx`

3. Run:
   ```bash
   docker run hello-world
   ```
   **Expected:** Docker downloads a small test image and prints a message starting with:
   ```
   Hello from Docker!
   This message shows that your installation appears to be working correctly.
   ```

**If you see that message, you're done — Docker is fully working. Move on to Lesson 4.4.**

---

## Part B: Mac

Mac setup is simpler — no extra integration step needed.

### Before you start: quick requirements check

- **macOS version:** macOS 13 (Ventura) or newer is recommended.
- **Disk space:** At least 6 GB free.
- **Admin password:** You'll be asked for your Mac login password during install to grant system permissions.

If all of that looks fine, continue to Step 1.

### Step 1: Download Docker Desktop for Mac

1. Go to [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)
2. Click **Download for Mac**
3. Choose the correct version for your Mac's chip:
   - **Apple Silicon** (M1/M2/M3/M4) — most Macs from late 2020 onward
   - **Intel Chip** — older Macs
   
   **Not sure which chip you have?** Click the Apple menu (top-left) → **About This Mac** — it will say "Chip: Apple M-something" or "Processor: Intel..."

### Step 2: Install Docker Desktop

1. Open the downloaded `.dmg` file
2. Drag the **Docker** icon into your **Applications** folder
3. Open **Docker** from your Applications folder (or Spotlight search)
4. Approve any system permission prompts it asks for

### Step 3: Start Docker Desktop

1. Wait for Docker Desktop to fully start (the whale icon in your menu bar should stop animating)
2. **Leave Docker Desktop running in the background** — it needs to stay open whenever you want to use Docker

### Step 4: Verify Docker works

1. Open **Terminal** (your regular Mac terminal)
2. Run:
   ```bash
   docker --version
   ```
   **Expected:** Something like `Docker version 27.x.x, build xxxxxxx`

3. Run:
   ```bash
   docker run hello-world
   ```
   **Expected:** Docker downloads a small test image and prints a message starting with:
   ```
   Hello from Docker!
   This message shows that your installation appears to be working correctly.
   ```

**If you see that message, you're done — Docker is fully working. Move on to Lesson 4.4.**

---

## Troubleshooting

### "wsl --install" or "wsl --version" doesn't work at all (Windows)

Your Windows version may be too old, or WSL was never set up. Check with your instructor — this needs to be resolved before Docker Desktop will work.

### Docker Desktop won't start / shows a virtualization error (Windows)

This usually means hardware virtualization is turned off in your computer's BIOS/UEFI settings.

1. Restart your computer and enter BIOS/UEFI setup (usually pressing `F2`, `F10`, `Del`, or `Esc` during startup — varies by manufacturer)
2. Look for a setting called **Intel VT-x**, **Intel Virtualization Technology**, or **SVM Mode** (AMD)
3. Enable it, save, and restart normally
4. Try opening Docker Desktop again

### `docker: command not found` in WSL terminal, even after installing Docker Desktop

You likely missed Step 5 (WSL Integration). Go back to Docker Desktop → Settings → Resources → WSL Integration, and make sure your distro's toggle is switched **ON**, then click **Apply & Restart**.

### `docker run hello-world` hangs or fails with a connection error

Docker Desktop probably isn't running. Check that the whale icon is visible (system tray on Windows, menu bar on Mac) and shows Docker as running, not starting up. Give it a minute after opening it before trying again.

### I already have Docker installed directly inside WSL (not Docker Desktop)

Uninstall it before installing Docker Desktop. Running Docker Engine directly inside WSL *and* Docker Desktop at the same time can cause conflicts. Docker Desktop (installed on Windows, with WSL Integration turned on) is the supported setup for this course.

---

## Summary Checklist

Before moving to Lesson 4.4, confirm:

- [ ] Docker Desktop is installed and open
- [ ] (Windows only) WSL Integration is turned ON for your distro
- [ ] `docker --version` returns a version number
- [ ] `docker run hello-world` prints the "Hello from Docker!" success message