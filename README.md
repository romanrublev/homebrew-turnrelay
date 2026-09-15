# homebrew-turnrelay

Homebrew tap for [turnrelay](https://github.com/romanrublev/turnrelay), a system
VPN that tunnels UDP through WebRTC TURN relays.

## Install (macOS Apple Silicon)

```sh
brew tap romanrublev/turnrelay
brew install romanrublev/turnrelay/turnrelay
sudo turnrelay install
```

This pours a prebuilt binary (no build, no sandbox flag).

### Other platforms / latest main (build from source)

```sh
HOMEBREW_NO_SANDBOX=1 brew install --HEAD romanrublev/turnrelay/turnrelay
```

`HOMEBREW_NO_SANDBOX=1` is required because the source build fetches Go modules,
which Homebrew's build sandbox blocks.

## Use

Create your profile (chmod 600) and connect:

```sh
# ~/Library/Application Support/turnrelay/profile.json (macOS)
# ~/.config/turnrelay/profile.json (Linux)
turnrelay up
turnrelay status
turnrelay down
```

Homebrew-installed binaries are not quarantined, so the unsigned binary runs
without a Gatekeeper prompt. The privileged daemon is set up by
`sudo turnrelay install` (launchd on macOS, systemd on Linux), not by
`brew services`.
