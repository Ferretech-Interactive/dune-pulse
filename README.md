<p align="center">
  <img src="assets/dune-docker-logo.png" alt="Dune Docker logo" width="112">
</p>

<h1 align="center">Dune Pulse</h1>

<p align="center">
  A read-only, local telemetry companion for <em>Dune: Awakening</em>.<br>
  A tool in the <a href="https://dunedocker.app">DuneDocker.app</a> family.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2011%20x64-0078D4" alt="Platform: Windows 11 x64">
  <img src="https://img.shields.io/badge/Driver-Attestation--signed-2EA043" alt="Driver: attestation-signed">
  <img src="https://img.shields.io/badge/HVCI-Compatible-2EA043" alt="HVCI: compatible">
  <img src="https://img.shields.io/badge/Telemetry-Local%20only-2EA043" alt="Telemetry: local only">
  <img src="https://img.shields.io/badge/Status-Beta-E05D44" alt="Status: beta">
</p>

---

Dune Pulse shows your expedition at a glance while you play: your vitals, the vehicle you're in, your bases and their power, the Coriolis storm, and what you last did with each character. It reads values from the running game on your own PC. It never changes the game, sends no input and uploads nothing.

This repository is where Dune Pulse is **downloaded** and where you **report problems and ideas**. The source code is kept in a separate repository.

## Download

Get `DunePulseSetup-<version>.exe` from [**Releases**](../../releases). Versions marked **Pre-release** are betas.

**Check that the file is genuine before running it.** Official releases are signed by **FerreTech Interactive LLC**:

- In Explorer: right-click the file → **Properties** → **Digital Signatures**. The signer must be *FerreTech Interactive LLC* and the signature must be OK.
- Or in PowerShell:

  ```powershell
  Get-AuthenticodeSignature .\DunePulseSetup-<version>.exe | Format-List Status, SignerCertificate
  Get-FileHash .\DunePulseSetup-<version>.exe -Algorithm SHA256
  ```

  `Status` must be `Valid`, and the SHA-256 must match the one in the release notes.

Don't run a Dune Pulse setup from anywhere else, and don't run one whose signature isn't valid.

## Requirements

- Windows 11, 64-bit (x64).
- Administrator approval once, while installing. Dune Pulse itself runs as you, without administrator rights.
- Microsoft's .NET Desktop Runtime 10. If it's missing, setup offers to download it from Microsoft and installs it for you.
- Memory Integrity (HVCI) and Secure Boot can stay on: the driver is signed by Microsoft.

## Install, use and remove

1. Run the setup and approve the administrator prompt.
2. Start **Dune Pulse**. It connects to the game by itself when Dune: Awakening is running, and reconnects after a drop.
3. To remove it: **Settings → Apps → Dune Pulse → Uninstall**. This removes the app, its background service, the driver, the renewal task and its files. You can keep or delete your settings and remembered characters.

Dune Pulse checks for new versions about a minute after it starts and then daily. You can turn this off in **About**.

## What it reads, and what it never does

**It reads only what the dashboard shows, about you:**

- your character: health, water, stamina, energy, heat, cold, spice, armor, radiation protection, position, map and heading; on the main menu, your character's name, level, world, sietch and faction;
- the vehicle you're in: hull, temperature, fuel, modules and speed;
- your world: time of day, Coriolis storm timing, the server and region;
- your bases: power, water, shields, claim size, power-down timer and generators;
- a base blueprint, only when you click **Export base**, saved where you choose.

**It never:**

- shows or stores anything about **other players**;
- **changes the game**, sends keyboard or mouse input, or automates anything;
- reads your **accounts**, passwords, chat or Steam login;
- **uploads** anything: there's no telemetry or analytics.

**What stays on your PC:** your settings and, unless you turn it off in **About › Characters**, a memory of your characters (level, world, last place, bases and recent sessions) in `%LOCALAPPDATA%\DunePulse`. Setup logs are in `%ProgramData%\DunePulse\Setup`.

**What it downloads:** update checks and the signed list of approved Dune Pulse builds from `cdn.ferretech.org`, and, only if you agree while installing, Microsoft's .NET runtime from Microsoft. None of these carries your account, character, server or PC details.

**How it's protected:** a small Microsoft-signed driver copies values out of the game for Dune Pulse's background service, and serves nothing else. It accepts only Dune Pulse's own signed programs, listed by exact file fingerprint in a list signed by FerreTech that expires every 30 days. The service talks only to the Windows user who installed Dune Pulse, reads only the Dune: Awakening process in your own session, and only for game versions it recognizes.

## Reporting a problem or an idea

[Open an issue](../../issues/new/choose) and pick the form that fits:

- **Bug report:** something doesn't work.
- **Game update:** a Dune: Awakening patch stopped or changed what Dune Pulse shows. After a patch Dune Pulse tries to find its way around the new version by itself; when it can't, it says the build is unsupported and reads nothing. That's expected, but tell us.
- **Feature request:** something you'd like it to do.

Please leave out personal details: character and account names, server names you'd rather keep private, IP addresses and personal file paths.

**Security problems:** don't open an issue. Report them privately, as described in [SECURITY.md](SECURITY.md).

## Things to know

- Dune Pulse is an **unofficial community tool**. It isn't affiliated with or endorsed by Funcom. It never changes the game, but its standing with the game's anti-cheat is still being confirmed, so use it at your own discretion.
- It's in **beta**: expect rough edges, and some values may be missing for a while after a game patch.

## Credits and names

Built by FerreTech Interactive LLC in partnership with [Red-Blink](https://github.com/Red-Blink), originator of the [DuneDocker.app](https://dunedocker.app) community project. The Dune Docker name and logo are used with permission.

"Dune Pulse" and "FerreTech Interactive" are names of FerreTech Interactive LLC. *Dune: Awakening* is a trademark of its respective owner. Licensing and third-party notices are in [LICENSE.md](LICENSE.md).
