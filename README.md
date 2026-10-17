# PS5 Relapse Exploit — AIO by Muhammad Yaser

Supported firmware: 7.00 through 13.60.

## Usage

- In network settings, set Primary DNS to `45.56.67.85` (recommended).
- Run `python serve.py` locally, or open https://muhammad10yaser.github.io/ex on the PS5.
- Payloads are stored in `payloads/`. After a successful run, the ELF loader listens on port `9021`.
- Once elfldr is listening on port `9021`:
  - Press **X** to select/deselect a payload.
  - Use **D-pad ↑ / ↓** to move the cursor.
  - Press **L2** to run all selected payloads.
  - Press **R1** to run **etaHEN only**.

## Included payloads

All payloads are stored in `payloads/` and listed in `payloads.json`:

- `CheatRunner_v0.12.elf` — cheat runner
- `elfldr-ps5-1360.elf` — ELF loader (listens on port 9021)
- `etaHEN(13.60).elf` — homebrew enabler (13.60 build)
- `ftpsrv-ps5.elf` — FTP server (PS5 build)
- `ftpsrv.elf` — FTP server
- `game-compressor (1.04).elf` — game compressor
- `garlic-savemgr.elf` — save manager
- `kstuff lite (1.11).elf` — kernel payload
- `lapy_jb_daemon.elf` — jailbreak daemon
- `LZ4-Game-Compressor-beta.2.elf` — LZ4 game compressor (beta)
- `nanodns.elf` — minimal DNS server
- `np-fake-signin-ps5.elf` — fake NP sign-in
- `OnionHEN(upto 12.70).elf` — OnionHEN (firmware ≤ 12.70)
- `OnionHEN(Upto 13.60).elf` — OnionHEN (firmware ≤ 13.60)
- `pkg-manager_v1.4.1.elf` — PKG manager
- `pldmgr_v0.5.1.elf` — payload manager (v0.5.1)
- `pldmgr_v0.6.1.elf` — payload manager (v0.6.1)
- `PoorDS4-stop.elf` — PoorDS4 (stop)
- `PoorDS4rc51.elf` — PoorDS4 (rc51)
- `ps5-app-dumper.elf` — app dumper
- `ps5-backpork.elf` — backpork
- `ShadowMountPlus 1.7beta5.elf` — mount helper
- `TabShifter-v1.1.0.elf` — tab shifter
- `webkit-autoloader-installer_v0.5.2.elf` — WebKit autoloader installer (v0.5.2)
- `webkit-autoloader-installer_v0.6.1.elf` — WebKit autoloader installer (v0.6.1)

Missing payloads are skipped automatically.

## Controls

| Button | Action |
|---|---|
| **X** | Toggle select on the cursor row |
| **D-pad ↑ / ↓** | Move cursor up / down |
| **L2** | Run all selected payloads |
| **R1** | Run **etaHEN.elf only** |

Clicking a row with the mouse has the same effect as pressing X on it.

## Payload list (display order)

1. `pldmgr_v0.5.1.elf`
2. `kstuff lite (1.11).elf`
3. `ShadowMountPlus 1.7beta5.elf`
4. `game-compressor (1.04).elf`
5. `webkit-autoloader-installer_v0.5.2.elf`
6. `etaHEN(13.60).elf`
7. `CheatRunner_v0.12.elf`
8. `elfldr-ps5-1360.elf`
9. `ftpsrv-ps5.elf`
10. `ftpsrv.elf`
11. `garlic-savemgr.elf`
12. `lapy_jb_daemon.elf`
13. `LZ4-Game-Compressor-beta.2.elf`
14. `nanodns.elf`
15. `np-fake-signin-ps5.elf`
16. `OnionHEN(upto 12.70).elf`
17. `OnionHEN(Upto 13.60).elf`
18. `pkg-manager_v1.4.1.elf`
19. `pldmgr_v0.6.1.elf`
20. `PoorDS4-stop.elf`
21. `PoorDS4rc51.elf`
22. `ps5-app-dumper.elf`
23. `ps5-backpork.elf`
24. `TabShifter-v1.1.0.elf`
25. `webkit-autoloader-installer_v0.6.1.elf`

When you press **L2**, only the **selected** payloads are sent, in the order above. Each payload is sent with a short delay (3 s) so elfldr can finish loading before the next one arrives.

## Already jailbroken?

If the console is already jailbroken when the page is opened, the payload sender becomes ready automatically — no re-jailbreak needed. Just select payloads and press **L2**.

## Stability notes

WebKit may need several attempts — reload the page if the browser stalls. The kernel exploit may hang or panic the console, so reboot before trying again if that happens.

## Exploit chain

Browser stage uses JSC info leaks and a structured clone object pool mismatch to corrupt a typedarray. The kernel stage combines an address leak with an `aio_multi_wait` UAF race to establish kernel R/W.

## Developer

**Muhammad Yaser** — PS5 dashboard, payload sender, launcher UI, and payload integration.

## Credits

ntfargo, ufm42, Sonic-Iso, Jordy, Dr. Yenyen, TheFlow, SlidyBat, Flatz, cow, nhk, bollarz, Sleirsgoevy, EchoStretch, EarthOnion.

## Disclaimer

This project is intended for **educational and security research purposes only**. It does not endorse piracy, unauthorized access, or misuse of commercial devices. Use it only on devices you own or are authorized to test, and comply with applicable laws and regulations.

The software is provided as-is, without warranty. You assume the risks of using it, including system instability, data loss, and account bans. The maintainers accept no liability for resulting damage.