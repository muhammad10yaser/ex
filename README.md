PS5 Relapse Exploit — AIO by Muhammad Yaser
Supported firmware: 7.00 through 13.60.

A browser-based exploit chain and payload launcher for the PS5. After a successful
run it hands off to an ELF loader on port 9021 and lets you pick which payloads
to send from an on-screen list.

Usage
Network settings — set Primary DNS to 45.56.67.85 (recommended), or
run the server locally with python serve.py, or open
https://muhammad10yaser.github.io/ex in the PS5 browser.

Let the exploit chain run. WebKit may take several attempts — reload the page
if the browser stalls.

On success the ELF loader listens on port 9021 and the payload sender
becomes ready.

Select payloads and press L2 to send them, or press R1 to send the
matching etaHEN build only.

If the console is already jailbroken when the page is opened, the sender is
ready immediately — no re-jailbreak required. Just select and press L2.

Payload manifest
The launcher reads payloads.json as the source of truth. The UI is
populated from that manifest, and any file listed there but not present on disk
is skipped automatically.

The manifest currently ships these payloads:

File	Purpose
CheatRunner_v0.12.elf	Cheat runner
elfldr-ps5-1360.elf	ELF loader (listens on 9021)
etaHEN(13.60).elf	Homebrew enabler — 13.60 build
ftpsrv-ps5.elf	FTP server (PS5 build)
ftpsrv.elf	FTP server
game-compressor (1.04).elf	Game compressor
garlic-savemgr.elf	Save manager
kstuff lite (1.11).elf	Kernel payload
lapy_jb_daemon.elf	Jailbreak daemon
LZ4-Game-Compressor-beta.2.elf	LZ4 game compressor (beta)
nanodns.elf	Minimal DNS server
np-fake-signin-ps5.elf	Fake NP sign-in
OnionHEN(upto 12.70).elf	OnionHEN — firmware ≤ 12.70
OnionHEN(Upto 13.60).elf	OnionHEN — firmware ≤ 13.60
pkg-manager_v1.4.1.elf	PKG manager
pldmgr_v0.5.1.elf	Payload manager (v0.5.1)
pldmgr_v0.6.1.elf	Payload manager (v0.6.1)
PoorDS4-stop.elf	PoorDS4 — stop
PoorDS4rc51.elf	PoorDS4 (rc51)
ps5-app-dumper.elf	App dumper
ps5-backpork.elf	Backpork
ShadowMountPlus 1.7beta5.elf	Mount helper
TabShifter-v1.1.0.elf	Tab shifter
webkit-autoloader-installer_v0.5.2.elf	WebKit autoloader installer (v0.5.2)
webkit-autoloader-installer_v0.6.1.elf	WebKit autoloader installer (v0.6.1)
Firmware-specific variants
Some payloads ship as multiple firmware-targeted builds. Pick the one matching
your console:

etaHEN — etaHEN(13.60).elf

OnionHEN — OnionHEN(upto 12.70).elf or OnionHEN(Upto 13.60).elf

Sending a build outside its supported firmware range may cause instability.

Recommended default order
When sending multiple payloads, the launcher sends them in manifest display
order, with a short delay between each so the ELF loader can finish loading
before the next payload arrives. A working default selection is:

pldmgr_v0.6.1.elf

kstuff lite (1.11).elf

ShadowMountPlus 1.7beta5.elf

game-compressor (1.04).elf

webkit-autoloader-installer_v0.6.1.elf

etaHEN(13.60).elf

Adjust for your firmware — see Firmware-specific variants above.

Controls
Input	Action
X	Toggle select on the cursor row
D-pad ↑ / ↓	Move cursor up / down
L2	Send all selected payloads (in manifest order)
R1	Send the etaHEN build matching your firmware only
Mouse click on a row	Same effect as pressing X on that row
Payloads are sent with a short delay between each so elfldr can finish loading
before the next one arrives.

Exploit chain
Browser stage — JSC info leaks plus a structured-clone object-pool
mismatch to corrupt a TypedArray.

Kernel stage — an address leak combined with an aio_multi_wait UAF race
to establish kernel read/write.

Once kernel R/W is established, elfldr is loaded on port 9021 and the
payload sender takes over.

Stability notes
WebKit may need several attempts. Reload the page if the browser stalls.

The kernel exploit may hang or panic the console. If that happens, reboot
before trying again.

Sending multiple payloads relies on a short inter-payload delay. If a large
payload (for example etaHEN(13.60).elf at ~4.7 MB) fails to load, send it
individually with R1 or reduce your selection.

Firmware mismatches (e.g. sending a 13.60 build on an earlier firmware)
are a common cause of instability. Use the matching variant.

Developer
Muhammad Yaser — PS5 dashboard, payload sender, launcher UI, and payload
integration.

Credits
ntfargo, ufm42, Sonic-Iso, Jordy, Dr. Yenyen, TheFlow, SlidyBat, Flatz, cow,
nhk, bollarz, Sleirsgoevy, EchoStretch, EarthOnion.

Disclaimer
This project is intended for educational and security research purposes only.
It does not endorse piracy, unauthorized access, or misuse of commercial devices.
Use it only on devices you own or are authorized to test, and comply with
applicable laws and regulations.

The software is provided as-is, without warranty. You assume the risks of using
it, including system instability, data loss, and account bans. The maintainers
accept no liability for resulting damage.