# Nujabes handoff: XPS 15 → dedicated Windows DJ box

Context from a planning session with the owner. You (Claude Code on the device) are helping turn this laptop into a dedicated DJ machine. The owner has 35 years in IT and handles the OS reload themselves; they are new to DJing. Ask before anything destructive (disk writes, partitioning, BIOS changes).

## Hardware

| Item | Value | Status |
|---|---|---|
| Laptop | Dell XPS 15 **9500** (2020) | Inferred from specs below; confirm on F2 BIOS screen or bottom label (regulatory model P91F) |
| CPU | Intel Core i7-10750H, 6 cores / 12 threads | Confirmed (Dell system info screenshot) |
| RAM | 32 GB | Confirmed |
| SSD | 512 GB NVMe | Confirmed |
| GPU | Intel UHD + NVIDIA GTX 1650 Ti | Confirmed |
| Display | 4K touchscreen | Confirmed |
| Charger | 130 W USB-C | Confirmed |
| Ports | USB-C/Thunderbolt only (no USB-A) | Model fact |
| Current OS | Linux (tinkering install, **nothing to back up**) | Confirmed by owner |
| Service tag | Unknown — capture it | To do |

## DJ gear and accounts

- **Controller:** AlphaTheta (formerly Pioneer DJ) **DDJ-GRV6**, 4-channel, with the Groove Circuit section (Drum Swap, Drum Roll, Capture — stem-based). Connects over **USB-C**; the owner already has the cable (it worked with their MacBook Air).
- **Software:** test **rekordbox** and **Serato DJ Pro** side by side, then keep one.
  - rekordbox: native for the GRV6; performance features are unlocked when the deck is connected (hardware unlock).
  - Serato: the owner used it on the Mac. **There is no license in their serato.com account**, so it was probably unlocked by the deck. Confirm on Windows: no trial or "Activate" banner means it's unlocked by the deck. A trial countdown or "Serato DJ Lite" means the Mac was probably on a trial.
