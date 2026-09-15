# homebrew-turnrelay

Homebrew tap for [turnrelay](https://github.com/romanrublev/turnrelay), a system
VPN that tunnels UDP through WebRTC TURN relays.

## Install

```sh
brew tap romanrublev/turnrelay
brew install --HEAD romanrublev/turnrelay/turnrelay
sudo turnrelay install
```

Then create your profile and connect:

```sh
# ~/Library/Application Support/turnrelay/profile.json (macOS)
# ~/.config/turnrelay/profile.json (Linux), chmod 600
turnrelay up
turnrelay status
turnrelay down
```

Homebrew-installed binaries are not quarantined, so the unsigned binary runs
without a Gatekeeper prompt. The privileged daemon is set up by
`sudo turnrelay install` (launchd on macOS, systemd on Linux), not by
`brew services`.
