DISCLAIMER: For transparency's sake (mainly because I don't want to take unfair credit for stuff): the research and testing here was done by me (as you can see on www.f4mi.com on the video where we talk about this), I did end up using local LLMs to help me with building the websites based on that research and cleaning up/helping me with docs/pushing some stuff to GitHub, as I said in the video I don't know shit and I am pretty much learning on the fly. Some of them for some reason (which I mean, isn't that mysterious if you consider how the sausage is made) think they are Claude. So if you see Claude mentions here, that's why lol

# GameBuddy TUI

Small standalone terminal UI for controlling an AVerMedia Game Capture HD II / GameMate box over HTTP.

Files in this folder:

- `gcii_tui.py`: main Python app
- `launch_gcii.cmd`: launcher for `cmd.exe`
- `launch_gcii.ps1`: launcher for PowerShell
- `launch_gcii.sh`: launcher for Linux/macOS shells

Features:

- SSDP discovery
- Status and box info queries
- Record start, pause, and stop
- Snapshot capture
- Remote-control keys such as arrows, OK, menu, back, and F1-F3
- Remote download over LAN
- Custom `method/...` and `query/...` calls

## Requirements

- Python 3.10 or newer recommended
- Network access to the Game Capture HD II on your LAN

## Run

Direct Python:

```bash
python gcii_tui.py
python gcii_tui.py --host 192.168.1.50 --port 80
```

Windows `cmd.exe`:

```bat
launch_gcii.cmd
launch_gcii.cmd --host 192.168.1.50 --port 80
```

Windows PowerShell:

```powershell
./launch_gcii.ps1
./launch_gcii.ps1 --host 192.168.1.50 --port 80
```

Linux/macOS shell:

```bash
chmod +x launch_gcii.sh
./launch_gcii.sh
./launch_gcii.sh --host 192.168.1.50 --port 80
```

## Keys

- `d`: discover devices with SSDP
- `h`: set host
- `t`: set port
- `n`: query device name
- `q`: query status
- `w`: query whole box info
- `i`: query input source
- `r`: start recording
- `p`: pause recording
- `x`: stop recording
- `s`: take snapshot
- `k`: keep-alive
- Arrow keys: remote directional pad
- `Enter` or `o`: OK
- `m`: menu
- `b`: back
- `1`, `2`, `3`: F1, F2, F3
- `/`: custom endpoint
- `[` and `]`: cycle discovered devices
- `Esc`: exit

## Notes

- Discovery now uses SSDP to `239.255.255.250:1900`, matching behavior seen in the original app.
- The exact response payloads can vary by firmware.
- The tool is standalone and only depends on the Python standard library.

## Research Sources

- [lkiesow/avermedia-game-capture-hd-ii-reverse-engineering](https://github.com/lkiesow/avermedia-game-capture-hd-ii-reverse-engineering) was used as a reverse-engineering reference.