- **Streaming:** **Beatport** subscription (tier unknown — check offline/locker allowance) and **Spotify Premium** (DJ integration came back in 2025 for rekordbox, Serato and djay; check each app's streaming list — region/version dependent; personal use only).
- **Home audio (future):** Sonos Port planned, shared with a turntable. The Port has one analog input, so it needs an RCA A/B switch, plus a phono preamp if the turntable lacks one. Feed it from the GRV6 **Booth out**, lowest line-in delay. Expect ~70–75 ms latency, which is fine because the DJ monitors on headphones from the deck.

## Phase 1 — Before wipe (on Linux, now)

1. Capture identity (owner asked for these):
   ```
   sudo dmidecode -s system-product-name
   sudo dmidecode -s system-serial-number      # Dell service tag
   lscpu | grep "Model name"
   sudo ls /sys/firmware/acpi/tables/MSDM      # exists = Windows key embedded in firmware
   ```
   Write the results into this file under "Hardware".
2. Build the **Windows 11 installer** on a *spare* USB stick (≥8 GB) with **Ventoy** + the official Win11 ISO (microsoft.com/software-download/windows11). Don't write the stick with `dd`.
   - **Before running Ventoy2Disk, use `lsblk` to identify the stick and show the owner the target device to confirm.** Ventoy wipes it. Never touch the internal NVMe (`nvme0n1`).
   - The owner's separate USB data drive is **not** the installer stick.
3. Optional: copy onto the stick for later — LatencyMon installer, DDJ-GRV6 Windows driver (alphatheta.com support page), rekordbox installer (rekordbox.com), Serato DJ Pro installer (serato.com).

## Phase 2 — Install (owner drives this)

1. **F2** → BIOS → Storage: change **RAID On → AHCI** (safe because the disk is being wiped; avoids needing the Intel RST driver). Note the service tag/model from the BIOS screen.
2. **F12** → boot the Ventoy USB → Windows 11 → delete **all** partitions → install. Activation should be automatic if MSDM existed.
3. Windows Update until clean → install **Dell Command Update** → apply drivers + **BIOS update**.

## Phase 3 — Post-install tuning (you can do most of this on Windows)

Dedicated DJ box. Keep it minimal.

- Power (admin PowerShell):
  ```powershell
  # Best performance on AC, never sleep while plugged in
  powercfg /change standby-timeout-ac 0
  powercfg /change monitor-timeout-ac 0
  # Disable USB selective suspend (AC) — prevents controller dropouts
  powercfg /setacvalueindex SCHEME_CURRENT 2a737441-1930-4402-8d77-b2bebba308a3 48e6b7a6-50f5-4782-a5d4-53bb8f07e226 0
  powercfg /setactive SCHEME_CURRENT
  ```
  Also set Settings → Power mode → **Best performance**.
- Notifications off. Do Not Disturb on. Windows Update **active hours** cover DJ time. Pause updates before sessions; don't disable updates permanently.
- Remove Dell/McAfee trial software and unneeded startup apps. **Leave Defender on**, but schedule scans outside DJ time.
- Music library: single folder on the internal SSD (e.g. `C:\Music`). Both DJ apps point at it. The USB drive is for backups and rekordbox USB exports only, never for live playback.
- **LatencyMon baseline** (5 min) **before** installing the DJ software. Known XPS 9500 culprits:
  - `nvlddmkm.sys` (NVIDIA): update the driver, and set rekordbox/Serato to **Power saving** (Intel GPU) under Settings → Display → Graphics.
  - Wi-Fi (Killer/Intel AX): update the driver. Turn Wi-Fi off when not streaming.
  - ACPI: update the BIOS.

## Phase 4 — DJ software

1. Install the **DDJ-GRV6 Windows driver first**, then rekordbox, then Serato.
2. Plug the deck **directly** into a laptop USB-C port (no hub).
3. Audio buffer: start around 5–10 ms and raise it if you hear crackles.
4. Log in to Beatport (and Spotify, if listed) in each app's browser panel.
5. **Never run rekordbox and Serato at the same time.** Unplug and replug the deck when switching between them.

### Side-by-side test (same 6–10 tracks in each, ~30–45 min per app)
Rate each on:
- Setup and detection
- Library and playlists
- A first transition (sync + bass swap at a phrase boundary)
- Hot cues and loops
- Stems / Groove Circuit pads
- Beatport playback (do stems work on streamed tracks?)
- Spotify availability and what's grayed out
- Touchscreen feel
- Gut feel

Tie-breaker: **rekordbox** (full GRV6 support, club CDJ standard).

## DJ coaching notes (owner is a beginner)

Teach in this order:
1. Phrasing (4 beats per bar; 8/16/32-bar phrases; start transitions on phrase boundaries; rekordbox Phrase analysis)
2. Beatmatching (SYNC is fine to start; learn by ear later)
3. Gain staging (TRIM to equal meters, nothing in the red)
4. EQ (never two basslines at once: the bass swap)
5. Hot cues and loops
6. Key / harmonic mixing
7. Track selection and energy

- **Practice plan:**
  - Wk1: library prep, plus lots of sync/bass-swap transitions.
  - Wk2: strict phrasing, plus loops.
  - Wk3: beatmatch by ear, plus light Beat FX.
  - Wk4+: stems/Groove Circuit, and record mixes to listen back to.
- **Beatport tips:** prefer **extended mixes**. Build playlists by purpose (warm-up / peak / closers). Use genre and DJ charts for discovery. Stream to practice; buy or save offline the tracks you rely on to play out.
- **Spotify:** good for practicing with songs the owner already knows well (radio edits, short intros). Not for public gigs.
- **Resources:** AlphaTheta's official DDJ-GRV6 videos, Crossfader and Digital DJ Tips on YouTube, rekordbox tutorial mode.
- Owner's preferred genre is still unknown. Ask.

## Open items
- [ ] Confirm model (9500) and record the service tag
- [ ] MSDM present? (license auto-activation)
- [ ] Beatport tier and offline allowance
- [ ] Does the GRV6 have a line/aux input on the back? (would let the turntable feed through the deck to the Sonos Port)
- [ ] Owner's genre(s)
- [ ] rekordbox vs Serato decision after the side-by-side test
